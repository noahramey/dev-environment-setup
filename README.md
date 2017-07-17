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
$ brew cask install atom # My text editor of choice, but you can use whatever you prefer.
$ brew cask install spectacle # For resizing windows with keystrokes. Very helpful.
$ brew cask install iterm2 # A better terminal with more options.
$ brew cask install alfred # A spotlight replacement.
$ brew cask install google-chrome # I suggest this for the Dev tools, also Chrome is just great in general.
```

### Zsh and Git

Once you've installed the applications above, go ahead and quit Terminal and open iTerm2. We will be using iTerm2 as our terminal application from here on out. We will be using zsh instead of bash as our shell, as it's more customizable. We will be using [Oh My Zsh](https://github.com/robbyrussell/oh-my-zsh) to manage our zsh configuration. Copy and paste the line below to install and start using zsh. You will have to enter your password once during installation.
```shell
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```
After installation, you will be using zsh! A nice feature from Oh My Zsh is the ability to use themes. In your home directory `~`, you will find a file called `.zshrc`, which will hold all of your zsh configurations. On line 10, you will find `ZSH_THEME="robbyrussell"`. You can choose your own theme from the [Oh My Zsh themes wiki](https://github.com/robbyrussell/oh-my-zsh/wiki/themes) to style your shell as you wish! To change your theme, replace `robbyrussell` with your desired theme. I, personally, prefer the cloud theme.  

Now we will install Git, a widely used version control system. Git has a simple installation available through Homebrew. Copy and paste the line below (minus the comment) and you're done!
```shell
$ brew install git # Yes it's that easy.
```

Restart iTerm to be safe. I also suggest configuring Git using the following lines. These store your name and email with Git, set Atom as Git's default editor, and color code Git information.
```shell
$ git config --global user.name "YOURNAME" # Replace YOURNAMEHERE with your name.
$ git config --global user.email YOUREMAIL # Replace YOUREMAILHERE with your email.
$ echo "export EDITOR='atom -w'" >> ~/.zshrc # Restart iTerm after this one.
$ git config --global color.ui true
```

And you're done! Zsh and Git are successfully installed! Next we're going to install a few packages with Brew.

### Node and PostgreSQL

Node.js and PostgreSQL are both important but different technologies. Node.js is a Javascript runtime, and PostgreSQL is a database system. I suggest installing both as they are widely used, also they're awesome and I love them both. Let's start with Node. To install node you just copy and paste the following line.
```shell
$ brew install node
```

And you're done! The Node Homebrew package installs the Javascript runtime and npm, which is node's package manager.  

Now for PostgreSQL. To install Postgres, copy and paste the following brew install line.
```shell
$ brew install postgres
```

Homebrew makes it easy. From here you have to decide whether you want to keep Postgres running in the background or run it in an instance in your terminal. I prefer to run it in the background. To run it in the background just run the following line.
```shell
$ brew services start postgresql
```

Now Postgres will always run in the background, even if you restart your computer! I also suggest creating a default database with your username. Run `createdb $USER` in your terminal. This also helps the `psql` command, so that your computer has a default database to connect to. Postgres is now all setup!

### Ruby/Rails

This one gets a little more complicated, let me explain why. A fresh install of MacOS come with Ruby already installed. If I retrieve my Ruby version in the terminal, I should get the following.
```shell
$ ruby -v
ruby 2.0.0p648 (2015-12-16 revision 53162) [universal.x86_64-darwin16]
```
At first glance, this seems like it would be helpful, but that Ruby version is out of date. We need to be using Ruby-2.2 or above, as Rails 5 requires that version or above. The process we'll be using allows us to install multiple ruby versions and switch between them as needed. Let's get started!

##### Ruby-Install

We'll start by using ruby-install, a tool for installing Ruby versions. After that install, we'll be installing Ruby version 2.4.1, the latest stable release of Ruby. The lines below will walk you through this process. In your terminal, enter the following lines to install ruby-install and Ruby-2.4.1. The ruby-install command will take some time.
```shell
$ brew install ruby-install
$ ruby-install ruby 2.4.1
```

##### Chruby

Now we'll be installing Chruby, a tool for managing installed ruby versions. Let's start by installing it with Homebrew (isn't Homebrew so helpful?)
```shell
brew install chruby
```
Once you've installed chruby, use the following lines to configure zsh to use chruby and allow auto-switching between ruby versions.
```shell
$ echo 'source /usr/local/opt/chruby/share/chruby/chruby.sh' >> ~/.zshrc
$ echo 'source /usr/local/opt/chruby/share/chruby/auto.sh' >> ~/.zshrc

# Setting your computers default ruby version to 2.4.1
$ echo "ruby-2.4.1" > ~/.ruby-version
# Used so that documentation is not installed when installing ruby gems.
$ echo "gem --no-ri --no-rdoc" > ~/.gemrc
```
After you've run all of these commands, **Restart your terminal**, this is important for the process of installing Rails, which we will do next. When you reopen iTerm, run `ruby -v` and you should get your new Ruby version!
```shell
$ ruby -v
ruby 2.4.1p111 (2017-03-22 revision 58053) [x86_64-darwin16]
```

##### Rails

This step can be very error prone. I suggest restarting your terminal before starting the Rails installation process. Rails is a web-application framework written in Ruby. It goes hand in hand with Ruby and I suggest it to anyone looking to learn a framework. Let's get started! At this point if you run `rails` in your terminal, you should get an error that looks like this.
```shell
$ rails
Rails is not currently installed on this system. To get the latest version, simply type:

    $ sudo gem install rails

You can then rerun your "rails" command.
```
**Do not use that command**, this is very important. When you run `sudo gem install rails`, it uses the system's default version of Ruby (which is 2.0.0) to install Rails. These versions are incompatible, and will give you a very hard time with your installation. Instead, run `$ gem install rails` in your terminal, **without the sudo**. This will install Rails 5 on your new Ruby version. **Restart your terminal** and try to create a new Rails app. You should get the following:
```shell
$ rails new project
      create
      create  README.md
      create  Rakefile
      create  config.ru
      create  .gitignore
      create  Gemfile
         run  git init from "."
      etc..........
```
It worked! Rails is now successfully installed!

## You did it!

I hope this helped setup your dev environment on MacOS. If you have anything you think I should add, please clone this repository and make a PR! I would love feedback of any kind.

#### License

This guide is released under the [MIT License](./LICENSE)
