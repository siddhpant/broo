# Broo
 
- Connect your phone as microphone wirelessly.
- Get clear voice and low latency with minimal CPU overhead.
- Just run one command (`$ broo`) to quickly set-up the mic and start talking with peers.
- Supports both modern PipeWire and legacy PulseAudio.
- For PulseAudio use case, restores backed-up ALSA settings stored in `~/.config/asound.state`, if it exists.

## Why call it Broo?

- Sanskrit धातु (lexical word stem) &nbsp;" **ब्रू** "&nbsp; (brU) which means "to speak".
- You go like "BROOOOOOOOO that was NICE" while vibing with your homies.

## Requirements

- A GNU/Linux distro with either PipeWire or PulseAudio.
- A smartphone (or anything with a mic which can connect to a local Mumble server).
    - For Android → Mumla app* ([F-Droid](https://f-droid.org/packages/se.lublin.mumla/)) [[Source](https://gitlab.com/quite/mumla)]
    - For iOS → Official Mumble app* ([App Store](https://apps.apple.com/us/app/mumble/id443472808)) [[Source](https://github.com/mumble-voip/mumble-iphoneos)]

### For distros with the `apt` package manager.

- The setup script will do the heavy lifting for you. Please proceed to the installation.

### Otherwise

Install the following:

- `mumble`
    - Typically includes `mumble-server` or `murmur`.
    - If not, then install them too.
- `avahi` or `avahi-daemon`
- `iproute2`

If you want, you may build Mumble and its server directly from the [source](https://github.com/mumble-voip/mumble) to get improved PipeWire support, performance, and bug fixes. Compilation doesn't take much time and completes under a few minutes. Though, you may want to build a package for better uninstallation later instead of directly going the `sudo make install` route.

## Installation

```
$ git clone https://github.com/siddhpant/broo.git
$ cd broo
$ chmod +x broo setup_broo
$ ./setup_broo
```

Then follow the on-screen instructions.

## Run

```
$ broo
Do you want to start Broo, or close it? (s/c): 
```

- Press `s` to start Broo, or `c` to stop it.
- Use the mic by choosing `Monitor of Broo` as your input source / mic in applications.
- The script will reside in `~/.local/bin`, so you can run Broo from anywhere.
- You can use `-h` or `--help` for help.

## Audiophile?

Then you can eliminate the WiFi latency by connecting your phone to your computer with a wire.

Use `USB tethering` to share your smartphone's active internet connection with your computer. When Broo creates a local server, due to direct connection with the phone the WiFi latency will be bypassed, and you can observe Mumla showing 0ms latency before connecting.

This will reduce the total audio latency by a significant percentage. For example, you might reduce the latency by 15ms, but the gain can be more or less since it depends on your connection.

The network latency to the web servers of services such as Teams, Google Meet, Discord, etc. is usually higher, so in the grand scheme of things, this optimisation might not matter for the average user.

Further, this may come in handy when your WiFi adapter / card / driver is borked.

## Miscellaneous

If you see that your PC's user isn't in the channel when you join from your mobile, then restart Broo and press `p` on the starting prompt of Broo. After following the on-screen steps, run Broo normally.

If the problem still persists, it would be nice to go through the setup again.

You can also force close broo with `q` and force start with `f`.

---

## Credits

Inspired by the implementation of https://github.com/pzmarzly/mic_over_mumble/.

I have tried to hopefully iron out some problems with the original implementation by making the script from scratch to streamline the code, and added absolutely necessary features such as supporting PipeWire, adding prompt and ability to close the terminal, ALSA setting restore, etc.

## Footnotes

\* Due to devs being busy, the iOS app is officially unmaintained, while Android app is sorta in the same boat but short of being abandoned.

But the apps seem to work for many people thanks to Mubmle's backward compatibility. **Any breakages maybe due to system changes rather than problems in Broo.**

If you are someone capable of creating apps, a new Mumble client for mobile would be a nice project. Probably could use Flutter for cross-platform (idk much), with something building on the lines of using [libmumble](https://github.com/mumble-voip/libmumble) + [dart:ffi](https://dart.dev/guides/libraries/c-interop), or [dumble](https://github.com/EPNW/dumble).

---

## License

Copyright (C) 2021  Siddh Raman Pant

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published
by the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.

The online repository can be found at <https://github.com/siddhpant/broo>.
