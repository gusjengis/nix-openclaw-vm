This is a script that sets up a functioning OpenClaw instance in a VM. Intended to work with a minimal NixOS ISO.
This is a work in progress. If you're coming from my resume, the project that I described is what this will become. It's all stuff I know how to do already, it's just a matter of applying existing skills.

I'm documenting the stops that work for me as I take them.


Instructions:

1. Install NixOS in a VM with the [Minimal ISO](https://channels.nixos.org/nixos-25.11/latest-nixos-minimal-x86_64-linux.iso)
    - I gave mine 8GB (8192 MB) of RAM, 8 cores, and 50GB of disk, but I just made those numbers up.

2. After booting:
    ```
    curl -fsSL https://raw.githubusercontent.com/gusjengis/nix-openclaw-vm/main/install.sh | bash
    ```
    - The Script will install the OS into the VMs disk automatically
    - Then you will be prompted to select the modules/capabilities you want to enable
    - If you have enabled Tailscale, you will be asked for you auth key, so that this machine can be added to the Tailscale network before the bot is up and running. The key will not be stored on the system.
    - When everything is configured and installed, the machine will reboot

3. After installation, during first boot, follow the prompts and walk through the OpenClaw setup

At this point, you should have some chat interface configured, and the bot is running and free to configure it's home environment however you direct it to. There should be a running WebUI that you can connect to that will allow you to view the history of it's configuration and activity, rollback to previous versions, manage it's execution (stop it, restart it, etc). Some of this WebUI will basically be a GUI for git and nix commands, the rest will be process management.

There is also the option of remotely configuring the VM/bot using SSH and/or Waypipe. Waypipe is super cool btw, it's like remote desktop, but for single programs, and they appear on your system like native windows. [Check it out](https://gitlab.freedesktop.org/mstoeckl/waypipe/).

This is a mostly just a plan at the moment, I'm currently in the process of working on the install script. It's similar to one I use for quickly setting up my personal machines, but the layout of this system is a little different, so I need to adapt it. 

I want to try OpenClaw for a bunch of personal applications. Along the way, I'm being careful to make sure that the basic setup is fully reproducible, so that myself and others can pretty automatically spawn new systems running OpenClaw, and this setup process never has to be repeated. 

While working on this, I've discovered that it's pretty easy to make custom NixOS installer ISOs. This means that I can create one that comes pre-installed setup to automatically run this script. If I define a bunch of reasonable default settings, this will enable someone to create a VM, boot it with this ISO, walk away for a few minutes, and come back to a freshly installed system prompting them to go through the OpenClaw initialization. Pretty slick. I'll see what I can do about automating the OpenClaw init when I get to it, but I'm pretty sure it's unavoidable.
