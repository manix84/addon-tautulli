# Home Assistant Add-on: Tautulli

[![GitHub Release][releases-shield]][releases]
[![CI][github-actions-shield]][github-actions]
[![License][license-shield]](LICENSE.md)

![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]

Monitor, understand, and get notified about activity on your Plex Media Server.

![Screenshot of Tautulli][screenshot]

## About

[Tautulli][tautulli] provides monitoring, analytics, watch history, graphs, and
notifications for Plex Media Server. This add-on packages Tautulli for Home
Assistant OS and provides access through Home Assistant Ingress and the
sidebar.

The add-on currently packages Tautulli `2.17.2` and supports `aarch64` and
`amd64` systems.

## Access and authentication

Home Assistant Ingress is the secure default. Leave
`disable_authentication: true` to use **Open Web UI** or **Show in sidebar**;
the direct port remains blocked.

If direct access on port `8181` is required, set
`disable_authentication: false` and provide both `authentication_username` and
`authentication_password`. NGINX requires those credentials for direct
requests, while Ingress continues to use Home Assistant authentication.
Tautulli's own web authentication stays disabled so it cannot weaken the proxy
boundary or add a second login prompt.

## Installation

This repository is currently installed as a local Home Assistant add-on:

1. Copy the `tautulli` directory into the Home Assistant `/addons` directory.
1. In Home Assistant, go to **Settings** > **Add-ons** > **Add-on Store**.
1. Open the menu and select **Check for updates** to reload local add-ons.
1. Select **Tautulli**, install it, and start it.
1. Select **Open Web UI** and connect Tautulli to Plex.
1. Optionally enable **Show in sidebar** on the add-on's **Info** tab.

Updating the add-on files does not replace Tautulli's database or configuration
stored in the add-on data directory. A Home Assistant backup is still
recommended before upgrading.

[:books: Read the full add-on documentation][docs]

## Support and contributing

Use this repository's [support guide][support] for help, or open an
[issue][issues] for an add-on problem. Problems that also occur in a standard
Tautulli installation should be reported to the [upstream project][upstream].

Contributions are welcome; review the [contribution guidelines][contributing]
before opening a pull request. Suspected vulnerabilities must be reported
privately according to the [security policy][security].

## Privacy and releases

See the [privacy notice][privacy] for details about local data, credentials,
logs, backups, and external connections. Release highlights are recorded in
[What's New][whats-new].

## Credits and license

The original add-on was created by [Joakim Sørensen][ludeeus] and later
maintained by [Franck Nijhof][frenck]. This fork is maintained by
[Rob Taylor][maintainer]. See the [contributors page][contributors] for the
complete history.

This project is available under the [MIT License](LICENSE.md).

[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[contributors]: https://github.com/manix84/addon-tautulli/graphs/contributors
[contributing]: .github/CONTRIBUTING.md
[docs]: tautulli/DOCS.md
[frenck]: https://github.com/frenck
[github-actions-shield]: https://github.com/manix84/addon-tautulli/actions/workflows/ci.yaml/badge.svg
[github-actions]: https://github.com/manix84/addon-tautulli/actions/workflows/ci.yaml
[issues]: https://github.com/manix84/addon-tautulli/issues
[license-shield]: https://img.shields.io/github/license/manix84/addon-tautulli.svg
[ludeeus]: https://github.com/ludeeus
[maintainer]: https://github.com/manix84
[privacy]: PRIVACY.md
[releases-shield]: https://img.shields.io/github/v/release/manix84/addon-tautulli
[releases]: https://github.com/manix84/addon-tautulli/releases
[screenshot]: images/screenshot.png
[security]: .github/SECURITY.md
[support]: .github/SUPPORT.md
[tautulli]: https://tautulli.com/
[upstream]: https://github.com/Tautulli/Tautulli
[whats-new]: WHATSNEW.md
