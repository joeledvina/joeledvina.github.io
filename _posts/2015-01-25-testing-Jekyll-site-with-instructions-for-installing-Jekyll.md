---
layout:post
title: Installing Jekyll to serve GitHub.io website
---

Installing Jekyll to serve GitHub.io website

###Trying to follow the instructions [from GitHub](https://help.github.com/articles/using-jekyll-with-pages/)
This is probably not at all worth all of the hassle

Installed GitHub Windows client

1. "installed" Ruby in a folder (C:\Ruby21-x64)

    - version 2.1.5 64-bit from [rubyinstaller](http://rubyinstaller.org)

    - added the directory to the Windows PATH

2. installing "bundler" by passing `gem install bundler`

   - Got an ssl error, but found the workaround [here](https://gist.github.com/luislavena/f064211759ee0f806c88)
downloaded the [latest Rubygems release (2.2.3)](https://github.com/rubygems/rubygems/releases/tag/v2.2.3) for my version of Ruby

   - in command prompt, passed `C:\>gem install --local` then `C:\rubygems-update-1.8.30.gem` and then `C:\>update_rubygems --no-ri --no-rdoc` to install the updated gems, then passed `C:\>gem uninstall rubygems-update -x` to remove the updater

   - Added a file name "Gemfile" to the GitHub.io repository, and used a text editor to add the following:

```ruby
source 'https://rubygems.org'
gem 'github-pages'
```

   - after all of the above, `gem install bundler` gave me an error that indicated I needed to install the Ruby devkit

   - downloaded the [devkit for my version of Ruby](http://cdn.rubyinstaller.org/archives/devkits/DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe) from the [rubyinstaller downloads page[(http://rubyinstaller.org/downloads/)
   
   - extracted the devkit to C:\rubydevkit
   
   - ran the included "devkitvars.bat" that is supposed to add the devkit to the Windows PATH, then ran it as admin, but it didn't work, so I added `C:\rubydev\bin` and `C:\rubydev\mingw\bin` to PATH
   
   - folowing the [instructions for the devkit](https://github.com/oneclick/rubyinstaller/wiki/Development-Kit), opened a cmd window in the rubydev directory and ran `ruby dk.rb init` and `ruby dk.rb install` to bind it to ruby installations in your path.

   - after all of that hassle, the install was successful
 
3. run Jekyll using `bundle exec jekyll serve` in the root of the repository

   - To ensure the local development environment is using the same version of Jekyll and its dependencies as GitHub Pages, periodically run the command `gem update github-pages` (or `bundle update github-pages` if using Bundler)

4. I can then [view the website in my browser](http://localhost:4000/).

