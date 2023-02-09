# git-realm

git-realm is Git plugin written mainly for fast and/or creative development.

## Requirements

Install dictionary package `libcrack2`.

```bash
# / Debian based systems (Debian, Ubuntu, Linux Mint, etc.)
~$ sudo apt-get install libcrack2
# / openSUSE
~$ sudo zypper install libcrack2
```

## Installation

**1**/ Clone this repo into your usual location.\
**2**/ Symlink git-realm to `/usr/local/bin/` (or a different directory in `$PATH` env. variable)\
**3**/ Try `git realm help` and if it works, profit!

## Configuration

You can configure git-realm with Git config:

- `realm.separator` _(default: -)_ Separator character between _"realm"_ and realm name - ie. "realm-decent-stray" or "realm/gastro-tour"
- `realm.common-branch` _(default: master)_ Common Git branch - could be _main_, some prefers _master_, others _production_.

## Usage

### Lising

```bash
~/git/super-soft@master$ git realm list
  doomsday-clock
  memory-leaks
~/git/super-soft@master$
```

### Entering realms

**1**/ The easy way

```bash
~/git/super-soft@master$ git realm enter
Entering a new realm called 'citrus-narrative'...
Switched to a new branch 'realm-citrus-narrative'
~/git/super-soft@realm-citrus-narrative$
```

**2**/ From common branch

```bash
~/git/super-soft@realm-citrus-narrative$ git realm enter --master
Switching you to the master branch...
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Entering a new realm called "dilettante-bequeathed"...
Switched to a new branch 'realm-dilettante-bequeathed'
~/git/super-soft@realm-dilettante-bequeathed$
```

**3**/ With a custom name

```bash
~/git/super-soft@realm-citrus-narrative$ git realm enter fix-bug3000
Creating a new realm called 'fix-bug3000'...
Switched to a new branch 'realm-fix-bug3000'
~/git/super-soft@realm-fix-bug3000$
```

### Rewording enterd realm

**1**/ New random name

```bash
~/git/super-soft@realm-citrus-narrative$ git realm reword
~/git/super-soft@realm-naiive-ninja$
```

**2**/ Desired name

```bash
~/git/super-soft@realm-naiive-ninja$ git realm reword memory-leaks
~/git/super-soft@realm-memory-leaks$
```

### Leaving realms

```bash
~/git/super-soft@realm-memory-leaks$ git realm leave
Leaving 'memory-leaks' realm...
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
~/git/super-soft@master$
```

### Disposing realms

```bash
~/git/super-soft@realm-memory-leaks$ git realm dispose
Disposing current realm called 'memory-leaks'...
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
Deleted branch realm-memory-leaks (was 2c31ec3).
~/git/super-soft@master$
```

## Planned features

- [x] `git realm enter [realm-name]` will enter new or existing realm
- [x] Reword current realm - generated or typed - `git realm reword [realm-name]`
- [x] Configuration support
- [ ] Merging realms into common branch (like Git-Flow)

## Dependant commands

- bash _(based upon)_
- git _(manipulated with)_
- coreutils - cat, shuf
- grep
- sed
