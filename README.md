# git-realm

Git Realm - A different approach to branch naming.\
Efficient way to work with git branches and getting things done quickly.

## Requirements

git-realm uses small word dictionary from `libcrack2` package for getting two random words for every new realm you create.

```bash
# / Debian based systems (Debian, Ubuntu, Linux Mint, etc.)
~$ sudo apt-get install libcrack2
# / openSUSE
~$ sudo zypper install libcrack2
```

## Installation

It is up on you. For a inspiration there are two methods of installing git-realm:

### System-wide

Best choice for multi-user Linux computer or users that do not care a lot where things goes.

2 lines. That's all.

```bash
git clone https://github.com/dehahost/git-realm.git       # Hold on and do not cd into the repo!
sudo ln -s -t /usr/local/bin/ ${PWD}/git-realm/git-realm  # Create symlink in /usr/local/bin/
```

Profit!

### One user only

Good option for a user on a multi-user system that do not have a root access. Or for ones that belives user binaries and scripts should stay in user's home folder.

3 lines. And some extra steps.

```bash
git clone https://github.com/dehahost/git-realm.git    # Hold on and do not cd into the repo!
mkdir ~/bin/                                           # Create "homebin"
ln -s -t ~/bin/ ${PWD}/git-realm/git-realm             # Symlink git-realm in
```

Put following line into shell environment file like `~/.bashrc` or `~/.profile`. It will insert "homebin" into PATH envvar and make `git-realm` available when you log in. Every time.
You can skip this and next step if you already have this configured.

```bash
( echo "$PATH" | grep "$HOME/bin" 2>&1 >/dev/null ) && [ -d "$HOME/bin" ] && export PATH="$PATH:$HOME/bin"
```

Do not forget to _re-source_ your shell like so ...

```bash
reset && source ~/.bashrc
```

Profit!

## Updating

It is really simple. Inside clonned git-realm repo execute ...

```bash
git fetch && git pull
```

## Usage

Create new realm:

```bash
~/git/super-soft@master$ git realm enter
Entering a new realm called 'citrus-narrative'...
Switched to a new branch 'realm-citrus-narrative'
~/git/super-soft@realm-citrus-narrative$
```

Beware, git-realm create new realms nested by default. If you don't want that, there is a `--master` for it:

```bash
~/git/super-soft@realm-citrus-narrative$ git realm enter --master
Switching you to the master branch...
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering a new realm called "dilettante-bequeathed"...
Switched to a new branch 'realm-dilettante-bequeathed'
~/git/super-soft@realm-dilettante-bequeathed$
```

You can also specify what you are up to in a new realm:

```bash
~/git/super-soft@realm-citrus-narrative$ git realm enter fix-bug3000
Creating a new realm called 'fix-bug3000'...
Switched to a new branch 'realm-fix-bug3000'
~/git/super-soft@realm-fix-bug3000$
```

You can switch between realms any time:

```bash
~/git/super-soft@realm-citrus-narrative$ git realm enter citrus-narrative
Entering realm called 'citrus-narrative'...
Switched to branch 'realm-citrus-narrative'
~/git/super-soft@realm-citrus-narrative$
```

And rename currently used realm:

```bash
~/git/super-soft@realm-citrus-narrative$ git realm reword memory-leaks
~/git/super-soft@realm-memory-leaks$
```

Leave your realm and get focused on the other part in your repo:

```bash
~/git/super-soft@realm-memory-leaks$ git realm leave
Leaving 'memory-leaks' realm...
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
~/git/super-soft@master$
```

You can easily dispose your realm and everything with it:
_Think twice before doing it!_

```bash
~/git/super-soft@realm-memory-leaks$ git realm dispose
Disposing current realm called 'memory-leaks'...
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Deleted branch realm-memory-leaks (was 2c31ec3).
~/git/super-soft@master$
```

Every realm can be listed out for better orientation:

```bash
~/git/super-soft@master$ git realm list
  doomsday-clock
  memory-leaks
~/git/super-soft@master$
```

## Configure

You can configure git-realm with Git config:

- `realm.separator` _(default: -)_ Separator character between _"realm"_ and realm name - ie. "realm-routine-stray" or "realm/gastro-tour"
- `realm.common-branch` _(default: master)_ Common Git branch - could be _main_, some prefers _master_.

## Planned funcionalities

- __Simple__:
  - [x] Ability to enter already existing realms by typing something like `git realm enter [realm-name]` [^1]
  - [x] Reword current realm - generated or typed - `git realm reword [realm-name]`
  - [x] Configuration support
- __Advanced ones__:
  - [ ] Excerpts (short notes) to a realm and view them by a command (command design `git realm [<info/excerpt/note/sign> <show|set|scrap>]`) [^2]
    - [ ] Realm list will show that excerpts
  - [ ] ~~Notify about new version (probably cURL will be used for this)~~ [^3]

[^1]: When implementing this nice feature, another was added: Ability to choose custom name for a new realm.
[^2]: Could be achieved with `gitrealm-notes` file in `.git` dir. Only downside of this is impossibility to sync it, which I see as a minor problem rn.
[^3]: This have to be non-disruptive feature, because I don't want my script to check and notify about a new version every time. So sub-command like `version-check` is the preffered way to go...

## Dependant commands

- bash _(based upon)_
- git _(manipulated with)_
- coreutils - cat, shuf
- grep
- sed
