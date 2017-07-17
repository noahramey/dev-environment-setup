![Apple Logo](https://cdn3.iconfinder.com/data/icons/picons-social/57/56-apple-256.png)

# MacOS Computer Setup for Developers
> Applicable to any developers, but I will be going in-depth on the Ruby/Rails installation.

I used to hate the process of setting up my dev environment on a fresh computer, but with this guide, I've narrowed down the process to keep it simple and help people setup their new computers with ease. Let's get started!

## The Process

### Getting Started / Homebrew

You're going to need a fresh installation of MacOS, along with a user Admin account. I always start by installing Homebrew, an amazing package manager available on MacOS. Copy and paste the line below into your Terminal. You will be asked for your password at some point during the Homebrew install.
```shell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
This will install Homebrew, as well as install Xcode's command line tools, which is Apple's GCC compiler. After the command has finished running, restart your terminal (this is not necessary but I do it to make sure Homebrew has successfully completed the installation).
