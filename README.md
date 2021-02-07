# git-realm

Git Realm - A different approach to branch naming.\
If you do not want to care about naming a branch for a hot-fix or a new feature without a delay, simply enter a new realm and get things done.

## Requirements

git-realm uses a small word dictionary from `libcrack2` package for generating two random words for every new realm you create.

```bash
# / Debian based systems (Debian, Ubuntu, Linux Mint, etc.)
~$ sudo apt-get install libcrack2
# / openSUSE
~$ sudo zypper install libcrack2
```

## Installation

Install it as you'd like. It's on you. However there are two ways of installing git-realm:

### System-wide

Best choice for multi-user Linux computer or users that don't care a lot where things goes.

2 lines. That's all.

```bash
git clone https://github.com/dehahost/git-realm.git       # Hold on and do not cd into the repo!
sudo ln -s -t /usr/local/bin/ ${PWD}/git-realm/git-realm  # Create symlink in /usr/local/bin/
```

### One user only

Good option for user on a multi-user system that don't have a root access. Or for ones that belives user binaries and scripts should stay in user's home folder.

3 lines. And some extra steps.

```bash
git clone https://github.com/dehahost/git-realm.git    # Hold on and do not cd into the repo!
mkdir ~/bin/                                           # Create "homebin"
ln -s -t ~/bin/ ${PWD}/git-realm/git-realm             # Symlink git-realm in
```

Put following line into shell environment file like `.bashrc` or `.profile`. It will insert "homebin" into PATH envvar and make `git-realm` available when you log in. Every time.
You can skip this and next step if you already have this configured.

```bash
( echo "$PATH" | grep "$HOME/bin" 2>&1 >/dev/null ) && [ -d "$HOME/bin" ] && export PATH="$PATH:$HOME/bin"
```

Don't forget to *re-source* your shell. Mine is Bash:

```bash
reset && source ~/.bashrc
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
~/git/super-soft@realm-citrus-narrative$ git realm enter trusty-regex
Creating a new realm called 'trusty-regex'...
Switched to a new branch 'realm-trusty-regex'
~/git/super-soft@realm-trusty-regex$
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
~/git/super-soft@realm-citrus-narrative$ git realm reword fixed-sla
~/git/super-soft@realm-fixed-sla$
```

Leave your realm and get focused on the other part in your repo:

```bash
~/git/super-soft@realm-fixed-sla$ git realm leave
Leaving 'fixed-sla' realm...
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
~/git/super-soft@master$
```

You can easily dispose your realm and everything with it:
_Think twice before doing it!_

```bash
~/git/super-soft@realm-fixed-sla$ git realm dispose
Disposing current realm called 'fixed-sla'...
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Deleted branch realm-fixed-sla (was 2c31ec3).
~/git/super-soft@master$
```

Every realm can be listed out for better orientation:

```bash
~/git/super-soft@master$ git realm list
  doomsday-merciless
  trusty-regex
~/git/super-soft@master$
```

## Planned funcionalities

- __Simple__:
  - [x] Ability to enter already existing realms by typing something like `git realm enter [realm-name]` [^1]
  - [x] Reword current realm - generated or typed - `git realm reword [realm-name]`
- __Advanced ones__:
  - [ ] Excerpts (short notes) to a realm and view them by a command (command design `git realm [<info/excerpt/note/sign> <show|set|scrap>]`) [^2]
    - [ ] Realm list will show that excerpts
  - [ ] Notify about new version (probably cURL will be used for this) [^3]

[^1]: When implementing this nice feature, another has been added: Ability to choose custom name for a new realm.
[^2]: Creating additional file like `.gitrealm-notes` in repo root will be required to achieve this functionality.
[^3]: This have to be non-disruptive feature, because I don't want my script to check and notify about a new version every execution time. So sub-command like `version-check` is the preffered way to go...
