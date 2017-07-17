![Apple Logo](https://cdn3.iconfinder.com/data/icons/picons-social/57/56-apple-256.png)

# MacOS Computer Setup for Devs
> Applicable to any developers, but I will be going in-depth on the Ruby/Rails installation.

I used to hate the process of setting up my dev environment on a fresh computer, but with this guide, I've narrowed down the process to keep it simple and help people setup their new computers with ease. Let's get started!

## The Process

### Getting Started / Homebrew

You're going to need a fresh installation of MacOS, along with a user Admin account. I always start by installing Homebrew, an amazing package manager available on MacOS. Copy and paste the line below into your Terminal. You will be asked for your password at some point during the Homebrew install.
```shell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
This will install Homebrew, as well as install Xcode's command line tools, which is Apple's GCC compiler. After the command has finished running, restart your terminal (this is not necessary but I do it to make sure Homebrew has successfully completed the installation).

### Applications

Homebrew makes installing packages incredibly simple, but it also helps with installing applications! You can use `brew cask` to install applications without struggling to download disk images for every application. Below I will include lines to download a few of my favorite applications.
```shell
brew cask install atom # My text editor of choice, but you can use whatever you prefer.
brew cask install spectacle # For resizing windows with keystrokes. Very helpful.
brew cask install iterm2 # A better terminal with more options.
brew cask install alfred # A spotlight replacement.
brew cask install google-chrome # I suggest this for the Dev tools, also Chrome is just great in general.
```
