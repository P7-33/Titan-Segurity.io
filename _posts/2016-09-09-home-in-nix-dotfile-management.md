---
title: 'Home in Nix – dotfile management'
date: 2020-01-10T08:47:00+01:00
draft: false
---

*   August 01, 2019
*   1641 words
*   8 min

Anyone who spends a significant amount of time in the terminal or developing applications on more than one device has come across the challenge of portable user configuration management. The files used to configure tools like your shell, fish in my case, and your editor, neovim, are commonly referred to as 'dotfiles' and usually live within `~/.config/` Everyone tends to have their own unique solution to the problem; throughout most of 2018 and the start of 2019 I used the git bare repo approach described in this [Atlassian Doc](https://www.atlassian.com/git/tutorials/dotfiles). This solution served me well for a while, I could use a single repo per machine to store my dotfiles which enabled all the benefits of version control. The big issue was that I had to keep my Darwin and Arch/NixOS configuration separate because many configs needed to be tailored to the individual system. This made it particularly hard to keep common configs like my [Neovim config](https://github.com/HugoReeves/nix-home/tree/26b92f051c264a5391ae55531be7916d5051ce5f/program/editor/neovim/configs) in sync across Darwin and Linux.

It's safe to say that managing dotfiles is a tough problem and I wasn't happy with my git bare repo solution. After recently getting started with and learning to love [**Nix/NixOS**](https://nixos.org), installing NixOS on my desktop and Nix on my Darwin machine, I had a renewed interest in improving my dotfile management. NixOS allows you to define your system configuration, system users, desktop environments, bootloader, etc, using the declarative Nix language and enables atomic updates that can be reliably rolled back. Using this ability I was able to successfully create a portable system configuration, that could be deployed using shared elements such as the Desktop Environment, to multiple computers running NixOS. Now, I wanted to do the same for my dotfiles.

Defining my problem
-------------------

Ideally we want a single repository that enables sharing configuration and installed programs across any \*nix operating system that supports nix. We must cater to an installation characterized as such.

*   Multiple independent hardware devices. Refered to as **machines**.
*   Multiple "desktop" environments, Darwin (MacOS), bspwm, kde, etc. Lets call these **roles**.
*   Multiple users with specific package requirements. Referred to as **users**.

Packages and settings should be able installed/set depending on the selected, machine, role and user. After cloning the nixpkgs repository, a single file should be edited to compose the hardware, role and user.

Defining a solution
-------------------

Packages and settings should be installed/set depending on the selected, machine, role and user. Each of these three components, machine, role and user, can select the packages they require and override shared settings.

When searching for dotfile management using nix, the number one tool that appears is [Rycee's Home Manager](https://github.com/rycee/home-manager). This tool allows you to define settings for supported programs and services using nix expressions in a way comparable to NixOS configuration files. For example, you can install some user packages and configure your `.gitconfig` using a nix expression like this.

```
 { config, pkgs, ... }: { home.packages = with pkgs; \[ # Rust CLI Tools! I love rust. exa bat tokei xsv fd # Development neovim tmux jq git-crypt # Files zstd restic # Media youtube-dl imagemagick # Overview htop wtf lazygit neofetch # Jokes fortune figlet lolcat \]; programs.git = { enable = true; userEmail = "user@email.com"; userName = "user"; signing.key = "GPG-KEY-ID"; signing.signByDefault = true; }; } 
```

There's [good documentation](https://rycee.gitlab.io/home-manager/options.html) of all the options you can use within Home Manager. Now it's time to implement our solution.

Implementing a solution
-----------------------

Let's start with an entry point, `~/.config/nixpkgs/home.nix`, this is the file that home-manager uses by default as it's entry point.

```
 \# ~/.config/nixpkgs/home.nix { config, pkgs, ... }: { # Let Home Manager install and manage itself. programs.home-manager.enable = true; imports = \[ ./machine/apollo.nix ./role/darwin-laptop/index.nix ./user/x.nix \]; } 
```

I have actually symlinked `~/.config/nixpkgs` to `~/nix-home` just to make it easier to `cd` into the repo from a new shell.

### Machine Configuration

There isn't much required in terms of machine level configuration, so this file will be left more or less empty.

```
 \# ~/.config/nixpkgs/machine/apollo.nix { config, lib, pkgs, ... }: { nixpkgs.config.allowUnfree = true; } 
```

### Role Configuration

The role configuration contains config that is specific to the GUI/DE of the system.

I use [Alacritty](https://github.com/jwilm/alacritty) as my terminal, because it's a GUI app I want to place it's configuration in the role configuration. Here, I'm creating the role configuration `~/.config/nixpkgs/role/darwin-laptop/index.nix`.

Home Manager has built in support for Alacritty, this means you can define your `~/.config/alacritty/alacritty.yml` using a nix expression. A simple version of our role configuration, only setting Alacritty settings might look something like this.

```
 \# ~/.config/nixpkgs/role/darwin-laptop/index.nix { config, lib, pkgs, ... }: { programs.alacritty = { enable = true; settings = { font.size = 11; shell.program = "/usr/local/bin/fish"; }; }; } 
```

Here, the settings will overwrite the default alacritty settings.

If your setup can be defined using only one role, ie. you only operate one distinct desktop configuration, defining program settings in your role file might work. However, we want to make our dotfiles portable, ideally we should have a shared set of Alacritty settings that can be imported into each role for which we want to use Alacritty, each role file should also be able to override some shared settings where necessary.

To achieve this, we'll create a file `~/.config/nixpkgs/program/terminal/alacritty/default-settings.nix` and populate it our Alacritty configuration.

```
 \# ~/.config/nixpkgs/program/terminal/alacritty/default-settings.nix { env = { "TERM" = "xterm-256color"; }; background\_opacity = 0.95; window = { padding.x = 10; padding.y = 10; decorations = "buttonless"; }; font = { size = 12.0; use\_thin\_strokes = true; normal.family = "FuraCode Nerd Font"; bold.family = "FuraCode Nerd Font"; italic.family = "FuraCode Nerd Font"; }; cursor.style = "Beam"; shell = { program = "fish"; args = \[ "-C" "neofetch" \]; }; colors = { # Default colors primary = { background = "0x1b182c"; foreground = "0xcbe3e7"; }; # Normal colors normal = { black = "0x100e23"; red = "0xff8080"; green = "0x95ffa4"; yellow = "0xffe9aa"; blue = "0x91ddff"; magenta = "0xc991e1"; cyan = "0xaaffe4"; white = "0xcbe3e7"; }; # Bright colors bright = { black = "0x565575"; red = "0xff5458"; green = "0x62d196"; yellow = "0xffb378"; blue = "0x65b2ff"; magenta = "0x906cff"; cyan = "0x63f2f1"; white = "0xa6b3cc"; }; }; } 
```

Now, we can import the shared alacritty settings into our role file. We'll also overwrite some of the settings where neccesary. `lib.attrsets.recursiveUpdate` performs a deep merge of `arg1` with `arg2` overwriting values.

```
 \# ~/.config/nixpkgs/role/darwin-laptop/index.nix { config, lib, pkgs, ... }: { nixpkgs.config.allowUnfree = true; programs.alacritty = { enable = true; settings = lib.attrsets.recursiveUpdate (import ../../program/terminal/alacritty/default-settings.nix) { shell.program = "/usr/local/bin/fish"; }; }; home.file.".hammerspoon".source = ../../de/darwin-only/hammerspoon; } 
```

You may have noticed this last statement in the file `home.file.".hammerspoon".source = ../../de/darwin-only/hammerspoon;` This statement sources (copies file/s) from the local directory path `../../de/darwin-only/hammerspoon` into the home directory path `~/.hammerspoon` This is the primary method of sharing config files that cannot be configured using home manager. Hammerspoon is a utility app that I use on Darwin that allows binding custom keyboard shortcuts to lua scripts.

### User Configuration

User configuration stores common elements for your userspace that are platform independent.

I store my git configuration, and cli tools in the user configuration. The two imports, `neovim/default.nix` and `tmux/default.nix` are just nix expressions that source my `~/.config/neovim/` and `~/.config/tmux/tmux.conf` files. The `.vimrc` files for neovim are stored under `~/.config/nixpkgs/program/editor/neovim/config-files/*`.

Whenever I want to edit my neovim configuration I have to edit a file like `~/.config/nixpkgs/program/editor/neovim/config-files/keybinds.vimrc` and then run `home-manager switch` to have the files sourced into the `~/.config/neovim` folder. This may sound like a pain, having to run a command to deploy your changes each time you make them, but for me the advantages of having a single repo for cross os/de config management outweigh this slight pain point.

```
 \# ~/.config/nixpkgs/user/x.nix { config, pkgs, ... }: { imports = \[ ../program/editor/neovim/default.nix ../program/terminal/tmux/default.nix \]; home.packages = with pkgs; \[ # Rust CLI Tools! I love rust. exa bat tokei xsv fd # Development neovim tmux jq git-crypt dnsutils whois # Files zstd restic brig ipfs # Media youtube-dl imagemagick # Overview htop wtf lazygit neofetch # Jokes fortune figlet lolcat \]; programs.git = { enable = true; userEmail = "hugolreeves@gmail.com"; userName = "Hugo Reeves"; signing.key = "738A0BE6D8D8AE7D"; signing.signByDefault = true; }; } 
```

### Setting up a new system

Now, my dotfiles have been properly split up and modularized so that I can compose a deployment of dotfiles and packages on any unix distribution with the ability to override shared configuration depending on the platform.

On a new system with nix installed, say, my NixOS machine, I can simply clone my nix-home repository into `~/.config/nixpkgs` and create a new `home.nix` file. Within this file I can import the `user/x.nix` config I use on Darwin and create a new role, `role/bspwm-workstation/index.nix`, and machine, `machine/boron.nix`, config. Within the workstation file, I can import the shared Alacritty configuration and overwrite some of the settings where necessary.

```
 \# ~/.config/nixpkgs/role/bspwm-workstation/index.nix { config, lib, pkgs, attrsets, ... }: { home.packages = with pkgs; \[ dunst compton \]; services = { polybar = { enable = true; config = ../../de/bars/polybar/boron-config; script = "polybar top &"; }; }; programs.alacritty = { enable = true; settings = lib.attrsets.recursiveUpdate (import ../../program/terminal/alacritty/default-settings.nix) { font.size = 11; font.user\_thin\_strokes = false; window = { decorations = "full"; }; }; }; xdg.configFile = { "dunst/dunstrc".source = ../../de/notifications/dunst/dunstrc; "compton/compton.conf".source = ../../de/compositors/compton/boron-compton.conf; }; } 
```

Summary
-------

I think I'm finally happy. Nix and home-manager make it possible to store all of my dotfiles in a single repo and on a single branch. Separating my dependency path into the machine, role, user, system allows host specific adjustments to the a configuration. Now, if I update my neovim config on one system, and check the changes into github, on another system I can just run `cd ~/.config/nixpkgs; git pull; home-manager switch`

I encourage you to checkout my **nix-home** repo if this system interests you.

  
  
from Hacker News https://ift.tt/2QDkrUY