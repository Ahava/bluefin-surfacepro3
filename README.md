# Surface Pro 3 Bluefin based on Bluebuild &nbsp; [![bluefin-surfacepro3 build badge](https://github.com/Ahava/bluefin-surfacepro3/actions/workflows/build.yml/badge.svg)](https://github.com/Ahava/bluefin-surfacepro3/actions/workflows/build.yml)

Custom image for my Surface Pro 3. This is adjusted to my own needs and should not be taken as a generalized image. Based on [BlueBuild](https://blue-build.org/how-to/setup/) and [Bluefin HWE](https://github.com/ublue-os/bluefin/pkgs/container/bluefin-hwe).

## Installation

> **Warning**  
> [This is an experimental feature](https://www.fedoraproject.org/wiki/Changes/OstreeNativeContainerStable), try at your own discretion.

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/ahava/bluefin-surfacepro3:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/ahava/bluefin-surfacepro3:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

The `latest` tag will automatically point to the latest build. That build will still always use the Fedora version specified in `recipe.yml`, so you won't get accidentally updated to the next major version.

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/Ahava/bluefin-surfacepro3
```
