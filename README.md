# homebrew-turnrelay

Homebrew tap for [turnrelay](https://github.com/romanrublev/turnrelay), a system
VPN that tunnels UDP through WebRTC TURN relays.

## Install

```sh
brew tap romanrublev/turnrelay
HOMEBREW_NO_SANDBOX=1 brew install --HEAD romanrublev/turnrelay/turnrelay
sudo turnrelay install
```

`HOMEBREW_NO_SANDBOX=1` is required: the formula builds from source, and the
build fetches Go modules (the sing-box dependency tree), which Homebrew's build
sandbox blocks. Vendoring those deps is ~1.7 GB, so it is not committed; the
proper long-term fix is a prebuilt bottle attached to a GitHub release.

Then create your profile (chmod 600) and connect:

```sh
# ~/Library/Application Support/turnrelay/profile.json (macOS)
# ~/.config/turnrelay/profile.json (Linux)
turnrelay up
turnrelay status
turnrelay down
```

Homebrew-installed binaries are not quarantined, so the unsigned binary runs
without a Gatekeeper prompt. The privileged daemon is set up by
`sudo turnrelay install` (launchd on macOS, systemd on Linux), not by
`brew services`.
