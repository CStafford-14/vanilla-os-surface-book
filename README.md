# VanillaOS for Surface Book 2

This repository contains a Vib recipe for creating a custom VanillaOS install medium suitable for the Surface Book 2.
This is my first time really using Vib, so this repository will likely change as I figure out what I should and should not do to build a system image.
I will be daily driving this image on my own Surface device, so I'll know if something screws up!

## Changes and additions

- Adds the Surface Linux kernel repository (More information [here](https://github.com/linux-surface/linux-surface).) and the kernel and headers
- `iptsd`
- Secure boot via `linux-surface-secureboot-mok`
- Clipboard detachment via `surface-dtx-daemon`
- GNOME Tweaks
- Wine

### Planned additions

- [Howdy](https://github.com/boltgolt/howdy)
- Custom plymouth theme for Surface, probably BGRT or something of the like

## Customize this image

- First, click on the "Fork" button in the top right corner, then follow the options to create a repository based on this one. This would create a new repository with the same files and directories as this repository.
- Go to Settings → Actions → General and ensure "Allow all actions and reusable workflows" are enabled.
- Now, clone the repository to your local machine and let's start customizing your image. You can also use the GitHub online editor if you prefer.
- Open the `vib-build.yml` workflow file and replace the custom image name with an image name of your choosing in line 11.
- Open the `recipe.yml` file and replace the image name and ID with your image name and ID in lines 2 and 3.
- Now, perform your additions and modifications to the recipe as per your requirements.
- If you just want to install .deb files, you can just put them in `includes.container/deb-pkgs`
- Optionally, add your modules to the `modules` directory and add them to the package-modules `includes` in `recipe.yml`.
- You can check the Actions tab in GitHub to see the build progress of your image.

> [!NOTE]
> It is suggested to add a `vib-image` tag to your repository for your image to be easily discoverable.

## Use your custom image

If your image is successfully built, you can then point ABRoot to your custom image to use it.

- Edit `/etc/abroot/abroot.json` with `host-shell pkexec nano /etc/abroot/abroot.json`.
- Change the "name" entry from something like `vanilla-os/desktop` to `your-github-name/your-image-name` (for example `taukakao/custom`).
- Run `abroot upgrade` to switch to your custom image.

Instructions for direct ISO coming soon™

To learn more about Vib and how to use it, check out the following resources:
- [Vib Repository](https://github.com/Vanilla-OS/Vib)
- [Custom Vib Image Template](https://github.com/Vanilla-OS/custom-image)
