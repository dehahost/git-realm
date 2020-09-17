# git-realm

Git Realm - A different approach to branch naming.\
If you do not want to care about naming a branch for a fix or a new feature, simply enter a new realm and get things done.

## Requirements

git-realm uses a small word dictionary from `libcrack2` package for generating two random words for every new realm you create.\
Here are some installation one-liners:
```bash
# / Debian based systems (Debian, Ubuntu, Linux Mint, etc.)
~$ sudo apt-get install libcrack2
# / openSUSE
~$ sudo zypper install libcrack2
```

## Installation

Clone it somewhere:
```bash
~/git$ git clone https://github.com/dehahost/git-realm.git
```

Do not enter cloned repo. Link git-realm from it.
```
#  / ...For system-wide usage
~/git$ sudo ln -s -t /usr/local/sbin/ ${PWD}/git-realm/git-realm

#  / ...Just for you (do not do 1st, 3rd and 4th if you have it already)
~/git$ mkdir ~/bin/                                                    # Create "homebin"
~/git$ sudo ln -s -t ~/bin/ ${PWD}/git-realm/git-realm                 # Symlink git-realm into ~/bin
~/git$ echo -e "\n# Homebin\nPATH=${PATH}:${HOME}/bin\n" >>~/.bashrc   # Add ~/bin into PATH var
~/git$ . ~/.bashrc                                                     # Load .bashrc
```

Enjoy it!

## Updating

As you've _installed_ git-realm using symlink, receiving updateds is a matter of the moment:
```bash
~/git/git-realm$ git fetch && git pull
```

## Usage

It's simple. To create a new realm for quick fixing or brand new feature development, enter a new realm:
```bash
~/git/super-soft@master$ git realm enter
Entering a new realm called 'citrus-narrative'...
Switched to a new branch 'realm-citrus-narrative'
~/git/super-soft@realm-citrus-narrative$ # Do your work... :]
```

You can enter a new nested realm in the existing one. This could be useful for better work organization or for _something else_.\
To avoid nested realms, `--switch` argument can be used. Add it at the end of the enter command. The master branch will be checked out just right before entering a new realm:
```bash
~/git/super-soft@realm-citrus-narrative$ git realm enter --switch
Switching you to the master branch...
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering a new realm called "dilettante-bequeathed"...
Switched to a new branch 'realm-dilettante-bequeathed'
~/git/super-soft@realm-dilettante-bequeathed$ # Brand new one...
```

Want to switch back to master? Leave a realm:
```bash
~/git/super-soft@realm-citrus-narrative$ git realm leave
Leaving 'citrus-narrative' realm...
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
~/git/super-soft@master$ # Here we go... :]
```

If you are not satisfied with your work and you are decided to give it up, dispose a realm with everithing in it:
```bash
~/git/super-soft@realm-citrus-narrative$ git realm dispose
Disposing current realm called 'citrus-narrative'...
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Deleted branch realm-citrus-narrative (was 2c31ec3).
~/git/super-soft@master$ # ...gone!
```

Exising realms can be listed to stay properly organized:
```bash
~/git/super-soft@master$ git realm list
  doomsday-merciless
~/git/super-soft@master$
```

## Planned funcionalities

- [ ] Ability to enter already existing realms by typing something like `git realm enter ballistic-future`
- [ ] Possibility to add excerpts (short notes) to a realm and view them by a command (command design `git realm [<info/excerpt/note/sign> <show|set|scrap>]`)
- [ ] Realm list will show that excerpts
