# Vim/Neovim Guide

This guide is a really helpful and complete kickstart in how to use Vim/Neovim

![Neovim Logo](https://i.imgur.com/P8AtcKX.jpeg)


## What is Vim/Neovim? A brief history about ancient code editors.

Back in the days, computers weren't that advanced as nowdays. Programmers didn't have IDE's to work with their codes and the auto-complete functionality was a dream away.

In order to work with code, they had to use Vi, an ancient code editor that makes use of the terminal. Here's an image of Vi:

![Vi in a really old computer.](https://i.imgur.com/C8jYSgX.png)

Pretty old right?

So one day someone thought it was a good idea to create a new improved version of Vi, which you can presume is the Vim code editor as we know.

But you might be thinking: is Neovim an improved version of Vim? Yes, you nailed it.

As vim is hashly limited by it's configurations, someone just created a new version of Vim that accepts scripting for custom settings and so on. Neovim accepts Lua as scrippting programming language, LSP (Language Server Protocol) providing code completion and code hinting, and even more.

## Before Trying to Use Vim/Neovim

You might be thinking: Why not just to use a working IDE's such as Visual Studio Code?

Vim makes you really fast on writing code. Once you try, you don't wanna go back. And you can develop anything you want from it, because at the end of the day every code is just text.

If you use Visual Studio Code and want to use Vim, there's actually an extension in Visual Studio Code that simulates Vim on it. Go try it.

## For Windows Users: Configuring WSL

In order to make Linux terminals work on Windows, you should take knowledge of WSL. Quoting Microsoft FAQ's:

> The Windows Subsystem for Linux (WSL) lets developers install a Linux distribution (such as Ubuntu, OpenSUSE, Kali, Debian, Arch Linux, etc) and use Linux applications, utilities, and Bash command-line tools directly on Windows, unmodified, without the overhead of a traditional virtual machine or dualboot setup.

You should also enable virtualization on your machine.

### Running Debian Distro on WSL

To install a Debian-based WSL on your machine, you can run PowerShell as Administrator and run the following command:

``wsl --install``

This command take a while. I meant, really a while. Once is installed, reboot your machine.

Once the computer is powered up, open PowerShell again and run `ubuntu` on the command line. It might be take a while to install. After that, a username and password will be prompted:

![Ubuntu, username and password](https://i.imgur.com/vWqWDrN.gif)

Now, run these commands:

``sudo apt-get update``

``sudo apt-get install build-essential``

``wget https://github.com/neovim/neovim/releases/download/stable/nvim-linux64.deb``

Run `ls` and check if there's a file called `nvim-linux64.deb` on the directory. To install the package, run `sudo apt install ./nvim-linux64.deb`.

Once is installed, run `nvim`. You might be in the 0.8.0^ version of neovim.

To quit Vim/Neovim, just simply hit `Shift` + `z` + `q` to exit the vim without saving anything. If you want to save and quit, hit `Shift` + `z` + `z`. 

If you hit these keys with Caps Lock activated, it will not work. The reason is because Vim differ uppercase latters from lowercase letters. As an example, the command above `Shift` + `z` + `q` is no more than `ZQ`. So if your caps is on, you can just hit `z` + `q`.

### Running Arch Distro on WSL

To install a Arch-based WSL on your machine, access the [Arch WSL](https://markdownlivepreview.com/). 

Find the Releases page and download `Arch.zip`. Now, extract the zip file and put all content in a new folder. Put that folder somewhere in your disk (e.g I've put mine in C:\ ). Now with PowerShell or CMD, go to the location you have put the folder and just simply run `arch` on the command line.

Arch automatically gives you root permissions. So, you need to set up a new user.

In order to set up a new user, you can simply run:

`echo "%wheel ALL=(ALL) ALL" > /etc/sudoers.d/wheel`

`useradd -m -G wheel -s /bin/bash {username}`

Note that `{username}` represents the username you want to.

`passwd {username}`

Now if you run `su {username}` you should login as the user you just created.

![Ubuntu, username and password](https://i.imgur.com/SuwkQxP.gif)

Exit the Arch WSL by running `exit` and go back to PowerShell or CMD. Go back to the Arch folder directory and run:

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

Install [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=en-us&gl=en) from Microsoft Store, and you have a really great terminal to work with.

Click the drop arrow at the tab and click Arch, Ubuntu (or whatever distro you have installed), and you have it!

![Yes, you can put your waifu as background now.](https://i.imgur.com/XjeqltN.gif)

You can customize your Windows Terminal appearence by going into Settings, clicking on the distro profile you use and go to Appearance.

If you want some custom themes, you can go to [Windows Terminal Themes](https://windowsterminalthemes.dev/) website and click "Get Theme" on any theme you like. Go back to Windows Terminal settings and click "Open JSON file".

Scroll to the end of the file and paste the theme you picked right after the comma, like this:

![This is a alt text.](https://i.imgur.com/xQX1zeZ.gif)

Go to Color scheme and the theme will be there. If it's not, you probably had got something wrong.

![Changing theme](https://i.imgur.com/27OIwEy.gif)

## Installing LunarVim

In Neovim, you can install any plugins you want and make your IDE, but is a litte complicate to get things working properly. Instead, you can install a complete IDE layer for Neovim, like LunarVim.

[LunarVim](https://www.lunarvim.org/) is not an actual IDE. It's just a bunch of plugins packed and pre-configured that makes your life easier.

To install LunarVim on Linux, just run:

```
LV_BRANCH='release-1.2/neovim-0.8' bash <(curl -s https://raw.githubusercontent.com/lunarvim/lunarvim/fc6873809934917b470bff1b072171879899a36b/utils/installer/install.sh)
```

Once installed, you may noticed the following message:

```
Thank you for installing LunarVim!!
You can start it by running: /home/{username}/.local/bin/lvim
Do not forget to use a font with glyphs (icons) support [https://github.com/ryanoasis/nerd-fonts]
```

You need to export the path on the `.bashrc` file. In Ubuntu distro, run `sudo nano .bashrc`. 

In Arch distro, run `sudo nano /etc/bash.bashrc`.

Once you got in there, export the path by adding this line to the file:

`export PATH=$PATH:/home/{user}/.local/bin:$PATH`

Note that you should change `{user}` to the current user you are using.

Now, run `lvim` in the command line and wait all the things to install.

![LunarVim](https://i.imgur.com/1oq4sTP.gif)
