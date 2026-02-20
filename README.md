I'm using the bootstapping that I already have working for my personal NixOS setup as base for my OpenClaw VM project. If you're coming here from my resume, this is something that will be working soon enough. I've tested the pieces in isolation, it's just a matter of putting them together.

I'm documenting the stops that work for me as I take them.

This is a script that sets up a functioning OpenClaw instance in a VM. Intended to work with a fresh "No Desktop" NixOS install. 

Instructions:

1. Install NixOS in a VM with the [Minimal ISO](https://channels.nixos.org/nixos-25.11/latest-nixos-minimal-x86_64-linux.iso)
    - I gave mine 8GB (8192 MB) of RAM, 8 cores, and 50GB of disk, but I just made those numbers up.

2. After booting:
    ```
    curl -fsSL https://raw.githubusercontent.com/gusjengis/nix-install-script/main/install.sh | bash
    ```
    - Select the modules you want to enable in the prompts
