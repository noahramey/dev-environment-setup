![Apple Logo](https://cdn3.iconfinder.com/data/icons/picons-social/57/56-apple-256.png)

# MacOS Computer Setup for Devs
> Applicable to any developers, but I will be going in-depth on the Ruby/Rails installation.

I used to hate the process of setting up my dev environment on a fresh computer, but with this guide, I've narrowed down the process to keep it simple and help people setup their new computers with ease. Let's get started!

## The Process

### Getting Started / Homebrew

You're going to need a fresh installation of MacOS, along with a user Admin account. I always start by installing [Homebrew](https://brew.sh/), an amazing package manager available on MacOS. Copy and paste the line below into your Terminal. You will be asked for your password at some point during the Homebrew install.
```shell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
This will install Homebrew, as well as install Xcode's command line tools, which is Apple's GCC compiler. After the command has finished running, restart your terminal (this is not necessary but I do it to make sure Homebrew has successfully completed the installation).

### Applications

Homebrew makes installing packages incredibly simple, but it also helps with installing applications! You can use `brew cask` to install applications without struggling to download disk images for every application. Below I will include lines to download a few of my applications of choice.
```shell
brew cask install atom # My text editor of choice, but you can use whatever you prefer.
brew cask install spectacle # For resizing windows with keystrokes. Very helpful.
brew cask install iterm2 # A better terminal with more options.
brew cask install alfred # A spotlight replacement.
brew cask install google-chrome # I suggest this for the Dev tools, also Chrome is just great in general.
```

### Zsh and Git

Once you've installed the applications above, go ahead and quit Terminal and open iTerm2. We will be using iTerm2 as our terminal application from here on out. We will be using zsh instead of bash as our shell, as it's more customizable. We will be using [Oh My Zsh](https://github.com/robbyrussell/oh-my-zsh) to manage our zsh configuration. Copy and paste the line below to install and start using zsh. You will have to enter your password once during installation.
```shell
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
After installation, you will be using zsh! A nice feature from Oh My Zsh is the ability to use themes. In your home directory `~`, you will find a file called `.zshrc`, which will hold all of your zsh configurations. On line 10, you will find `ZSH_THEME="robbyrussell"`. You can choose your own theme from the [Oh My Zsh themes wiki](https://github.com/robbyrussell/oh-my-zsh/wiki/themes) to style your shell as you wish! I, personally, prefer the cloud theme.  

Now we will install Git, a widely used version control system. Git has a simple installation available through Homebrew. Copy and paste the line below (minus the comment) and you're done!
```shell
brew install git # yes it's that easy.
```
Restart iTerm to be safe. I also suggest configuring Git to use your name and email by using the following lines.
```shell
git config --global user.name "YOURNAME" # replace YOURNAMEHERE with your name
git config --global user.email YOUREMAIL # replace YOUREMAILHERE with your email
```
And you're done! Zsh and Git are successfully installed! Next we're going to install a few packages with Brew.
