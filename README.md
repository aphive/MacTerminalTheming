# Making the Mac Terminal easy to look at and use.
This is just my personal setup, feel free to use or add to it.

### Give thanks where it's due
Thanks to
* [lysyi3m](https://github.com/lysyi3m) for the terminal theme.
* [jakwings](https://github.com/jakwings) for the vim theme.

## What's included
* colors/moody.vim  - theme for vim, called from .vimrc
* darkside.terminal - A nice theme for terminal

## How to configure things
First you will need to do is either clone or download this repo to your computer. If you download it, you will need to unzip the files.

Once you have the files do the following:

### Setup your Terminal Profile
You can do this two ways:

The easy way is to just double click `darkside.terminal` and your terminal will load with the theme already active, you just need to make sure it's set as the default. Then go to the `General` tab and set `Darkside` as the profile to load on startup.

The other way you can do it is to:
* Open Terminal
* Click `Terminal` -> `Preferences`
* Click the `Profiles` tab
* Click on the `gear` icon in the bottom left menu then click `Import`
* Browse to the location of the files you just downloaded and select `darkside.terminal`
* Set as `Default`
* Under the `Text` tab, activate the `Use bright colors for bold text` option
* Click on the `General` tab and set `Darkside` as the profile to load on startup.

### Vim theme
While your terminal is still open:

* Create `.vim`:

```
mkdir ~/.vim
```

* cd into the `MacTerminalTheming` directory (where ever it's currently located)
* Run `ls -a` and you should see the following items:

```
./  ../ .git/   Darkside.terminal*  README.md   colors/
```

* Run `mv colors ~/.vim` to move things to their right place.
* Run `vi ~/.vimrc` and enter the following:

```
filetype plugin indent on
syntax on
set t_Co=256
colorscheme moody
```

## Things to add to your Bash Profile
In `Terminal` edit your `.bash_profile` file

```
vi ~/.bash_profile
```

You can use any or all of the following:

```
# Set default blocksize for ls, df, du
export BLOCKSIZE=1k

# extract:  Extract most know archives with one command
extract () {
        if [ -f $1 ] ; then
                case $1 in
                        *.tar.bz2)   tar xjf $1     ;;
                        *.tar.gz)    tar xzf $1     ;;
                        *.bz2)       bunzip2 $1     ;;
                        *.rar)       unrar e $1     ;;
                        *.gz)        gunzip $1      ;;
                        *.tar)       tar xf $1      ;;
                        *.tbz2)      tar xjf $1     ;;
                        *.tgz)       tar xzf $1     ;;
                        *.zip)       unzip $1       ;;
                        *.Z)         uncompress $1  ;;
                        *.7z)        7z x $1        ;;
                        *)     echo "'$1' cannot be extracted via extract()" ;;
                esac
        else
                echo "'$1' is not a valid file"
        fi
}

# Networking
alias myip='dig +short myip.opendns.com @resolver1.opendns.com' # myip:         Public facing IP Address
alias netCons='lsof -i'                                         # netCons:      Show all open TCP/IP sockets
alias flushDNS='dscacheutil -flushcache'                        # flushDNS:     Flush out the DNS Cache
alias lsock='sudo /usr/sbin/lsof -i -P'                         # lsock:        Display open sockets
alias lsockU='sudo /usr/sbin/lsof -nP | grep UDP'               # lsockU:       Display only open UDP sockets
alias lsockT='sudo /usr/sbin/lsof -nP | grep TCP'               # lsockT:       Display only open TCP sockets
alias ipInfo0='ipconfig getpacket en0'                          # ipInfo0:      Get info on connections for en0
alias ipInfo1='ipconfig getpacket en1'                          # ipInfo1:      Get info on connections for en1
alias openPorts='sudo lsof -i | grep LISTEN'                    # openPorts:    All listening connections

# Dealing with files
alias cleanupDS="find . -type f -name '*.DS_Store' -ls -delete" # cleanupDS:    Recursively delete .DS_Store files

# Add color to terminal
export PS1="\[\033[36m\]\u\[\033[m\]@\[\033[32m\]\h:\[\033[33;1m\]\w\[\033[m\]\$ "
export CLICOLOR=1
export LSCOLORS=ExFxBxDxCxegedabagacad

# Better prompt
alias ls='ls -GFh'
```
The last line changes your default prompt from `computername:~ username$` to `username@computername:~$`

If you use brew here is a nice little entry for your `.bash_profile`

```
# Brew Stuffs
alias brewup='brew update; brew upgrade; brew prune; brew cleanup; brew doctor'
```
## Extras
I also setup my `/etc/motd` (Message of the Day) to show my my aliases at login just in case I need any:

* edit `/etc/motd`

```
vi vi /etc/motd
```

Here you can add anything you want for a message, you can even leave a warning in case someone starts up Terminal. For what I use it, just paste in the following:

```
Useful Aliases

    extract:    Extract most know archives with one command
       myip:    Public facing IP Address
    netCons:    Show all open TCP/IP sockets
   flushDNS:    Flush out the DNS Cache
      lsock:    Display open sockets
     lsockU:    Display only open UDP sockets
     lsockT:    Display only open TCP sockets
    ipInfo0:    Get info on connections for en0 (WiFi)
    ipInfo1:    Get info on connections for en1 (Lan)
  openPorts:    All listening connections
  cleanupDS:    Recursively delete .DS_Store files
     brewup:    Keep Brew up-to-date and clean
```

Now every time you start Terminal, you will get that as a message.

## Done
Restart your terminal and things should all be nice, pretty and useful.
