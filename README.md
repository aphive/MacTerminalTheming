# Making the Mac Terminal easy to look at and use.
This is just my personal setup, feel free to use or add to it.

## What's included
* .bash_profile     - things to use from the command line and to make bash look pretty.
* .vimrc            - tweaks and theming for vi editor
* moody.vim		    - theme for vim, called from .vimrc
* darkside.terminal - A nice theme for terminal

## How to configure things
First you will need to either clone or download this repo to your computer. If you download it, you will need to unzip the files.

Once you have the files do the following:

### Setup your Terminal Profile
You can do this two ways, the easy way is to just double click `darkside.terminal` and your terminal will load with the theme already active, you just need to make sure it's set as the default. Then go to the `General` tab and set `Darkside` as the profile to load on startup.

The other way you can do it is to:
* Open terminal
* Click `Terminal` -> `Preferences`
* Click the `Profiles` tab
* Click on the `gear` icon in the bottom left menu then click `Import`
* Browse to the location of the files you just downloaded and select `darkside.terminal`
* Set as default
* Under Text, activate the `Use bright colors for bold text` option
* Click on the `General` tab and set `Darkside` as the profile to load on startup.

### Vim theme
First you want to move the entire `.vim/colors` directory into your user directory, while your terminal is still open:

* cd into the `MacTerminalTheming` directory, don't go into the actual `.vim` directory
* Run `ls -a` and you should see the following items:
```
./   ../   .git/ .vim/   Darkside.terminal* README.md
```
* Run `mv .vim ~/` to move things to their right place.
* Run `vi ~/.vimrc` and enter the following:
```
filetype plugin indent on
syntax on
set t_Co=256
colorscheme moody
```
