# Broo

 [![License: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
 
- Connect your phone as microphone wirelessly.
- Get clear voice and low latency (around 30ms on average).
- Just run one command (`$ broo`) to quickly set-up the mic and start talking with peers.
- Supports both modern PipeWire and legacy PulseAudio.
- For PulseAudio use case, restores backed-up ALSA settings stored in `~/.config/asound.state`, if it exists.


## Reason for such a name

- Sanskrit धातु (lexical word stem) &nbsp;" **ब्रू** "&nbsp; (brU) which means "to speak".
- You go like "BROOOOOOOOO that was NICE" while vibing with your homies.

## Requirements

- A GNU/Linux distro with either PipeWire or PulseAudio.
- A smartphone (or anything with a mic which can connect to a local Mumble server).
    - For Android → Mumla app ([F-Droid](https://f-droid.org/packages/se.lublin.mumla/)) [[Source](https://gitlab.com/quite/mumla)]
    - For iOS → Official Mumble app ([App Store](https://apps.apple.com/us/app/mumble/id443472808)) [[Source, unmaintained](https://github.com/mumble-voip/mumble-iphoneos)]

### For distros with the `apt` package manager.

- The setup script will do the heavy lifting for you. Please proceed to the installation.

### Otherwise

Install the following:

- `mumble`
- `murmur` or `mumble-server`
- `avahi` or `avahi-daemon`

If you want, you may build Mumble and its server directly from the [source](https://github.com/mumble-voip/mumble) to get improved PipeWire support, performance, and bug fixes. Compilation doesn't take much take and completes under a few minutes. You may [want to build a package](https://github.com/mumble-voip/mumble/issues/5302#issuecomment-967989830) instead of directly going the `sudo make install` route.

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
- The script will reside in `/usr/local/bin`, so you can run Broo from anywhere.

## Credits

Inspired by the implementation of https://github.com/pzmarzly/mic_over_mumble/.

I have tried to hopefully iron out some problems with the original implementation by making the script from scratch to streamline the code, and added absolutely necessary features such as supporting PipeWire, adding prompt and ability to close the terminal, ALSA setting restore, etc.
