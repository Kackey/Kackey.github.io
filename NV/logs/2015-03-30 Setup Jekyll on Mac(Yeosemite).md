


# Log and Fails

- Tried to install jeklly into system ruby, but failed.


```bash
Last login: Fri Mar 27 05:25:40 on ttys000
iMac:~ hide$ ruby --version
ruby 2.0.0p481 (2014-05-08 revision 45883) [universal.x86_64-darwin14]

iMac:~ hide$ gem install bundler
Fetching: bundler-1.9.1.gem (100%)
ERROR:  While executing gem ... (Gem::FilePermissionError)
    You dont have write permissions for the /Library/Ruby/Gems/2.0.0 directory.

iMac:~ hide$ ls -al /Library/Ruby/Gems/2.0.0/
total 0
drwxr-xr-x  7 root  wheel  238  9 10  2014 .
drwxr-xr-x  3 root  wheel  102  9 10  2014 ..
drwxr-xr-x  2 root  wheel   68  9 10  2014 build_info
drwxr-xr-x  2 root  wheel   68  9 10  2014 cache
drwxr-xr-x  2 root  wheel   68  9 10  2014 doc
drwxr-xr-x  5 root  wheel  170  9 10  2014 gems
drwxr-xr-x  3 root  wheel  102  9 10  2014 specifications

iMac:~ hide$ who am i
hide     ttys000  Mar 29 15:30

iMac:~ hide$ sudo root

WARNING: Improper use of the sudo command could lead to data loss
or the deletion of important system files. Please double-check your
typing when using sudo. Type "man sudo" for more information.

To proceed, enter your password, or type Ctrl-C to abort.

Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
Sorry, try again.
sudo: 3 incorrect password attempts

iMac:~ hide$ sudo su root

WARNING: Improper use of the sudo command could lead to data loss
or the deletion of important system files. Please double-check your
typing when using sudo. Type "man sudo" for more information.

To proceed, enter your password, or type Ctrl-C to abort.

Password:
Sorry, try again.
Password:
sudo: 1 incorrect password attempt
iMac:~ hide$
iMac:~ hide$ su root
Password:
su: Sorry
```

- *Failure*: [Mac] "root" should have been active in mac env setting.
  - [Mac OS X で「ルート」ユーザを有効にして使用する - Apple サポート](https://support.apple.com/ja-jp/HT1528)


- *Failure*: [Mac] "sudo" command is not unavailable <Trans:非ブランクパスワードを変更するまで>
  - [Mac OS X：sudo コマンドには非ブランク管理パスワードが必要 - Apple サポート](https://support.apple.com/ja-jp/HT202035)


Tried to install bundler by root priviledge.
```bash
iMac:~ hide$ su root
Password:
sh-3.2# gem install bundler
Fetching: bundler-1.9.1.gem (100%)
Successfully installed bundler-1.9.1
Parsing documentation for bundler-1.9.1
Installing ri documentation for bundler-1.9.1
1 gem installed

sh-3.2# gem uni $(gem li --no-versions)
ERROR:  While executing gem ... (Gem::InstallError)
    gem "test-unit" cannot be uninstalled because it is a default gem
sh-3.2# gem list | cut -d" " -f1 | xargs gem uninstall -aIx
ERROR:  While executing gem ... (Gem::InstallError)
    gem "test-unit" cannot be uninstalled because it is a default gem
sh-3.2# gem list

*** LOCAL GEMS ***

activesupport (4.2.1)
bigdecimal (1.2.0)
blankslate (2.1.2.4)
celluloid (0.16.0)
CFPropertyList (2.2.8)
classifier-reborn (2.0.3)
coffee-script (2.3.0)
coffee-script-source (1.9.1)
colorator (0.1)
execjs (2.4.0)
fast-stemmer (1.0.2)
ffi (1.9.8)
gemoji (2.1.0)
github-pages-health-check (0.2.2)
hitimes (1.2.2)
i18n (0.7.0)
io-console (0.4.2)
jekyll (2.4.0)
jekyll-coffeescript (1.0.1)
jekyll-gist (1.2.1)
jekyll-paginate (1.1.0)
jekyll-sass-converter (1.2.0)
jekyll-watch (1.2.1)
json (1.8.2, 1.7.7)
kramdown (1.5.0)
libxml-ruby (2.6.0)
liquid (2.6.1)
listen (2.10.0)
mercenary (0.3.5)
mini_portile (0.6.2)
minitest (5.5.1, 4.3.2)
net-dns (0.8.0)
nokogiri (1.5.6)
parslet (1.5.0)
posix-spawn (0.3.10)
psych (2.0.0)
public_suffix (1.5.0)
pygments.rb (0.6.1)
rake (0.9.6)
rb-fsevent (0.9.4)
rb-inotify (0.9.5)
rdoc (4.0.0)
redcarpet (3.1.2)
RedCloth (4.2.9)
safe_yaml (1.0.4)
sass (3.4.13)
sqlite3 (1.3.7)
test-unit (2.0.0.0)
thread_safe (0.3.5)
timers (4.0.1)
toml (0.1.2)
tzinfo (1.2.2)
yajl-ruby (1.2.1)
sh-3.2# pwd
/Users/hide
sh-3.2# gem uninstall bundler
```

```bash
To proceed, enter your password, or type Ctrl-C to abort.

Password:
Sorry, try again.
Password:
```
#### Failed: Rootでbundlerを実行したら「rootでbundler呼ぶと、non-rootからアプリ使えないようになるよ」と警告がでたので中止

```bash
sudo: 1 incorrect password attempt
iMac:Kackey.github.io hide$ su root
Password:
sh-3.2# bundle install
Dont run Bundler as root. Bundler can ask for sudo if it is needed, and installing your bundle as root will break this application for all non-root users on this machine.
Fetching gem metadata from https://rubygems.org/..........
Fetching version metadata from https://rubygems.org/..
Resolving dependencies...
Installing RedCloth 4.2.9
Installing i18n 0.7.0
^C
SystemExit: exit
An error occurred while installing json (1.8.2), and Bundler cannot continue.
Make sure that `gem install json -v '1.8.2'` succeeds before bundling.
sh-3.2# exit
exit
```

#### sudo使ってbundlerを動かしてみてもうまくいかない
```bash
iMac:Kackey.github.io hide$ sudo bundle install

WARNING: Improper use of the sudo command could lead to data loss
or the deletion of important system files. Please double-check your
typing when using sudo. Type "man sudo" for more information.

To proceed, enter your password, or type Ctrl-C to abort.

Password:
Sorry, try again.
Password:
Sorry, try again.
Password:
Sorry, try again.
sudo: 3 incorrect password attempts


iMac:Kackey.github.io hide$ bundle install
Fetching gem metadata from https://rubygems.org/..........
Fetching version metadata from https://rubygems.org/..
Resolving dependencies...
Using RedCloth 4.2.9
Using i18n 0.7.0

WARNING: Improper use of the sudo command could lead to data loss
or the deletion of important system files. Please double-check your
typing when using sudo. Type "man sudo" for more information.

To proceed, enter your password, or type Ctrl-C to abort.



Your user account isnt allowed to install to the system Rubygems.
You can cancel this installation and run:

    bundle install --path vendor/bundle

to install the gems into ./vendor/bundle/, or you can enter your password
and install the bundled gems to Rubygems using sudo.

Password:
Installing json 1.8.2
Installing minitest 5.5.1
Installing thread_safe 0.3.5
Installing tzinfo 1.2.2
Installing activesupport 4.2.1
Installing blankslate 2.1.2.4
Installing hitimes 1.2.2
Installing timers 4.0.1
Installing celluloid 0.16.0
Installing fast-stemmer 1.0.2
Installing classifier-reborn 2.0.3
Installing coffee-script-source 1.9.1
Installing execjs 2.4.0
Installing coffee-script 2.3.0
Installing colorator 0.1
Installing ffi 1.9.8
Installing gemoji 2.1.0
Installing net-dns 0.8.0
Installing public_suffix 1.5.0
Installing github-pages-health-check 0.2.2
Installing jekyll-coffeescript 1.0.1
Installing jekyll-gist 1.2.1
Installing jekyll-paginate 1.1.0
Installing sass 3.4.13
Installing jekyll-sass-converter 1.2.0
Installing rb-fsevent 0.9.4
Installing rb-inotify 0.9.5
Installing listen 2.10.0
Installing jekyll-watch 1.2.1
Installing kramdown 1.5.0
Installing liquid 2.6.1
Installing mercenary 0.3.5
Installing posix-spawn 0.3.10
Installing yajl-ruby 1.2.1
Installing pygments.rb 0.6.1
Installing redcarpet 3.1.2
Installing safe_yaml 1.0.4
Installing parslet 1.5.0
Installing toml 0.1.2
Installing jekyll 2.4.0
Installing mini_portile 0.6.2

Gem::Installer::ExtensionBuildError: ERROR: Failed to build gem native extension.

    /System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/bin/ruby extconf.rb
checking if the C compiler accepts ... yes
checking if the C compiler accepts -Wno-error=unused-command-line-argument-hard-error-in-future... no
Building nokogiri using packaged libraries.
-----
The file "/usr/include/iconv.h" is missing in your build environment,
which means you haven't installed Xcode Command Line Tools properly.

To install Command Line Tools, try running `xcode-select --install` on
terminal and follow the instructions.  If it fails, open Xcode.app,
select from the menu "Xcode" - "Open Developer Tool" - "More Developer
Tools" to open the developer site, download the installer for your OS
version and run it.
-----
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of necessary
libraries and/or headers.  Check the mkmf.log file for more details.  You may
need configuration options.

Provided configuration options:
        --with-opt-dir
        --without-opt-dir
        --with-opt-include
        --without-opt-include=${opt-dir}/include
        --with-opt-lib
        --without-opt-lib=${opt-dir}/lib
        --with-make-prog
        --without-make-prog
        --srcdir=.
        --curdir
        --ruby=/System/Library/Frameworks/Ruby.framework/Versions/2.0/usr/bin/ruby
        --help
        --clean
        --use-system-libraries
        --enable-static
        --disable-static
        --with-zlib-dir
        --without-zlib-dir
        --with-zlib-include
        --without-zlib-include=${zlib-dir}/include
        --with-zlib-lib
        --without-zlib-lib=${zlib-dir}/lib
        --enable-cross-build
        --disable-cross-build


Gem files will remain installed in /var/folders/3n/c73k_7695zvc059rvqdb8xwh0000gp/T/bundler20150329-4429-1q5flih/nokogiri-1.6.6.2/gems/nokogiri-1.6.6.2 for inspection.
Results logged to /var/folders/3n/c73k_7695zvc059rvqdb8xwh0000gp/T/bundler20150329-4429-1q5flih/nokogiri-1.6.6.2/gems/nokogiri-1.6.6.2/ext/nokogiri/gem_make.out
An error occurred while installing nokogiri (1.6.6.2), and Bundler cannot continue.
Make sure that `gem install nokogiri -v '1.6.6.2'` succeeds before bundling.
iMac:Kackey.github.io hide$ gem install nokogiri -v '1.6.6.2'
Fetching: nokogiri-1.6.6.2.gem (100%)
ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.0.0 directory.
iMac:Kackey.github.io hide$ gem install bundler
ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.0.0 directory.
iMac:Kackey.github.io hide$ gem uninstall bundler
Remove executables:
        bundle, bundler

in addition to the gem? [Yn]  y
ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /usr/bin directory.
iMac:Kackey.github.io hide$ sudo gem uninstall bundler
Password:
Remove executables:
        bundle, bundler

in addition to the gem? [Yn]  y
Removing bundle
Removing bundler
Successfully uninstalled bundler-1.9.1
iMac:Kackey.github.io hide$ gem install bundler
ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.0.0 directory.
iMac:Kackey.github.io hide$ ruby --version
ruby 2.0.0p481 (2014-05-08 revision 45883) [universal.x86_64-darwin14]
iMac:Kackey.github.io hide$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
==> This script will install:
/usr/local/bin/brew
/usr/local/Library/...
/usr/local/share/man/man1/brew.1
==> The following directories will be made group writable:
/usr/local/.
/usr/local/bin
==> The following directories will have their group set to admin:
/usr/local/.
/usr/local/bin

Press RETURN to continue or any other key to abort
==> /usr/bin/sudo /bin/chmod g+rwx /usr/local/. /usr/local/bin
==> /usr/bin/sudo /usr/bin/chgrp admin /usr/local/. /usr/local/bin
==> /usr/bin/sudo /bin/mkdir /Library/Caches/Homebrew
==> /usr/bin/sudo /bin/chmod g+rwx /Library/Caches/Homebrew
==> Downloading and installing Homebrew...
remote: Counting objects: 239511, done.
remote: Total 239511 (delta 0), reused 0 (delta 0), pack-reused 239511
Receiving objects: 100% (239511/239511), 33.43 MiB | 244.00 KiB/s, done.
Resolving deltas: 100% (178295/178295), done.
From https://github.com/Homebrew/homebrew
 * [new branch]      master     -> origin/master
HEAD is now at 85287aa harbour: modernize, extend test, format test
==> Installation successful!
==> Next steps
Run `brew doctor` before you install anything
Run `brew help` to get started
iMac:Kackey.github.io hide$ $ echo 'export PATH=/usr/local/bin:$PATH' >> .bash_profile
bash: $: command not found
iMac:Kackey.github.io hide$ echo 'export PATH=/usr/local/bin:$PATH' >> .bash_profile
iMac:Kackey.github.io hide$ source .bash_profile
iMac:Kackey.github.io hide$ brew doctor
Your system is ready to brew.
iMac:Kackey.github.io hide$ brew update
Already up-to-date.
iMac:Kackey.github.io hide$ brew install git
==> Downloading https://homebrew.bintray.com/bottles/git-2.3.4.yosemite.bottle.tar.gz
######################################################################## 100.0%
==> Pouring git-2.3.4.yosemite.bottle.tar.gz
==> Caveats
The OS X keychain credential helper has been installed to:
  /usr/local/bin/git-credential-osxkeychain

The "contrib" directory has been installed to:
  /usr/local/share/git-core/contrib

Bash completion has been installed to:
  /usr/local/etc/bash_completion.d

zsh completion has been installed to:
  /usr/local/share/zsh/site-functions
==> Summary
🍺  /usr/local/Cellar/git/2.3.4: 1362 files,  31M
iMac:Kackey.github.io hide$ brew install redline
Error: No available formula for redline
Searching formulae...
Searching taps...
iMac:Kackey.github.io hide$ brew instal readline
==> Downloading https://homebrew.bintray.com/bottles/readline-6.3.8.yosemite.bottle.tar.gz
######################################################################## 100.0%
==> Pouring readline-6.3.8.yosemite.bottle.tar.gz
==> Caveats
This formula is keg-only, which means it was not symlinked into /usr/local.

Mac OS X provides similar software, and installing this software in
parallel can cause all kinds of trouble.

OS X provides the BSD libedit library, which shadows libreadline.
In order to prevent conflicts when programs look for libreadline we are
defaulting this GNU Readline installation to keg-only.

Generally there are no consequences of this for you. If you build your
own software and it requires this formula, you'll need to add to your
build variables:

    LDFLAGS:  -L/usr/local/opt/readline/lib
    CPPFLAGS: -I/usr/local/opt/readline/include

==> Summary
🍺  /usr/local/Cellar/readline/6.3.8: 40 files, 2.1M
iMac:Kackey.github.io hide$ brew install openssl
==> Downloading https://homebrew.bintray.com/bottles/openssl-1.0.2a-1.yosemite.bottle.tar.gz
######################################################################## 100.0%
==> Pouring openssl-1.0.2a-1.yosemite.bottle.tar.gz
==> Caveats
A CA file has been bootstrapped using certificates from the system
keychain. To add additional certificates, place .pem files in
  /usr/local/etc/openssl/certs

and run
  /usr/local/opt/openssl/bin/c_rehash

This formula is keg-only, which means it was not symlinked into /usr/local.

Mac OS X already provides this software and installing another version in
parallel can cause all kinds of trouble.

Apple has deprecated use of OpenSSL in favor of its own TLS and crypto libraries

Generally there are no consequences of this for you. If you build your
own software and it requires this formula, you'll need to add to your
build variables:

    LDFLAGS:  -L/usr/local/opt/openssl/lib
    CPPFLAGS: -I/usr/local/opt/openssl/include

==> Summary
🍺  /usr/local/Cellar/openssl/1.0.2a-1: 463 files,  18M
iMac:Kackey.github.io hide$ brew install ruby-build
==> Installing dependencies for ruby-build: autoconf, pkg-config
==> Installing ruby-build dependency: autoconf
==> Downloading https://homebrew.bintray.com/bottles/autoconf-2.69.yosemite.bottle.1.tar.gz
######################################################################## 100.0%
==> Pouring autoconf-2.69.yosemite.bottle.1.tar.gz
🍺  /usr/local/Cellar/autoconf/2.69: 70 files, 3.1M
==> Installing ruby-build dependency: pkg-config
==> Downloading https://homebrew.bintray.com/bottles/pkg-config-0.28.yosemite.bottle.2.tar.gz
######################################################################## 100.0%
==> Pouring pkg-config-0.28.yosemite.bottle.2.tar.gz
🍺  /usr/local/Cellar/pkg-config/0.28: 10 files, 612K
==> Installing ruby-build
==> Downloading https://github.com/sstephenson/ruby-build/archive/v20150319zf.tar.gz
######################################################################## 100.0%


curl: (7) Failed to connect to codeload.github.com port 443: Operation timed out
Error: Failed to download resource "ruby-build"
Download failed: https://github.com/sstephenson/ruby-build/archive/v20150319zf.tar.gz
iMac:Kackey.github.io hide$
iMac:Kackey.github.io hide$
iMac:Kackey.github.io hide$ brew install ruby-build
==> Downloading https://github.com/sstephenson/ruby-build/archive/v20150319zf.tar.gz
######################################################################## 100.0%
curl: (7) Failed to connect to codeload.github.com port 443: Operation timed out
Error: Failed to download resource "ruby-build"
Download failed: https://github.com/sstephenson/ruby-build/archive/v20150319zf.tar.gz
iMac:Kackey.github.io hide$ brew install renv
Error: No available formula for renv
Searching formulae...
direnv
Searching taps...
iMac:Kackey.github.io hide$ brew install rbenv
==> Downloading https://github.com/sstephenson/rbenv/archive/v0.4.0.tar.gz
######################################################################## 100.0%
curl: (7) Failed to connect to codeload.github.com port 443: Operation timed out
Error: Failed to download resource "rbenv"
Download failed: https://github.com/sstephenson/rbenv/archive/v0.4.0.tar.gz
iMac:Kackey.github.io hide$ brew uninstall openssl
Uninstalling /usr/local/Cellar/openssl/1.0.2a-1...
iMac:Kackey.github.io hide$ brew search gcc
gcc
homebrew/versions/gcc43        homebrew/versions/gcc45        homebrew/versions/gcc47        homebrew/versions/gcc49        homebrew/dupes/apple-gcc42
homebrew/versions/gcc44        homebrew/versions/gcc46        homebrew/versions/gcc48        homebrew/versions/llvm-gcc28
iMac:Kackey.github.io hide$ brew install rbenv
==> Downloading https://github.com/sstephenson/rbenv/archive/v0.4.0.tar.gz
######################################################################## 100.0%
curl: (7) Failed to connect to codeload.github.com port 443: Operation timed out
Error: Failed to download resource "rbenv"
Download failed: https://github.com/sstephenson/rbenv/archive/v0.4.0.tar.gz
iMac:Kackey.github.io hide$ brew help
Example usage:
  brew [info | home | options ] [FORMULA...]
  brew install FORMULA...
  brew uninstall FORMULA...
  brew search [foo]
  brew list [FORMULA...]
  brew update
  brew upgrade [FORMULA...]
  brew pin/unpin [FORMULA...]

Troubleshooting:
  brew doctor
  brew install -vd FORMULA
  brew [--env | config]

Brewing:
  brew create [URL [--no-fetch]]
  brew edit [FORMULA...]
  open https://github.com/Homebrew/homebrew/blob/master/share/doc/homebrew/Formula-Cookbook.md

Further help:
  man brew
  brew home
iMac:Kackey.github.io hide$ brew install rbenv --verbose
==> Downloading https://github.com/sstephenson/rbenv/archive/v0.4.0.tar.gz
/usr/bin/curl -fLA Homebrew 0.9.5 (Ruby 2.0.0-481; Mac OS X 10.10.2) https://github.com/sstephenson/rbenv/archive/v0.4.0.tar.gz -C 0 -o /Library/Caches/Homebrew/rbenv-0.4.0.tar.gz.incomplete
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   125    0   125    0     0    112      0 --:--:--  0:00:01 --:--:--   112
  0     0    0     0    0     0      0      0 --:--:--  0:01:15 --:--:--     0curl: (7) Failed to connect to codeload.github.com port 443: Operation timed out
Error: Failed to download resource "rbenv"
Download failed: https://github.com/sstephenson/rbenv/archive/v0.4.0.tar.gz
iMac:Kackey.github.io hide$ brew install git
Warning: git-2.3.4 already installed
iMac:Kackey.github.io hide$ brew update git
This command updates brew itself, and does not take formula names.
Use `brew upgrade <formula>`.
iMac:Kackey.github.io hide$ brew upgrade git
Error: git 2.3.4 already installed
iMac:Kackey.github.io hide$ brew update
Updated Homebrew from 85287aa9 to 6e05920f.
==> Updated Formulae
cmake       csfml       encfs       ffmpeg      mesos       protobuf    shellcheck  skinny      syncthing
iMac:Kackey.github.io hide$ brew install rbenv
==> Downloading https://github.com/sstephenson/rbenv/archive/v0.4.0.tar.gz
######################################################################## 100.0%
==> Caveats
To use Homebrew's directories rather than ~/.rbenv add to your profile:
  export RBENV_ROOT=/usr/local/var/rbenv

To enable shims and autocompletion add to your profile:
  if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi
==> Summary
🍺  /usr/local/Cellar/rbenv/0.4.0: 31 files, 152K, built in 3 seconds
iMac:Kackey.github.io hide$ rbenv --version
/usr/local/Cellar/rbenv/0.4.0/libexec/rbenv---version: line 17: cd: /Users/hide/.rbenv: No such file or directory
iMac:Kackey.github.io hide$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bash_profile
iMac:Kackey.github.io hide$ cat ~/.bash_profile
export PATH=$HOME/.nodebrew/current/bin:$PATH
export PATH="$HOME/.rbenv/bin:$PATH"
iMac:Kackey.github.io hide$ echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
iMac:Kackey.github.io hide$ cat ~/.bash_profile
export PATH=$HOME/.nodebrew/current/bin:$PATH
export PATH="$HOME/.rbenv/bin:$PATH"
if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi
iMac:Kackey.github.io hide$ brew install ruby-build
==> Installing ruby-build dependency: openssl
==> Downloading https://homebrew.bintray.com/bottles/openssl-1.0.2a-1.yosemite.bottle.tar.gz
Already downloaded: /Library/Caches/Homebrew/openssl-1.0.2a-1.yosemite.bottle.tar.gz
==> Pouring openssl-1.0.2a-1.yosemite.bottle.tar.gz
==> Caveats
A CA file has been bootstrapped using certificates from the system
keychain. To add additional certificates, place .pem files in
  /usr/local/etc/openssl/certs

and run
  /usr/local/opt/openssl/bin/c_rehash

This formula is keg-only, which means it was not symlinked into /usr/local.

Mac OS X already provides this software and installing another version in
parallel can cause all kinds of trouble.

Apple has deprecated use of OpenSSL in favor of its own TLS and crypto libraries

Generally there are no consequences of this for you. If you build your
own software and it requires this formula, you'll need to add to your
build variables:

    LDFLAGS:  -L/usr/local/opt/openssl/lib
    CPPFLAGS: -I/usr/local/opt/openssl/include

==> Summary
🍺  /usr/local/Cellar/openssl/1.0.2a-1: 463 files,  18M
==> Installing ruby-build
==> Downloading https://github.com/sstephenson/ruby-build/archive/v20150319zf.tar.gz
######################################################################## 100.0%
curl: (7) Failed to connect to codeload.github.com port 443: Operation timed out
Error: Failed to download resource "ruby-build"
Download failed: https://github.com/sstephenson/ruby-build/archive/v20150319zf.tar.gz
iMac:Kackey.github.io hide$ brew update
Already up-to-date.
iMac:Kackey.github.io hide$ brew upgrade git
Error: git 2.3.4 already installed
iMac:Kackey.github.io hide$ brew uninstall git
Uninstalling /usr/local/Cellar/git/2.3.4...
iMac:Kackey.github.io hide$ brew upgrade git
Error: No such file or directory - /usr/local/Cellar/git
iMac:Kackey.github.io hide$ brew install git
==> Downloading https://homebrew.bintray.com/bottles/git-2.3.4.yosemite.bottle.tar.gz
Already downloaded: /Library/Caches/Homebrew/git-2.3.4.yosemite.bottle.tar.gz
==> Pouring git-2.3.4.yosemite.bottle.tar.gz
==> Caveats
The OS X keychain credential helper has been installed to:
  /usr/local/bin/git-credential-osxkeychain

The "contrib" directory has been installed to:
  /usr/local/share/git-core/contrib

Bash completion has been installed to:
  /usr/local/etc/bash_completion.d

zsh completion has been installed to:
  /usr/local/share/zsh/site-functions
==> Summary
🍺  /usr/local/Cellar/git/2.3.4: 1362 files,  31M
iMac:Kackey.github.io hide$ brew install ruby-build
==> Downloading https://github.com/sstephenson/ruby-build/archive/v20150319zf.tar.gz
######################################################################## 100.0%
curl: (7) Failed to connect to codeload.github.com port 443: Operation timed out
Error: Failed to download resource "ruby-build"
Download failed: https://github.com/sstephenson/ruby-build/archive/v20150319zf.tar.gz
iMac:Kackey.github.io hide$ rbenv --version
/usr/local/Cellar/rbenv/0.4.0/libexec/rbenv---version: line 17: cd: /Users/hide/.rbenv: No such file or directory
iMac:Kackey.github.io hide$ rbenv install --list
rbenv: no such command `install'
iMac:Kackey.github.io hide$ rbenv install --list
rbenv: no such command `install'
iMac:Kackey.github.io hide$ rbenv install 2.1.3
rbenv: no such command `install'
iMac:Kackey.github.io hide$ which rbenv
/usr/local/bin/rbenv
iMac:Kackey.github.io hide$ brew install ruby-build
==> Downloading https://github.com/sstephenson/ruby-build/archive/v20150319zf.tar.gz
######################################################################## 100.0%
==> ./install.sh
🍺  /usr/local/Cellar/ruby-build/20150319zf: 154 files, 656K, built in 4 seconds
iMac:Kackey.github.io hide$ rbenv --version
/usr/local/Cellar/rbenv/0.4.0/libexec/rbenv---version: line 17: cd: /Users/hide/.rbenv: No such file or directory
iMac:Kackey.github.io hide$ brew install ruby-build
Warning: ruby-build-20150319zf already installed
iMac:Kackey.github.io hide$ brew install rbenv
Warning: rbenv-0.4.0 already installed
iMac:Kackey.github.io hide$ brew uninstall rbenv
Uninstalling /usr/local/Cellar/rbenv/0.4.0...
iMac:Kackey.github.io hide$ brew install rbenv
==> Downloading https://github.com/sstephenson/rbenv/archive/v0.4.0.tar.gz
Already downloaded: /Library/Caches/Homebrew/rbenv-0.4.0.tar.gz
==> Caveats
To use Homebrew's directories rather than ~/.rbenv add to your profile:
  export RBENV_ROOT=/usr/local/var/rbenv

To enable shims and autocompletion add to your profile:
  if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi
==> Summary
🍺  /usr/local/Cellar/rbenv/0.4.0: 31 files, 152K, built in 2 seconds
iMac:Kackey.github.io hide$ cat ~/.bash_profile
export PATH=$HOME/.nodebrew/current/bin:$PATH
export PATH="$HOME/.rbenv/bin:$PATH"
if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi
iMac:Kackey.github.io hide$ source ~/.bash_profile
iMac:Kackey.github.io hide$ rvenv --version
bash: rvenv: command not found
iMac:Kackey.github.io hide$ rbenv --version
rbenv 0.4.0
iMac:Kackey.github.io hide$ rbenv --list
rbenv: no such command `--list'
iMac:Kackey.github.io hide$ rbenv --list
rbenv: no such command `--list'
iMac:Kackey.github.io hide$ rbenv install --list
Available versions:
  1.8.6-p383
  1.8.6-p420
  1.8.7-p249
  1.8.7-p302
  1.8.7-p334
  1.8.7-p352
  1.8.7-p357
  1.8.7-p358
  1.8.7-p370
  1.8.7-p371
  1.8.7-p374
  1.8.7-p375
  1.9.1-p378
  1.9.1-p430
  1.9.2-p0
  1.9.2-p180
  1.9.2-p290
  1.9.2-p318
  1.9.2-p320
  1.9.2-p326
  1.9.2-p330
  1.9.3-dev
  1.9.3-preview1
  1.9.3-rc1
  1.9.3-p0
  1.9.3-p125
  1.9.3-p194
  1.9.3-p286
  1.9.3-p327
  1.9.3-p362
  1.9.3-p374
  1.9.3-p385
  1.9.3-p392
  1.9.3-p429
  1.9.3-p448
  1.9.3-p484
  1.9.3-p545
  1.9.3-p547
  1.9.3-p550
  1.9.3-p551
  2.0.0-dev
  2.0.0-preview1
  2.0.0-preview2
  2.0.0-rc1
  2.0.0-rc2
  2.0.0-p0
  2.0.0-p195
  2.0.0-p247
  2.0.0-p353
  2.0.0-p451
  2.0.0-p481
  2.0.0-p576
  2.0.0-p594
  2.0.0-p598
  2.0.0-p643
  2.1.0-dev
  2.1.0-preview1
  2.1.0-preview2
  2.1.0-rc1
  2.1.0
  2.1.1
  2.1.2
  2.1.3
  2.1.4
  2.1.5
  2.2.0-dev
  2.2.0-preview1
  2.2.0-preview2
  2.2.0-rc1
  2.2.0
  2.2.1
  2.3.0-dev
  jruby-1.5.6
  jruby-1.6.3
  jruby-1.6.4
  jruby-1.6.5
  jruby-1.6.5.1
  jruby-1.6.6
  jruby-1.6.7
  jruby-1.6.7.2
  jruby-1.6.8
  jruby-1.7.0-preview1
  jruby-1.7.0-preview2
  jruby-1.7.0-rc1
  jruby-1.7.0-rc2
  jruby-1.7.0
  jruby-1.7.1
  jruby-1.7.2
  jruby-1.7.3
  jruby-1.7.4
  jruby-1.7.5
  jruby-1.7.6
  jruby-1.7.7
  jruby-1.7.8
  jruby-1.7.9
  jruby-1.7.10
  jruby-1.7.11
  jruby-1.7.12
  jruby-1.7.13
  jruby-1.7.14
  jruby-1.7.15
  jruby-1.7.16
  jruby-1.7.16.1
  jruby-1.7.16.2
  jruby-1.7.17
  jruby-1.7.18
  jruby-1.7.19
  jruby-9.0.0.0-dev
  jruby-9.0.0.0+graal-dev
  jruby-9.0.0.0.pre1
  maglev-1.0.0
  maglev-1.1.0-dev
  maglev-2.0.0-dev
  mruby-dev
  mruby-1.0.0
  mruby-1.1.0
  rbx-1.2.4
  rbx-2.0.0-dev
  rbx-2.0.0-rc1
  rbx-2.0.0
  rbx-2.1.0
  rbx-2.1.1
  rbx-2.2.0
  rbx-2.2.1
  rbx-2.2.2
  rbx-2.2.3
  rbx-2.2.4
  rbx-2.2.5
  rbx-2.2.6
  rbx-2.2.7
  rbx-2.2.9
  rbx-2.2.10
  rbx-2.3.0
  rbx-2.4.0
  rbx-2.4.1
  rbx-2.5.0
  rbx-2.5.1
  rbx-2.5.2
  ree-1.8.6-2009.06
  ree-1.8.7-2009.09
  ree-1.8.7-2009.10
  ree-1.8.7-2010.01
  ree-1.8.7-2010.02
  ree-1.8.7-2011.03
  ree-1.8.7-2011.12
  ree-1.8.7-2012.01
  ree-1.8.7-2012.02
  topaz-dev
iMac:Kackey.github.io hide$ ruby -v
ruby 2.0.0p481 (2014-05-08 revision 45883) [universal.x86_64-darwin14]
iMac:Kackey.github.io hide$ rbenv install 2.2.1
Downloading ruby-2.2.1.tar.gz...
-> http://dqw8nmjcqpjn7.cloudfront.net/5a4de38068eca8919cb087d338c0c2e3d72c9382c804fb27ab746e6c7819ab28
Installing ruby-2.2.1...

Installed ruby-2.2.1 to /Users/hide/.rbenv/versions/2.2.1

iMac:Kackey.github.io hide$
iMac:Kackey.github.io hide$ rbenv global 2.2.0
rbenv: version `2.2.0' not installed
iMac:Kackey.github.io hide$ rbenv global 2.2.1
iMac:Kackey.github.io hide$ ruby -v
ruby 2.0.0p481 (2014-05-08 revision 45883) [universal.x86_64-darwin14]
iMac:Kackey.github.io hide$ rbenv install --list
Available versions:
  1.8.6-p383
  1.8.6-p420
  1.8.7-p249
  1.8.7-p302
  1.8.7-p334
  1.8.7-p352
  1.8.7-p357
  1.8.7-p358
  1.8.7-p370
  1.8.7-p371
  1.8.7-p374
  1.8.7-p375
  1.9.1-p378
  1.9.1-p430
  1.9.2-p0
  1.9.2-p180
  1.9.2-p290
  1.9.2-p318
  1.9.2-p320
  1.9.2-p326
  1.9.2-p330
  1.9.3-dev
  1.9.3-preview1
  1.9.3-rc1
  1.9.3-p0
  1.9.3-p125
  1.9.3-p194
  1.9.3-p286
  1.9.3-p327
  1.9.3-p362
  1.9.3-p374
  1.9.3-p385
  1.9.3-p392
  1.9.3-p429
  1.9.3-p448
  1.9.3-p484
  1.9.3-p545
  1.9.3-p547
  1.9.3-p550
  1.9.3-p551
  2.0.0-dev
  2.0.0-preview1
  2.0.0-preview2
  2.0.0-rc1
  2.0.0-rc2
  2.0.0-p0
  2.0.0-p195
  2.0.0-p247
  2.0.0-p353
  2.0.0-p451
  2.0.0-p481
  2.0.0-p576
  2.0.0-p594
  2.0.0-p598
  2.0.0-p643
  2.1.0-dev
  2.1.0-preview1
  2.1.0-preview2
  2.1.0-rc1
  2.1.0
  2.1.1
  2.1.2
  2.1.3
  2.1.4
  2.1.5
  2.2.0-dev
  2.2.0-preview1
  2.2.0-preview2
  2.2.0-rc1
  2.2.0
  2.2.1
  2.3.0-dev
  jruby-1.5.6
  jruby-1.6.3
  jruby-1.6.4
  jruby-1.6.5
  jruby-1.6.5.1
  jruby-1.6.6
  jruby-1.6.7
  jruby-1.6.7.2
  jruby-1.6.8
  jruby-1.7.0-preview1
  jruby-1.7.0-preview2
  jruby-1.7.0-rc1
  jruby-1.7.0-rc2
  jruby-1.7.0
  jruby-1.7.1
  jruby-1.7.2
  jruby-1.7.3
  jruby-1.7.4
  jruby-1.7.5
  jruby-1.7.6
  jruby-1.7.7
  jruby-1.7.8
  jruby-1.7.9
  jruby-1.7.10
  jruby-1.7.11
  jruby-1.7.12
  jruby-1.7.13
  jruby-1.7.14
  jruby-1.7.15
  jruby-1.7.16
  jruby-1.7.16.1
  jruby-1.7.16.2
  jruby-1.7.17
  jruby-1.7.18
  jruby-1.7.19
  jruby-9.0.0.0-dev
  jruby-9.0.0.0+graal-dev
  jruby-9.0.0.0.pre1
  maglev-1.0.0
  maglev-1.1.0-dev
  maglev-2.0.0-dev
  mruby-dev
  mruby-1.0.0
  mruby-1.1.0
  rbx-1.2.4
  rbx-2.0.0-dev
  rbx-2.0.0-rc1
  rbx-2.0.0
  rbx-2.1.0
  rbx-2.1.1
  rbx-2.2.0
  rbx-2.2.1
  rbx-2.2.2
  rbx-2.2.3
  rbx-2.2.4
  rbx-2.2.5
  rbx-2.2.6
  rbx-2.2.7
  rbx-2.2.9
  rbx-2.2.10
  rbx-2.3.0
  rbx-2.4.0
  rbx-2.4.1
  rbx-2.5.0
  rbx-2.5.1
  rbx-2.5.2
  ree-1.8.6-2009.06
  ree-1.8.7-2009.09
  ree-1.8.7-2009.10
  ree-1.8.7-2010.01
  ree-1.8.7-2010.02
  ree-1.8.7-2011.03
  ree-1.8.7-2011.12
  ree-1.8.7-2012.01
  ree-1.8.7-2012.02
  topaz-dev
iMac:Kackey.github.io hide$ rbenv rehash
iMac:Kackey.github.io hide$ ruby -v
ruby 2.2.1p85 (2015-02-26 revision 49769) [x86_64-darwin14]
iMac:Kackey.github.io hide$ rbenv versions
  system
* 2.2.1 (set by /Users/hide/.rbenv/version)
iMac:Kackey.github.io hide$ ruby -v
ruby 2.2.1p85 (2015-02-26 revision 49769) [x86_64-darwin14]
iMac:Kackey.github.io hide$ gem install bundler
Fetching: bundler-1.9.1.gem (100%)
Successfully installed bundler-1.9.1
Parsing documentation for bundler-1.9.1
Installing ri documentation for bundler-1.9.1
Done installing documentation for bundler after 4 seconds
1 gem installed
iMac:Kackey.github.io hide$ bundle install
bash: bundle: command not found
iMac:Kackey.github.io hide$ pwd
/Users/hide/Dropbox/git-repo/Kackey.github.io
iMac:Kackey.github.io hide$ bundle install
bash: bundle: command not found
iMac:Kackey.github.io hide$ ls
Gemfile         Gemfile.lock    LICENSE         README.md       index.html
iMac:Kackey.github.io hide$
iMac:Kackey.github.io hide$
iMac:Kackey.github.io hide$ bundle install
bash: bundle: command not found
iMac:Kackey.github.io hide$ ruby -v
ruby 2.2.1p85 (2015-02-26 revision 49769) [x86_64-darwin14]
iMac:Kackey.github.io hide$ which bundle
iMac:Kackey.github.io hide$ rbenv rehash
iMac:Kackey.github.io hide$ bundle install
Your Gemfile has no gem server sources. If you need gems that are not already on your machine, add a line like this to your Gemfile:
source 'https://rubygems.org'
Could not find gem 'github-pages (>= 0) ruby' in the gems available on this machine.
iMac:Kackey.github.io hide$ bundle install
Fetching gem metadata from https://rubygems.org/..........
Fetching version metadata from https://rubygems.org/..
Resolving dependencies...
Installing RedCloth 4.2.9
Installing i18n 0.7.0
Installing json 1.8.2
Installing minitest 5.5.1
Installing thread_safe 0.3.5
Installing tzinfo 1.2.2
Installing activesupport 4.2.1
Installing blankslate 2.1.2.4
Installing hitimes 1.2.2
Installing timers 4.0.1
Installing celluloid 0.16.0
Installing fast-stemmer 1.0.2
Installing classifier-reborn 2.0.3
Installing coffee-script-source 1.9.1
Installing execjs 2.4.0
Installing coffee-script 2.3.0
Installing colorator 0.1
Installing ffi 1.9.8
Installing gemoji 2.1.0
Installing net-dns 0.8.0
Installing public_suffix 1.5.0
Installing github-pages-health-check 0.2.2
Installing jekyll-coffeescript 1.0.1
Installing jekyll-gist 1.2.1
Installing jekyll-paginate 1.1.0
Installing sass 3.4.13
Installing jekyll-sass-converter 1.2.0
Installing rb-fsevent 0.9.4
Installing rb-inotify 0.9.5
Installing listen 2.10.0
Installing jekyll-watch 1.2.1
Installing kramdown 1.5.0
Installing liquid 2.6.1
Installing mercenary 0.3.5
Installing posix-spawn 0.3.10
Installing yajl-ruby 1.2.1
Installing pygments.rb 0.6.1
Installing redcarpet 3.1.2
Installing safe_yaml 1.0.4
Installing parslet 1.5.0
Installing toml 0.1.2
Installing jekyll 2.4.0
Installing mini_portile 0.6.2

Gem::Ext::BuildError: ERROR: Failed to build gem native extension.

    /Users/hide/.rbenv/versions/2.2.1/bin/ruby -r ./siteconf20150330-32723-18py1e0.rb extconf.rb
checking if the C compiler accepts ... yes
checking if the C compiler accepts -Wno-error=unused-command-line-argument-hard-error-in-future... no
Building nokogiri using packaged libraries.
-----
The file "/usr/include/iconv.h" is missing in your build environment,
which means you haven't installed Xcode Command Line Tools properly.

To install Command Line Tools, try running `xcode-select --install` on
terminal and follow the instructions.  If it fails, open Xcode.app,
select from the menu "Xcode" - "Open Developer Tool" - "More Developer
Tools" to open the developer site, download the installer for your OS
version and run it.
-----
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of necessary
libraries and/or headers.  Check the mkmf.log file for more details.  You may
need configuration options.

Provided configuration options:
        --with-opt-dir
        --without-opt-dir
        --with-opt-include
        --without-opt-include=${opt-dir}/include
        --with-opt-lib
        --without-opt-lib=${opt-dir}/lib
        --with-make-prog
        --without-make-prog
        --srcdir=.
        --curdir
        --ruby=/Users/hide/.rbenv/versions/2.2.1/bin/$(RUBY_BASE_NAME)
        --help
        --clean
        --use-system-libraries
        --enable-static
        --disable-static
        --with-zlib-dir
        --without-zlib-dir
        --with-zlib-include
        --without-zlib-include=${zlib-dir}/include
        --with-zlib-lib
        --without-zlib-lib=${zlib-dir}/lib
        --enable-cross-build
        --disable-cross-build

extconf failed, exit code 1

Gem files will remain installed in /Users/hide/.rbenv/versions/2.2.1/lib/ruby/gems/2.2.0/gems/nokogiri-1.6.6.2 for inspection.
Results logged to /Users/hide/.rbenv/versions/2.2.1/lib/ruby/gems/2.2.0/extensions/x86_64-darwin-14/2.2.0-static/nokogiri-1.6.6.2/gem_make.out
An error occurred while installing nokogiri (1.6.6.2), and Bundler cannot continue.
Make sure that `gem install nokogiri -v '1.6.6.2'` succeeds before bundling.
iMac:Kackey.github.io hide$ gem install nokogiri -v '1.6.6.2'
Building native extensions.  This could take a while...
ERROR:  Error installing nokogiri:
        ERROR: Failed to build gem native extension.

    /Users/hide/.rbenv/versions/2.2.1/bin/ruby -r ./siteconf20150330-36858-12p4tvo.rb extconf.rb
checking if the C compiler accepts ... yes
checking if the C compiler accepts -Wno-error=unused-command-line-argument-hard-error-in-future... no
Building nokogiri using packaged libraries.
-----
The file "/usr/include/iconv.h" is missing in your build environment,
which means you haven't installed Xcode Command Line Tools properly.

To install Command Line Tools, try running `xcode-select --install` on
terminal and follow the instructions.  If it fails, open Xcode.app,
select from the menu "Xcode" - "Open Developer Tool" - "More Developer
Tools" to open the developer site, download the installer for your OS
version and run it.
-----
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of necessary
libraries and/or headers.  Check the mkmf.log file for more details.  You may
need configuration options.

Provided configuration options:
        --with-opt-dir
        --without-opt-dir
        --with-opt-include
        --without-opt-include=${opt-dir}/include
        --with-opt-lib
        --without-opt-lib=${opt-dir}/lib
        --with-make-prog
        --without-make-prog
        --srcdir=.
        --curdir
        --ruby=/Users/hide/.rbenv/versions/2.2.1/bin/$(RUBY_BASE_NAME)
        --help
        --clean
        --use-system-libraries
        --enable-static
        --disable-static
        --with-zlib-dir
        --without-zlib-dir
        --with-zlib-include
        --without-zlib-include=${zlib-dir}/include
        --with-zlib-lib
        --without-zlib-lib=${zlib-dir}/lib
        --enable-cross-build
        --disable-cross-build

extconf failed, exit code 1

Gem files will remain installed in /Users/hide/.rbenv/versions/2.2.1/lib/ruby/gems/2.2.0/gems/nokogiri-1.6.6.2 for inspection.
Results logged to /Users/hide/.rbenv/versions/2.2.1/lib/ruby/gems/2.2.0/extensions/x86_64-darwin-14/2.2.0-static/nokogiri-1.6.6.2/gem_make.out
iMac:Kackey.github.io hide$


iMac:Kackey.github.io hide$ bundle install
Fetching gem metadata from https://rubygems.org/..........
Fetching version metadata from https://rubygems.org/..
Resolving dependencies...
Using RedCloth 4.2.9
Using i18n 0.7.0
Using json 1.8.2
Using minitest 5.5.1
Using thread_safe 0.3.5
Using tzinfo 1.2.2
Using activesupport 4.2.1
Using blankslate 2.1.2.4
Using hitimes 1.2.2
Using timers 4.0.1
Using celluloid 0.16.0
Using fast-stemmer 1.0.2
Using classifier-reborn 2.0.3
Using coffee-script-source 1.9.1
Using execjs 2.4.0
Using coffee-script 2.3.0
Using colorator 0.1
Using ffi 1.9.8
Using gemoji 2.1.0
Using net-dns 0.8.0
Using public_suffix 1.5.0
Using github-pages-health-check 0.2.2
Using jekyll-coffeescript 1.0.1
Using jekyll-gist 1.2.1
Using jekyll-paginate 1.1.0
Using sass 3.4.13
Using jekyll-sass-converter 1.2.0
Using rb-fsevent 0.9.4
Using rb-inotify 0.9.5
Using listen 2.10.0
Using jekyll-watch 1.2.1
Using kramdown 1.5.0
Using liquid 2.6.1
Using mercenary 0.3.5
Using posix-spawn 0.3.10
Using yajl-ruby 1.2.1
Using pygments.rb 0.6.1
Using redcarpet 3.1.2
Using safe_yaml 1.0.4
Using parslet 1.5.0
Using toml 0.1.2
Using jekyll 2.4.0
Using mini_portile 0.6.2
Installing nokogiri 1.6.6.2
Installing html-pipeline 1.9.0
Installing jekyll-mentions 0.2.1
Installing jekyll-redirect-from 0.6.2
Installing jekyll-sitemap 0.6.3
Installing jemoji 0.4.0
Installing maruku 0.7.0
Installing rdiscount 2.1.7
Installing terminal-table 1.4.5
Installing github-pages 33
Using bundler 1.9.1
Bundle complete! 1 Gemfile dependency, 54 gems now installed.
Use `bundle show [gemname]` to see where a bundled gem is installed.
Post-install message from html-pipeline:
-------------------------------------------------
Thank you for installing html-pipeline!
You must bundle Filter gem dependencies.
See html-pipeline README.md for more details.
https://github.com/jch/html-pipeline#dependencies
-------------------------------------------------

```
