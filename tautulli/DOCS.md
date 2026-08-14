# Home Assistant Add-on: Tautulli

Tautulli monitors your Plex Media Server and provides watch history, user and
library statistics, graphs, stream details, and notifications.

## Installation

This add-on is currently distributed as a local Home Assistant add-on:

1. Copy this repository's `tautulli` directory to `/addons/tautulli` on the
   Home Assistant host.
1. In Home Assistant, go to **Settings** > **Add-ons** > **Add-on Store**.
1. Open the menu and select **Check for updates** so Home Assistant reloads the
   local add-ons.
1. Select **Tautulli** and choose **Install**.
1. Start the add-on and review its log for errors.
1. Select **Open Web UI** and follow Tautulli's wizard to connect to Plex.

The initial image build and first start can take a few minutes. The wizard does
not request a Tautulli web username or password because access is protected by
Home Assistant Ingress or the add-on's direct-access proxy.

Updating or rebuilding the add-on preserves the Tautulli configuration and
database in the add-on data directory. Create a Home Assistant backup before a
significant upgrade.

## Ingress and sidebar access

The recommended access method is **Open Web UI**. This uses Home Assistant
Ingress, so users must already be authenticated by Home Assistant and no port
exposure is required.

To keep Tautulli in the Home Assistant navigation, enable **Show in sidebar**
on the add-on's **Info** tab.

The add-on manages Tautulli's internal HTTP root automatically. Do not change
the HTTP root or authentication settings inside Tautulli; the values are reset
at startup to keep Ingress routing and the authentication boundary consistent.

## Configuration

### Option: `disable_authentication`

The default is `true`. In this mode, only Home Assistant Ingress is allowed and
direct requests to port `8181` are blocked.

Set this option to `false` only when direct access is required. You must also
provide `authentication_username` and `authentication_password`. After the
add-on restarts, NGINX protects direct requests with HTTP Basic Authentication,
while Ingress continues to use Home Assistant authentication.

Tautulli's own web authentication remains disabled in both modes. This avoids a
second login through Ingress and prevents Tautulli settings from accidentally
creating an unauthenticated direct endpoint.

If direct authentication is enabled but either credential is absent, the add-on
logs a warning and remains in its safe, Ingress-only mode.

### Option: `authentication_username`

The username required by NGINX for direct access when
`disable_authentication: false`. It may contain letters, numbers, underscores,
periods, `@`, and hyphens.

### Option: `authentication_password`

The password required by NGINX for direct access when
`disable_authentication: false`. Home Assistant masks it in the add-on options.
Treat add-on configuration and backups as sensitive because administrators can
access these settings.

Change direct-access credentials in the add-on options, then restart the
add-on. Do not configure them in Tautulli.

### Option: `log_level`

The log level defaults to `info`. Supported values are:

- `trace`: All available diagnostic detail.
- `debug`: Detailed troubleshooting information.
- `info`: Normal operational messages.
- `notice`: Significant normal events.
- `warning`: Unexpected conditions that do not stop the add-on.
- `error`: Runtime errors.
- `fatal`: Errors that make the add-on unusable.

Each level also includes messages at higher severities. Use `debug` or `trace`
temporarily when troubleshooting because verbose logs may contain more private
information.

### Examples

Recommended Ingress-only configuration:

```yaml
disable_authentication: true
log_level: info
```

Authenticated direct access:

```yaml
disable_authentication: false
authentication_username: tautulli
authentication_password: change-this-password
log_level: info
```

Restart the add-on after changing any option.

## Data, backups, and privacy

Tautulli's database and configuration are stored in the add-on data directory.
Its application backups are stored under `/backup/tautulli`. Home Assistant
backups can therefore contain Plex tokens, viewing history, and direct-access
credentials.

Review the repository's [privacy notice][privacy] and redact credentials,
tokens, hostnames, IP addresses, and personal media information from logs before
sharing them.

## Troubleshooting

- If the sidebar entry is missing, confirm the add-on is running and **Show in
  sidebar** is enabled on its **Info** tab.
- If **Open Web UI** returns an error, inspect the add-on log for Tautulli or
  NGINX startup failures and restart the add-on once.
- If direct access is blocked, confirm `disable_authentication` is `false`, both
  credentials are present, and the add-on was restarted.
- A browser Basic Authentication prompt is expected only for direct access on
  port `8181`; it should not appear through Ingress.
- If Tautulli's wizard asks for its own web credentials, rebuild from the latest
  add-on files and inspect the startup log for a wizard-template error.

## Support

For installation, startup, Ingress, authentication, or packaging problems, use
this repository's [support guide][support] or open a [bug report][issues].

For behavior that also occurs in a standard Tautulli installation, consult the
upstream [Tautulli support guide][upstream-support]. Suspected vulnerabilities
must be reported privately according to the [security policy][security].

## Releases and license

Release highlights are recorded in [What's New][whats-new]. Versions follow
[Semantic Versioning][semver].

This add-on is distributed under the [MIT License][license]. The full copyright
history, including the 2026 fork maintenance attribution, is kept in that file.

[issues]: https://github.com/manix84/addon-tautulli/issues
[license]: ../LICENSE.md
[privacy]: ../PRIVACY.md
[security]: ../.github/SECURITY.md
[semver]: https://semver.org/spec/v2.0.0.html
[support]: ../.github/SUPPORT.md
[upstream-support]: https://github.com/Tautulli/Tautulli/wiki/Asking-for-Support
[whats-new]: ../WHATSNEW.md
