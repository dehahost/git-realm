# git-realm

Git Realm - A different approach to branch naming.\
If you do not want to care about naming a branch for a hot-fix or a new feature without a delay, simply enter a new realm and get things done.

## Requirements

git-realm uses a small word dictionary from `libcrack2` package for generating two random words for every new realm you create.\
```bash
# / Debian based systems (Debian, Ubuntu, Linux Mint, etc.)
~$ sudo apt-get install libcrack2
# / openSUSE
~$ sudo zypper install libcrack2
```

## Installation

Install it as you'd like. It's on you. However there are two ways of installing git-realm:

### Want it easy? And ASAP?
Best choice for multi-user Linux computer or users that don't care a lot where things goes.

2 lines. That's all.
```bash
git clone https://github.com/dehahost/git-realm.git       # Hold on and do not cd into the repo!
sudo ln -s -t /usr/local/bin/ ${PWD}/git-realm/git-realm  # Create symlink in /usr/local/bin/
```

### Only for me!
Good option for user on a multi-user system that don't have a root access. Or for ones that belives user binaries and scripts should stay in user's home folder.

3 lines. And some extra steps.
```bash
git clone https://github.com/dehahost/git-realm.git    # Hold on and do not cd into the repo!
mkdir ~/bin/                                           # Create "homebin"
ln -s -t ~/bin/ ${PWD}/git-realm/git-realm             # Symlink git-realm in
```

Put following line into your `.bashrc`. It will insert "homebin" into PATH envvar and make `git-realm` available when you log in. Every time.
You can skip this and next step if you already have this configured.
```bash
( echo "$PATH" | grep "$HOME/bin" 2>&1 >/dev/null ) && [ -d "$HOME/bin" ] && export PATH="$PATH:$HOME/bin"
```

Don't forget to *re-source* Bash environment:
```bash
source ~/.bashrc
```

Enjoy it!

## Updating

It's really simple. Inside clonned git-realm repo execute:
```bash
git fetch && git pull
```

## Usage

Create new realm:
```bash
~/git/super-soft@master$ git realm enter
Entering a new realm called 'citrus-narrative'...
Switched to a new branch 'realm-citrus-narrative'
~/git/super-soft@realm-citrus-narrative$ # Do your work... :]
```

Beware, git-realm create new realms nested. If you don't want that, there is a `--switch`:
```bash
~/git/super-soft@realm-citrus-narrative$ git realm enter --switch
Switching you to the master branch...
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering a new realm called "dilettante-bequeathed"...
Switched to a new branch 'realm-dilettante-bequeathed'
~/git/super-soft@realm-dilettante-bequeathed$ # Brand new one...
```

You can leave your realm and get focused on other part of a repo:
```bash
~/git/super-soft@realm-citrus-narrative$ git realm leave
Leaving 'citrus-narrative' realm...
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
~/git/super-soft@master$ # Here we go... :]
```

Realms and everything inside it can be erased without a trace:
```bash
~/git/super-soft@realm-citrus-narrative$ git realm dispose
Disposing current realm called 'citrus-narrative'...
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Deleted branch realm-citrus-narrative (was 2c31ec3).
~/git/super-soft@master$ # ...gone!
```

Every realm can be listed out for better orientation:
```bash
~/git/super-soft@master$ git realm list
  doomsday-merciless
~/git/super-soft@master$
```

## Planned funcionalities

- [ ] Ability to enter already existing realms by typing something like `git realm enter ballistic-future`
- [ ] Possibility to add excerpts (short notes) to a realm and view them by a command (command design `git realm [<info/excerpt/note/sign> <show|set|scrap>]`)
- [ ] Realm list will show that excerpts

_Side note: Excerpst can be pretty hard to implement as they require some kind of storage and sync - you really want that be everywhere else you work, right?. So there is a possibility I later drop those two last functionalities from the list._
