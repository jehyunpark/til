# How to Install jekyll on Ubuntu 14.04
# Install
### Install Ruby
1. Install RVM
```
\curl -L https://get.rvm.io | bash -s stable
```
```
//If you have an error
gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
\curl -L https://get.rvm.io | bash -s stable
```
- Apply RVM
```
source ~/.rvm/scripts/rvm
```
- Install Ruby
```
rvm install 2.3.0
```

### Install RubyGems
1. Download RubyGems
https://rubygems.org/pages/download
- Unpack downloaded file into a directory
- cd there
- ```$ ruby setup.rb```
- If you have rubygems version error `sudo gem update --system`


### Install jekyll
```
rvmsudo gem install jekyll
```


# Reference
### Remove Ruby
http://stackoverflow.com/questions/22753785/how-to-remove-ruby-from-ubuntu

1. Use this to find out what executable you're running:
```
$ which ruby
/usr/bin/ruby
```
- Use this to find out what it actually is:
```
$ readlink -f /usr/bin/ruby
/usr/bin/ruby1.8
```
- Use this to find out what package it belongs to:
```
$ dpkg -S /usr/bin/ruby1.8
ruby1.8: /usr/bin/ruby1.8
```
- Use this to uninstall that:
```
$ apt-get purge ruby1.8
```
