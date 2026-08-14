# What's New

## 0.3.0

- Updated Tautulli from `2.12.4` to `2.17.2`.
- Updated the Home Assistant Debian base image and Python runtime.
- Added Home Assistant Ingress and sidebar support.
- Made Ingress-only access the secure default.
- Added optional, independently authenticated direct access on port `8181`.
- Removed Tautulli authentication from the first-run wizard. Home Assistant
  protects Ingress, and NGINX protects optional direct access.
- Updated the add-on branding and documentation.
- Updated supported architectures to `amd64` and `aarch64`.

## Previous development releases

Versions `0.1.x` and `0.2.x` established the local add-on build, corrected
dependency and service startup failures, and iterated on Ingress routing and
authentication behavior leading to the `0.3.0` release.
