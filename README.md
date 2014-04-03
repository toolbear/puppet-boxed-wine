# Boxed Wine Puppet Module for Boxen

Manage your Emacs configuration with Boxen and [Cask](http://cask.github.io/).

Boxed Wine prescribes a layout and a few conventions for `.emacs.d` and
-- excepting Cask and its dependencies -- is vanilla Emacs.

Emacs packages can be installed from the standard sources (gnu, melpa, …)
or directly from GitHub.

[![Build Status](https://travis-ci.org/toolbear/puppet-boxed-wine.png?branch=master)](https://travis-ci.org/toolbear/puppet-boxed-wine)

## Usage

```puppet
include boxen::boxed_wine
```
## Layout and Conventions

```
.emacs.d
├── Cask
├── init.el
├── themes
│   └── …
└── $USER
    ├── custom.el
    └── …
```
-----------------|--
`Cask`           | Emacs packages to install or keep updated. Analogous to `Puppetfile` or `Gemfile`.
`init.el`        | Initialize Cask and Boxed Wine. Avoid putting your customizations here.
`themes`         | Themes installed here automatically added to `custom-theme-load-path`; searched recursively.
`$User`          | Your customizations, loaded after packages listed `Cask`; not searched recursively.
`$User/custom.el | Settings modified by Custom, e.g. `M-x customize`. Avoid manual edits.

Additionally, Cask stores installed packages in `.emacs.d/.cask/`.

### Example `.emacs.d` for user "toolbear"

```
.emacs.d
├── .cask
│   └── 24.3.1
│       └── elpa
│           ├── diff-hl-20140212.438
│           ├── puppet-mode-20120804.2038
│           └── s-20131223.944
├── Cask
├── init.el
├── themes
│   ├── emacs-color-theme-solarized
│   │   ├── solarized-dark-theme.el
│   │   └── solarized-light-theme.el
│   └── zenburn-emacs
│       └── zenburn-theme.el
└── toolbear
    ├── custom.el
    ├── font.el
    ├── indentation.el
    ├── theme.el
    └── unicode.el
```

*(some items omitted for brevity)*

## Required Puppet Modules

* `boxen`
* `emacs` (>= 24.3)
