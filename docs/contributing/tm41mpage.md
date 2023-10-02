---
layout: default
title: tm41m.github.io
nav_order: 3
parent: Contributing
---

# Quick Start

## Local Development

### On Ubuntu
  1. Install `rvm` using [https://rvm.io/rvm/install](https://rvm.io/rvm/install), `rvm --version` should return something equivalent to
  ```
   rvm 1.29.12 (latest) by Michal Papis, Piotr Kuczynski, Wayne E. Seguin [https://rvm.io]
  ```

  2. Install a version of ruby that is compatible with the Gemfile dependencies. @thecartercodes used `rvm install ruby-2.7.2`.
  Your version should look similar to this `ruby 2.7.2p137 (2020-10-01 revision 5445e04352) [x86_64-linux]`

  3. Run `bundle install`

  4. Run `bundle exec jekyll serve` to start a local instance of the site.

### On Mac
  1. Install Homebrew if not already installed via `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
  2. Run `brew install chruby ruby-install xz` to install `chruby` and `ruby-install` using Homebrew
  3. Run `ruby-install ruby 3.1.3` to install the latest version of Ruby supported by Jekyll (at the time of writing, this is Ruby 3.1.3)
  4. Configure your shell to automatically use the version manager `chruby`:
  ```
    echo "source $(brew --prefix)/opt/chruby/share/chruby/chruby.sh" >> ~/.zshrc
    echo "source $(brew --prefix)/opt/chruby/share/chruby/auto.sh" >> ~/.zshrc
    echo "chruby ruby-3.1.3" >> ~/.zshrc # run 'chruby' to see actual version
  ```
  Note: If you are using a Bash shell, replace `zshrc` with `.bash_profile` in the above commands. MacOS Catalina and later default to Zsh, but an easy way to check is to enter any nonsensical command into your terminal and read the first word of the output. For instance, entering `asdf` in Zsh will yield 
  `zsh: asdf: command not found` and `bash: asdf: command not found` in Bash.
  5. Quit and relaunch terminal, then run `ruby -v`. If you recieve something similar to `ruby 3.1.3p185 (2022-11-24 revision 1a6b16756e)`, then everything is working. If not, refer to the previous step and ensure that you aligned the command with the shell you are using (Zsh or Bash)
  6. Run `gem install jekyll` to install Jekyll as a Ruby gem 
  7. Run `bundle exec jekyll serve` in the root of the cloned repository to start a local instance of the site

### Contact

Visit [tm41m.io](tm41m.io) or contact admin@tm41m.com for more information.