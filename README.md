# Neovim Setup Guide

This guide is a really helpful and complete kickstart in how to use Vim/Neovim

![Neovim Logo](https://i.imgur.com/P8AtcKX.jpeg)

## What is Vim/Neovim? A brief history about ancient code editors.

Back in the days, computers weren't that advanced as nowdays. Programmers didn't have IDE's to work with their codes and the auto-complete functionality was a dream away.

In order to work with code, they had to use Vi, which is a ancient code editor that makes use of the terminal. Here's an image of Vi:

![Vi in a really old computer.](https://i.imgur.com/C8jYSgX.png)

Pretty clunky right?

So one day, someone thought it was a good idea to create a new improved version of Vi, which you can presume is the Vim code editor as we know.

But you might be thinking: is Neovim a new improved version of Vim too? Yes, you nailed it.

As vim is hashly limited by it's configurations, someone just thought to make a new version that accepts scripting for custom configurations and so on. Neovim accepts Lua as scrippting programming language, LSP (Language Server Protocol) providing code completion and code hinting.

## Before Trying to Use Vim/Neovim

You might be thinking, `Why not just to use a working IDE's such as Visual Studio Code?`

// Change this line below

If you use Visual Studio Code and want to use Vim/Neovim, don't do that. Instead, use the Vim extension from Visual Studio Code and get used to it. 

## For Windows Users: Configuring WSL

In order to make Linux terminals work on Windows, you should take knowledge of WSL (Windows Subsystem for Linux). Quoting Microsoft FAQ's:

> O WSL (Subsistema do Windows para Linux) permite que os desenvolvedores instalem uma distribuição do Linux (como Ubuntu, OpenSUSE, Kali, Debian, Arch Linux etc) e usem aplicativos, utilitários e ferramentas de linha de comando bash do Linux diretamente no Windows, sem modificação, sem a sobrecarga de uma máquina virtual tradicional ou configuração dualboot.

You should also enable virtualization on your machine.

### Running Debian Distro on WSL

To install a Debian-based WSL on your machine, you can run PowerShell as Administrator and run the following command:

``wsl --install``

This command take a while. I meant, really a while. Once is installed, reboot your machine.

Once the computer is powered up, open PowerShell again and run `ubuntu` on the command line. This might be take a while to install. After that, a username and password will be prompted. Now, run these commands:

``sudo apt-get update``

``sudo apt-get install build-essential``

``wget https://github.com/neovim/neovim/releases/download/stable/nvim-linux64.deb``

Run `ls` and check if there's a file called `nvim-linux64.deb` and run `sudo apt install ./nvim-linux64.deb`.

Once is installed, run `nvim`. You might be in the 0.8.0^ version of neovim.

To quit Vim/Neovim, just simply hit `Shift` + `z` + `q` to exit the vim without saving anything. If you want to save and quit, hit `Shift` + `z` + `z`. 

If you hit these keys with Caps Lock activated, it will not work. The reason is because Vim differ uppercase latters from lowercase letters. As an example, the command above `Shift` + `z` + `q` is no more than `ZQ`. So if your caps is on, you can just hit `z` + `q`.

### Running Arch Distro on WSL

To install a Arch-based WSL on your machine, you can access this link:

[Arch WSL](https://markdownlivepreview.com/)

Find the Releases page and download `Arch.zip`. Now, extract the zip file and put all content in a new folder. Put that folder somewhere in your disk (e.g I've put mine in C:\ ). Now with PowerShell or CMD, go to the location you have put the folder and just simply run `arch` on the command line.

You may have an Arch on your WSL, but Arch automatically gives you root permissions. So, you need set up a new user.

In order to set up a new user, you can simply run:

`echo "%wheel ALL=(ALL) ALL" > /etc/sudoers.d/wheel`

`useradd -m -G wheel -s /bin/bash {username}`

Note that `{username}` represents the username you want to.

`passwd {username}`

Exit the Arch WSL by running `exit` and go back to PowerShell or CMD.

Go back to the Arch folder and run:

`Arch.exe config --default-user {username}`

Run `./arch` to go back to Arch terminal. You can check if the user is really yourself by running `whoami`.

Before installing Neovim we need to run some commands to initialize the use of the pacman. Run the following commands:

``sudo pacman-key --init``

``sudo pacman-key --populate``

``sudo pacman -Sy archlinux-keyring``

``sudo pacman -Su``

Install the build-essential pack:

``sudo pacman -S base-devel``

And finally, install Neovim:

``sudo pacman -Sy neovim``

Run `nvim` and you have it!

## Setting Up WSL on Windows Terminal

Using Vim/Neovim in Windows can be painful, because PowerShell and CMD don't provide that cool stuff as Linux terminals do. So if you can't beat them, join them!

Install Windows Terminal from Microsoft Store, and you have a really great terminal to work with.

Click the drop arrow at the tab and click Arch, Ubuntu (or whatever distro you have), and you have it!

You can customize your Windows Terminal appearence by going into Settings, clicking on the distro profile you use and go to Appearance.

If you want some custom themes, you can go to [Windows Terminal Themes](https://windowsterminalthemes.dev/) website and click "Get Theme" on any theme you like. Go back to Windows Terminal settings and click "Open JSON file".

Scroll to the end of the file and paste the theme you picked right after the comma, like this:

![This is a alt text.](https://i.imgur.com/xQX1zeZ.gif)

Go to Color scheme and the theme will be there. If it's not, probably have got something wrong.

## For Linux Users

You can follow the same tutorial for Windows as in there we install WSL which is basically Linux running on Windows.
