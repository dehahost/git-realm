# git-realm

git-realm is a Git plugin written mainly for fast and/or creative development.

## Requirements

Make sure you have Cracklib packages installed. If not run the following:

```bash
# / Debian based systems - Debian, Ubuntu, Linux Mint, etc.
~$ sudo apt-get install libcrack2

# / openSUSE (may not be required)
~$ sudo zypper install cracklib
```

## Installation

**1**/ Clone this repo into your usual location.\
**2**/ Symlink git-realm to `/usr/local/bin/` (or a different directory in `$PATH` env. variable)\
**3**/ Try `git realm help` and if it works, profit!

## Configuration

git-realm can be configured with Git config:

- `realm.separator` _(default: -)_ Separator character between _"realm"_ and realm name - ie. "realm-decent-stray" or "realm/gastro-tour"
- `realm.commonBranch` _(default: master)_ Common Git branch - could be _main_, some prefers _master_, others _production_.
- `realm.unpackPath` _(default: /tmp/cracklib_pw.dict)_ Where should be saved output of cracklib-unpacker - openSUSE only

## Usage

### Listing

```bash
 ~/realm-test@master$ git realm list
base-one
decent-stray
```

### Entering realms

**1**/ The easy way\
New realm is entered from _`HEAD`_.

```bash
 ~/realm-test@realm-base-one % git realm enter
Creating a new realm called 'matrices-gaucherie'...
Switched to a new branch 'realm-matrices-gaucherie'
 ~/realm-test@realm-matrices-gaucherie %

# * bb52534 (HEAD -> realm-matrices-gaucherie, realm-base-one) feat: Add hello.sh
# * 1d483b6 chore: Update README.md
# * 1d59365 (master) feat: Add README.md
```

**2**/ From common branch

```bash
 ~/realm-test@realm-base-one % git realm enter -c
Going to checkout from master branch.
Creating a new realm called 'krause-propounded'...
Switched to a new branch 'realm-krause-propounded'
 ~/realm-test@realm-krause-propounded %

# * bb52534 (realm-base-one) feat: Add hello.sh
# * 1d483b6 chore: Update README.md
# * 1d59365 (HEAD -> realm-krause-propounded, master) feat: Add README.md
```

**3**/ With a custom name

```bash
 ~/realm-test@master % git realm enter BAU-30000
Creating a new realm called 'BAU-30000'...
Switched to a new branch 'realm-BAU-30000'
 ~/realm-test@realm-BAU-30000 %
```

### Rewording entered realm

**1**/ New random name

```bash
 ~/realm-test@realm-BAU-30000 % git realm reword
Rewording to 'restrictively-melina'...
 ~/realm-test@realm-restrictively-melina %
```

**2**/ Specific name

```bash
 ~/realm-test@realm-restrictively-melina % git realm reword GRLM-4
Rewording to 'GRLM-4'...
 ~/realm-test@realm-GRLM-4 %
```

### Leaving realms

```bash
 ~/realm-test@realm-GRLM-4 % git realm leave
Leaving realm called 'GRLM-4'...
Switched to branch 'master'
 ~/realm-test@master %
```

### Disposing realms

**1**/ Currently used realm

```bash
 ~/realm-test@realm-GRLM-4 % git realm dispose
Leaving and disposing currently used realm called 'GRLM-4'...
Switched to branch 'master'
Deleted branch realm-GRLM-4 (was 1d59365).
 ~/realm-test@master %
```

**2**/ Existing realm

```bash
 ~/tempie/realm-test@master % git realm dispose base-one
Disposing realm called 'base-one'...
Deleted branch realm-base-one (was bb52534).
```

## Planned features

- [x] `git realm enter [realm-name]` will enter new or existing realm
- [x] Reword current realm - generated or typed - `git realm reword [realm-name]`
- [x] Configuration support
- [ ] Merging realms into common branch (like Git-Flow)
- [ ] Rewording without entering the realm

## Dependant commands

- bash _(based upon)_
- git _(manipulated with)_
- coreutils - cat, shuf
- grep
- sed
