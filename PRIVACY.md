# Privacy

## Overview

This add-on runs Tautulli locally within Home Assistant. The add-on maintainer
does not operate a service that receives your Tautulli data.

Tautulli processes information from your Plex Media Server, which may include
server details, Plex account tokens, library metadata, users, devices, IP
addresses, and viewing activity. This information is stored in the add-on data
directory and is governed by your Tautulli and Plex configuration.

## Authentication data

When using Home Assistant Ingress, Home Assistant authenticates access to the
add-on. If direct access on port `8181` is enabled, its username and password are
stored in the Home Assistant add-on options. The password is masked in the user
interface, but administrators and backups with access to add-on configuration
must still be treated as sensitive.

The direct-access proxy derives an ephemeral password hash when the add-on
starts. Tautulli cannot disable or bypass that proxy authentication.

## Network connections

The add-on connects to the Plex Media Server and Plex services required by
Tautulli. Features configured within Tautulli, such as notifications, metadata,
newsletters, or third-party integrations, may contact additional services under
their respective privacy policies.

The add-on disables Tautulli system analytics and its built-in update checks.
Home Assistant and the container platform may perform their own update checks
according to their configuration.

## Storage, logs, and backups

The Tautulli database, configuration, and backups are stored in locations made
available to the add-on. Home Assistant backups may therefore contain viewing
history, tokens, credentials, and other personal information.

Add-on and Tautulli logs can contain usernames, media details, network
addresses, paths, or other identifying data. Review and redact logs before
sharing them.

Removing the add-on data and associated backups removes the copies controlled
by this add-on. It does not remove information retained by Plex, notification
providers, or other external services.
