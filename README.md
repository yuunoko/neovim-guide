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

If you use Visual Studio Code and want to use Vim, there's actually [an extension](https://marketplace.visualstudio.com/items?itemName=vscodevim.vim) in Visual Studio Code that simulates Vim on it. Go try it.

## For Windows Users: Configuring WSL

In order to make Linux terminals work on Windows, you should take knowledge of WSL. Quoting Microsoft FAQ's:

> The Windows Subsystem for Linux (WSL) lets developers install a Linux distribution (such as Ubuntu, OpenSUSE, Kali, Debian, Arch Linux, etc) and use Linux applications, utilities, and Bash command-line tools directly on Windows, unmodified, without the overhead of a traditional virtual machine or dualboot setup.

You should also enable virtualization on your machine. Make sure WSL feature is enabled on your system by going into the "Turn Windows features on or off" settings. Go all the way down and check "Windows Subsystem for Linux", like this:

![](https://i.imgur.com/eLHvUNx.png)

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

To install a Arch-based WSL on your machine, access the [Arch WSL](https://github.com/yuk7/ArchWSL) github repo.

Find the Releases page and download `Arch.zip`. Now, extract the zip file and put all content in a new folder. Put that folder somewhere in your disk (e.g I've put mine in C:\ ). Now with PowerShell or CMD, go to the location you have put the folder and just simply run `arch` on the command line.

Arch automatically gives you root permissions. So, you need to set up a new user.

In order to set up a new user, you can simply run:

`echo "%wheel ALL=(ALL) ALL" > /etc/sudoers.d/wheel`

`useradd -m -G wheel -s /bin/bash {username}`

Note that `{username}` represents the username you want to.

`passwd {username}`

Now if you run `su {username}` you should login as the user you just created.

![Ubuntu, username and password](https://i.imgur.com/SuwkQxP.gif)

Exit the Arch WSL by running `exit` and go back to PowerShell (or CMD if PowerShell just throw you erros). Go back to the Arch folder directory and run:

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

Go to `Color scheme` and the theme will be there. If it's not, you probably had got something wrong.

![Changing theme](https://i.imgur.com/27OIwEy.gif)

## Installing Plugins

You can of course install plugins from scratch by your own.

[ThePrimeagen](https://youtu.be/w7i4amO_zaE)

## Installing an IDE on Neovim

With Neovim, you can install a complete IDE layer for Neovim, like LunarVim.

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

Note that you should change `{user}` to the current user you are using on your Arch installation.

Now, run `lvim` in the command line and wait all the things to install.

![LunarVim](https://i.imgur.com/1oq4sTP.gif)

If you want your LunarVim background transparent, just press `c` for configuration at the start screen of LunarVim (the dashboard) add `lvim.transparent_window = true` line on the file and save it.

I also highly recommend to enable relative line numbers, by adding `vim.opt.relativenumber = true` to the same config file.

## How to use Vim/Neovim

You just installed Vim/Neovim, but you don't know how to use. Luckly, there are some things that can help you learn to use it.

First, I highly recommend you to run `nvim` (or `lvim`) and type `:Tutor`. This will open the user manual of Vim. But at the end is a little complicated to remember everything so you need a lot of pratice.

![Neovim Tutorial](https://i.imgur.com/eH1UIlO.gif)

To get you ready for using Vim, you need to learn the basics concepts of it.

###### Moving the cursor

To move the cursor, press the h,j,k,l keys as indicated.

![HJKL](https://i.imgur.com/DDq4WCS.png)

###### Exiting Vim

Hit the keys `Shift` + `z` + `q` to exit without saving anything, or `Shift` + `z` + `z` to exit saving everything.

###### Understanding Vim Modes

Vim have some modes you can work with:

* Normal Mode 
* Insert Mode
* Delete Mode
* Visual Mode       
* Replace Mode     
* Command Mode

Let's break down these modes, one by one.

### Normal Mode

This is the mode you gonna be all the time when using vim. You can move through the file by using h,j,k,l keys.

### Insert Mode

Insert text to your file, but you can't use h,j,k,l. To enter this mode just hit `a` to insert text text after the character your cursor is currently in, or press `i` to insert text before.

### Delete Mode

Delete an entire line by hitting the key `d` twice. You can also delete the letter your cursor is currently in by pressing `x` once.

### Visual Mode

Highlight any line, word, letter, by using h,j,k,l. This is really useful because you can highlight and combine with delete mode in order to delete multiple lines. If you want to highlight an entire line, hit `Shift ` + `v`.

### Replace Mode

You can replace any letter by hitting `r` and putting the letter you want.

### Command Mode

In this mode, you can run any commands like `:Tutor` from earlier. But you can also run terminal commands by typing `:!` and put whatever terminal command you would like to run.

You can also search any word by hitting `/` and put whatever word you want to search to.

You made it. Now that you know the basics, you can start to improve your capabilities.

### Moving Vertically

You can press any numbers on your keyboard and press `j` to go down based on the relative line number or `k` to go up, line this:

![Relative line numbers movement](https://i.imgur.com/BNSeqwt.gif)

### Moving Horizontally

One helpful horizontal movement is to press `t` and whatever character you want the cursor to stand before it.

You can also press any number and `w` to go foward and `b` to go backwards. As you see, it goes x words to the direction you want. But you don't wanna count the words you have to go, so we can afford to other methods.


![Word by word movement](https://i.imgur.com/Xdp1VYH.gif)

## LunarVim features

### Terminals

By hitting `Alt` + `1` you will open a new terminal. You can press any number you want up to 9.

### File Explorer

Just hit `Space` + `e` and you will open the file explorer. To move between the file explorer and your file, just hit `Ctrl` + `h` or `l`. The same words for up and down, respectivily `k` and `j`.

To create a new file, just hit `a`. You will see a prompt asking for the name of the folder or the file. If you want a folder, type the name of the folder and add `/` to the end. If you want a file, you leave it empty and make sure your file has a file extension like `.js` or `.rs`.

To go back to the dashboard screen, hit `Space` + `;`.

That's it. Now, you know all the basics of Vim/Neovim and LunarVim.

