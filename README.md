# Powerlevel10k
[![Gitter](https://badges.gitter.im/powerlevel10k/community.svg)](
  https://gitter.im/powerlevel10k/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

Powerlevel10k is a theme for Zsh. It emphasizes [speed](#uncompromising-performance),
[flexibility](#extremely-customizable) and [out-of-the-box experience](#configuration-wizard).

![Powerlevel10k](
https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/prompt-styles-high-contrast.png)

To see what Powerlevel10k is about, scroll through [features](#features).

Powerlevel9k users, go [here](#powerlevel9k-compatibility).

## Table of contents

- [Features](#features)
  - [Configuration wizard](#configuration-wizard)
  - [Uncompromising performance](#uncompromising-performance)
  - [Powerlevel9k compatibility](#powerlevel9k-compatibility)
  - [Pure compatibility](#pure-compatibility)
  - [Instant prompt](#instant-prompt)
  - [Show on command](#show-on-command)
  - [Transient prompt](#transient-prompt)
  - [Current directory that just works](#current-directory-that-just-works)
  - [Extremely customizable](#extremely-customizable)
  - [Batteries included](#batteries-included)
  - [Extensible](#extensible)
- [Installation](#installation)
  - [Manual](#manual)
  - [Oh My Zsh](#oh-my-zsh)
  - [Prezto](#prezto)
  - [Zim](#zim)
  - [Antibody](#antibody)
  - [Antigen](#antigen)
  - [Zplug](#zplug)
  - [Zgen](#zgen)
  - [Zplugin](#zplugin)
  - [Zinit](#zinit)
  - [Homebrew](#homebrew)
  - [Arch Linux](#arch-linux)
- [Configuration](#configuration)
  - [For new users](#for-new-users)
  - [For Powerlevel9k users](#for-powerlevel9k-users)
- [Fonts](#fonts)
  - [Meslo Nerd Font patched for Powerlevel10k](#meslo-nerd-font-patched-for-powerlevel10k)
    - [Automatic font installation](#automatic-font-installation)
    - [Manual font installation](#manual-font-installation)
- [Try it in Docker](#try-it-in-docker)
- [License](#license)
- [FAQ](docs/faq.md)
- [Troubleshooting](docs/troubleshooting.md)

Ready to give Powerlevel10k a try?

1. Install [the recommended font](#meslo-nerd-font-patched-for-powerlevel10k). *Optional but highly
   recommended.*
1. Install Powerlevel10k for your plugin manager.
   - [Manual](#manual) 👈 **choose this if confused or uncertain**
   - [Oh My Zsh](#oh-my-zsh)
   - [Prezto](#prezto)
   - [Zim](#zim)
   - [Antibody](#antibody)
   - [Antigen](#antigen)
   - [Zplug](#zplug)
   - [Zgen](#zgen)
   - [Zplugin](#zplugin)
   - [Zinit](#zinit)
   - [Homebrew](#homebrew)
   - [Arch Linux](#arch-linux)
1. Restart Zsh.
1. Type `p10k configure` if the configuration wizard doesn't start automatically.

## Features

### Configuration wizard

Type `p10k configure` to access the builtin configuration wizard right from your terminal.

![Powerlevel10k Configuration Wizard](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/configuration-wizard.gif)

All styles except [Pure](#pure-compatibility) are functionally equivalent. They display the same
information and differ only in presentation.

Configuration wizard creates `~/.p10k.zsh` based on your preferences. Additional prompt
customization can be done by editing this file. It has plenty of comments to help you navigate
through configuration options.

*Tip*: Install [the recommended font](#meslo-nerd-font-patched-for-powerlevel10k) before
running `p10k configure` to unlock all prompt styles.

*FAQ:*

- [What is the best prompt style in the configuration wizard?](
    docs/faq.md#what-is-the-best-prompt-style-in-the-configuration-wizard)
- [What do different symbols in Git status mean?](
    docs/faq.md#what-do-different-symbols-in-git-status-mean)
- [How do I change prompt colors?](
    docs/faq.md#how-do-i-change-prompt-colors)

*Troubleshooting*:

- [Some prompt styles are missing from the configuration wizard](
    docs/troubleshooting.md#some-prompt-styles-are-missing-from-the-configuration-wizard).
- [Question mark in prompt](
    docs/troubleshooting.md#question-mark-in-prompt).
- [Icons, glyphs or powerline symbols don't render](
    docs/troubleshooting.md#icons-glyphs-or-powerline-symbols-dont-render).
- [Sub-pixel imperfections around powerline symbols](
    docs/troubleshooting.md#sub-pixel-imperfections-around-powerline-symbols).
- [Directory is difficult to see in prompt when using Rainbow style](
    docs/troubleshooting.md#directory-is-difficult-to-see-in-prompt-when-using-rainbow-style).

### Uncompromising performance

When you hit *ENTER*, the next prompt appears instantly. With Powerlevel10k there is no prompt lag.
If you install Cygwin on Raspberry Pi, `cd` into a Linux Git repository and activate enough prompt
segments to fill four prompt lines on both sides of the screen... wait, that's just crazy and no
one ever does that. Probably impossible, too. The point is, Powerlevel10k prompt is always fast, no
matter what you do!

![Powerlevel10k Performance](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/performance.gif)

Note how the effect of every command is instantly reflected by the very next prompt.

| Command                       | Prompt Indicator | Meaning                                                               |
|-------------------------------|:----------------:|----------------------------------------------------------------------:|
| `timew start hack linux`      | `🛡️ hack linux`  | time tracking enabled in [timewarrior](https://timewarrior.net/)      |
| `touch x y`                   | `?2`             | 2 untracked files in the Git repo                                     |
| `rm COPYING`                  | `!1`             | 1 unstaged change in the Git repo                                     |
| `echo 2.7.3 >.python-version` | `🐍 2.7.3`       | the current python version in [pyenv](https://github.com/pyenv/pyenv) |

Other Zsh themes capable of displaying the same information either produce prompt lag or print
prompt that doesn't reflect the current state of the system and then refresh it later. With
Powerlevel10k you get fast prompt *and* up-to-date information.

*FAQ*: [Is it really fast?](docs/faq.md#is-it-really-fast)

### Powerlevel9k compatibility

Powerlevel10k understands all [Powerlevel9k](https://github.com/Powerlevel9k/powerlevel9k)
configuration parameters.

![Powerlevel10k Compatibility with 9k](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/9k-compatibility.gif)

[Migration](#installation) from Powerlevel9k to Powerlevel10k is a straightforward process. All
your `POWERLEVEL9K` configuration parameters will still work. Prompt will look the same as before
([almost](
  #does-powerlevel10k-always-render-exactly-the-same-prompt-as-powerlevel9k-given-the-same-config))
but it will be [much faster](#uncompromising-performance) ([certainly](#is-it-really-fast)).

*FAQ*:

- [I'm using Powerlevel9k with Oh My Zsh. How do I migrate?](
    docs/faq.md#im-using-powerlevel9k-with-oh-my-zsh-how-do-i-migrate)
- [Does Powerlevel10k always render exactly the same prompt as Powerlevel9k given the same config?](
    docs/faq.md#does-powerlevel10k-always-render-exactly-the-same-prompt-as-powerlevel9k-given-the-same-config)
- [What is the relationship between Powerlevel9k and Powerlevel10k?](
    docs/faq.md#What-is-the-relationship-between-powerlevel9k-and-powerlevel10k)

### Pure compatibility

Powerlevel10k can produce the same prompt as [Pure](https://github.com/sindresorhus/pure). Type
`p10k configure` and select *Pure* style.

![Powerlevel10k Pure Style](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/pure-style.gif)

You can still use Powerlevel10k features such as [transient prompt](#transient-prompt) or
[instant prompt](#instant-prompt) when sporting Pure style.

To customize prompt, edit `~/.p10k.zsh`. Powerlevel10k doesn't recognize Pure configuration
parameters, so you'll need to use `POWERLEVEL9K_COMMAND_EXECUTION_TIME_THRESHOLD=3` instead of
`PURE_CMD_MAX_EXEC_TIME=3`, etc. All relevant parameters are in `~/.p10k.zsh`. This file has
plenty of comments to help you navigate through it.

*FAQ:* [What is the best prompt style in the configuration wizard?](
  docs/faq.md#what-is-the-best-prompt-style-in-the-configuration-wizard)

### <a name='what-is-instant-prompt'></a>Instant prompt

If your `~/.zshrc` loads many plugins, or perhaps just a few slow ones
(for example, [pyenv](https://github.com/pyenv/pyenv) or [nvm](https://github.com/nvm-sh/nvm)), you
may have noticed that it takes some time for Zsh to start.

![Powerlevel10k No Instant Prompt](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/no-instant-prompt.gif)

Powerlevel10k can remove Zsh startup lag **even if it's not caused by a theme**.

![Powerlevel10k Instant Prompt](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/instant-prompt.gif)

This feature is called *Instant Prompt*. You need to explicitly enable it through `p10k configure`
or [manually](#how-do-i-enable-instant-prompt). It does what it says on the tin -- prints prompt
instantly upon Zsh startup allowing you to start typing while plugins are still loading.

Other themes *increase* Zsh startup lag -- some by a lot, others by a just a little. Powerlevel10k
*removes* it outright.

*FAQ:* [How do I enable instant prompt?](docs/faq.md#how-do-i-enable-instant-prompt)

### Show on command

The behavior of some commands depends on global environment. For example, `kubectl run ...` runs an
image on the cluster defined by the current kubernetes context. If you frequently change context
between "prod" and "testing", you might want to display the current context in Zsh prompt. If you do
likewise for AWS, Azure and Google Cloud credentials, prompt will get pretty crowded.

Enter *Show On Command*. This feature makes prompt segments appear only when they are relevant to
the command you are currently typing.

![Powerlevel10k Show On Command](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/show-on-command.gif)

Configs created by `p10k configure` enable show on command for several prompt segments by default.
Here's the relevant parameter for kubernetes context:

```zsh
# Show prompt segment "kubecontext" only when the command you are typing
# invokes kubectl, helm, kubens, kubectx, oc, istioctl or kogito.
typeset -g POWERLEVEL9K_KUBECONTEXT_SHOW_ON_COMMAND='kubectl|helm|kubens|kubectx|oc|istioctl|kogito'
```

To customize when different prompt segments are shown, open `~/.p10k.zsh`, search for
`SHOW_ON_COMMAND` and either remove these parameters to display affected segments unconditionally,
or change their values.

### Transient prompt

When *Transient Prompt* is enabled through `p10k configure`, Powerlevel10k will trim down every
prompt when accepting a command line.

![Powerlevel10k Transient Prompt](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/transient-prompt.gif)

Transient prompt makes it much easier to copy-paste series of commands from the terminal scrollback.

*Tip*: If you enable transient prompt, take advantage of two-line prompt. You'll get the benefit of
extra space for typing commands without the usual drawback of reduced scrollback density. Sparse
prompt (with an empty line before prompt) also works great in combination with transient prompt.

### Current directory that just works

The current working directory is perhaps the most important prompt segment. Powerlevel10k goes to
great length to highlight its important parts and to truncate it with the least loss of information
when horizontal space gets scarce.

![Powerlevel10k Directory Truncation](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/directory-truncation.gif)

When the full directory doesn't fit, the leftmost segment gets truncated to its shortest unique
prefix. In the screencast, `~/work` becomes `~/wo`. It couldn't be truncated to `~/w` because it
would be ambiguous (there was `~/wireguard` when the session was recorded). The next segment --
`projects` -- turns into `p` as there was nothing else that started with `p` in `~/work/`.

Directory segments are shown in one of three colors:

- Truncated segments are bleak.
- Important segments are bright and never truncated. These include the first and the last segment,
  roots of Git repositories, etc.
- Regular segments (not truncated but can be) use in-between color.

*Tip*: If you copy-paste a truncated directory and hit *TAB*, it'll complete to the original.

*Troubleshooting*: [Directory is difficult to see in prompt when using Rainbow style.](
  docs/troubleshooting.md#directory-is-difficult-to-see-in-prompt-when-using-rainbow-style)

### Extremely customizable

Powerlevel10k can be configured to look like any other Zsh theme out there.

![Powerlevel10k Other Theme Emulation](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/other-theme-emulation.gif)

[Pure](#pure-compatibility), [Powerlevel9k](#powerlevel9k-compatibility) and [robbyrussell](
  #how-to-make-powerlevel10k-look-like-robbyrussell-oh-my-zsh-theme) emulations are built-in.
To emulate the appearance of other themes, you'll need to write a suitable configuration file. The
best way to go about it is to run `p10k configure`, select the style that is the closest to your
goal and then edit `~/.p10k.zsh`.

The full range of Powerlevel10k appearance spans from spartan:

![Powerlevel10k Spartan Style](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/spartan-style.png)

To ~~ridiculous~~ extravagant:

![Powerlevel10k Extravagant Style](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/extravagant-style.png)

### Batteries included

Powerlevel10k comes with dozens of built-in high quality segments. When you run `p10k configure`
and choose any style except [Pure](#pure-compatibility), many of these segments get enabled by
default while others be manually enabled by opening `~/.p10k.zsh` and uncommenting them. You can
enable as many segments as you like. It won't slow down your prompt or Zsh startup.

| Segment | Meaning |
|--------:|---------|
| `os_icon` | your OS logo (apple for macOS, swirl for debian, etc.) |
| `dir` | current working directory |
| `vcs` | Git repository status |
| `prompt_char` | multi-functional prompt symbol; changes depending on vi mode: `❯`, `❮`, `Ⅴ`, `▶` for insert, command, visual and replace mode respectively; turns red on error |
| `context` | user@hostname |
| `status` | exit code of the last command |
| `command_execution_time` | duration (wall time) of the last command |
| `background_jobs` | presence of background jobs |
| `time` | current time |
| `direnv` | [direnv](https://direnv.net/) status |
| `asdf` | tool versions from [asdf](https://github.com/asdf-vm/asdf) |
| `virtualenv` | python environment from [venv](https://docs.python.org/3/library/venv.html) |
| `anaconda` | virtual environment from [conda](https://conda.io/) |
| `pyenv` | python environment from [pyenv](https://github.com/pyenv/pyenv) |
| `goenv` | go environment from [goenv](https://github.com/syndbg/goenv) |
| `nodenv` | node.js environment from [nodenv](https://github.com/nodenv/nodenv) |
| `nvm` | node.js environment from [nvm](https://github.com/nvm-sh/nvm) |
| `nodeenv` | node.js environment from [nodeenv](https://github.com/ekalinin/nodeenv) |
| `rbenv` | ruby environment from [rbenv](https://github.com/rbenv/rbenv) |
| `rvm` | ruby environment from [rvm](https://rvm.io) |
| `fvm` | flutter environment from [fvm](https://github.com/leoafarias/fvm) |
| `luaenv` | lua environment from [luaenv](https://github.com/cehoffman/luaenv) |
| `jenv` | java environment from [jenv](https://github.com/jenv/jenv) |
| `plenv` | perl environment from [plenv](https://github.com/tokuhirom/plenv) |
| `phpenv` | php environment from [phpenv](https://github.com/phpenv/phpenv) |
| `haskell_stack` | haskell version from [stack](https://haskellstack.org/) |
| `node_version` | [node.js](https://nodejs.org/) version |
| `go_version` | [go](https://golang.org) version |
| `rust_version` | [rustc](https://www.rust-lang.org) version |
| `dotnet_version` | [dotnet](https://dotnet.microsoft.com) version |
| `php_version` | [php](https://www.php.net/) version |
| `laravel_version` | [laravel php framework](https://laravel.com/) version |
| `package` | `name@version` from [package.json](https://docs.npmjs.com/files/package.json) |
| `kubecontext` | current [kubernetes](https://kubernetes.io/) context |
| `terraform` | [terraform](https://www.terraform.io) workspace |
| `aws` | [aws profile](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html) |
| `aws_eb_env` | [aws elastic beanstalk](https://aws.amazon.com/elasticbeanstalk/) environment |
| `azure` | [azure](https://docs.microsoft.com/en-us/cli/azure) account name |
| `gcloud` | [google cloud](https://cloud.google.com/) cli account and project |
| `google_app_cred` | [google application credentials](https://cloud.google.com/docs/authentication/production) |
| `nordvpn` | [nordvpn](https://nordvpn.com/) connection status |
| `ranger` | [ranger](https://github.com/ranger/ranger) shell |
| `nnn` | [nnn](https://github.com/jarun/nnn) shell |
| `vim_shell` | [vim](https://www.vim.org/) shell (`:sh`) |
| `midnight_commander` | [midnight commander](https://midnight-commander.org/) shell |
| `nix_shell` | [nix shell](https://nixos.org/nixos/nix-pills/developing-with-nix-shell.html) indicator |
| `todo` | [todo](https://github.com/todotxt/todo.txt-cli) items |
| `timewarrior` | [timewarrior](https://timewarrior.net/) tracking status |
| `taskwarrior` | [taskwarrior](https://taskwarrior.org/) task count |
| `vpn_ip` | virtual private network indicator |
| `ip` | IP address and bandwidth usage for a specified network interface |
| `load` | CPU load |
| `disk_usage` | disk usage |
| `ram` | free RAM |
| `swap` | used swap |
| `public_ip` | public IP address |
| `proxy` | system-wide http/https/ftp proxy |
| `wifi` | WiFi speed |
| `battery` | internal battery state and charge level (yep, batteries *literally* included) |

### Extensible

If there is no prompt segment that does what you need, implement your own. Powerlevel10k provides
public API for defining segments that are as fast and as flexible as built-in ones.

![Powerlevel10k Custom Segment](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/custom-segment.gif)

On Linux you can fetch current CPU temperature by reading `/sys/class/thermal/thermal_zone0/temp`.
The screencast shows how to define a prompt segment to display this value. Once the segment is
defined, you can use it like any other segment. All standard customization parameters will work for
it out of the box.

Type `p10k help segment` for reference.

*Tip*: Prefix names of your own segments with `my_` to avoid clashes with future versions of
Powerlevel10k.

## Installation

### Manual

```zsh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>! ~/.zshrc
```

This is the simplest kind of installation and it works even if you are using a plugin manager. Just
make sure to disable the current theme in your plugin manager. See
[troubleshooting](docs/troubleshooting.md#cannot-make-powerlevel10k-work-with-my-plugin-manager) for help.

### Oh My Zsh

```zsh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
```

Set `ZSH_THEME="powerlevel10k/powerlevel10k"` in `~/.zshrc`.

### Prezto

Add `zstyle :prezto:module:prompt theme powerlevel10k` to `~/.zpreztorc`.

### Zim

Add `zmodule romkatv/powerlevel10k` to `~/.zimrc` and run `zimfw install`.

### Antibody

Add `antibody bundle romkatv/powerlevel10k` to `~/.zshrc`.

### Antigen

Add `antigen theme romkatv/powerlevel10k` to `~/.zshrc`. Make sure you have `antigen apply`
somewhere after it.

### Zplug

Add `zplug romkatv/powerlevel10k, as:theme, depth:1` to `~/.zshrc`.

### Zgen

Add `zgen load romkatv/powerlevel10k powerlevel10k` to `~/.zshrc`.

### Zplugin

Add `zplugin ice depth=1; zplugin light romkatv/powerlevel10k` to `~/.zshrc`.

The use of `depth=1` ice is optional. Other types of ice are neither recommended nor officially
supported by Powerlevel10k.

### Zinit

Add `zinit ice depth=1; zinit light romkatv/powerlevel10k` to `~/.zshrc`.

The use of `depth=1` ice is optional. Other types of ice are neither recommended nor officially
supported by Powerlevel10k.

### Homebrew

```zsh
brew install romkatv/powerlevel10k/powerlevel10k
echo 'source /usr/local/opt/powerlevel10k/powerlevel10k.zsh-theme' >>! ~/.zshrc
```

### Arch Linux

```zsh
pacman -Sy --noconfirm zsh-theme-powerlevel10k
echo 'source /usr/share/zsh-theme-powerlevel10k/powerlevel10k.zsh-theme' >>! ~/.zshrc
```

## Configuration

### For new users

On the first run, Powerlevel10k [configuration wizard](#configuration-wizard) will ask you a few
questions and configure your prompt. If it doesn't trigger automatically, type `p10k configure`.
Configuration wizard creates `~/.p10k.zsh` based on your preferences. Additional prompt
customization can be done by editing this file. It has plenty of comments to help you navigate
through configuration options.

*FAQ*:

- [What is the best prompt style in the configuration wizard?](
    docs/faq.md#what-is-the-best-prompt-style-in-the-configuration-wizard)
- [What do different symbols in Git status mean?](
    docs/faq.md#what-do-different-symbols-in-git-status-mean)
- [How do I change the format of Git status?](#how-do-i-change-the-format-of-git-status)
- [How do I add username and/or hostname to prompt?](
    docs/faq.md#how-do-i-add-username-andor-hostname-to-prompt)
- [How do I change prompt colors?](#how-do-i-change-prompt-colors)
- [Why some prompt segments appear and disappear as I'm typing?](
    docs/faq.md#why-some-prompt-segments-appear-and-disappear-as-im-typing)

*Troubleshooting*:

- [Question mark in prompt](
    docs/troubleshooting.md#question-mark-in-prompt).
- [Icons, glyphs or powerline symbols don't render](
    docs/troubleshooting.md#icons-glyphs-or-powerline-symbols-dont-render).
- [Sub-pixel imperfections around powerline symbols](
    docs/troubleshooting.md#sub-pixel-imperfections-around-powerline-symbols).
- [Directory is difficult to see in prompt when using Rainbow style](
    docs/troubleshooting.md#directory-is-difficult-to-see-in-prompt-when-using-rainbow-style).

### For Powerlevel9k users

If you've been using Powerlevel9k before, **do not remove the configuration options**. Powerlevel10k
will pick them up and provide you with the same prompt UI you are used to. See
[Powerlevel9k compatibility](#powerlevel9k-compatibility).

*FAQ*:

- [I'm using Powerlevel9k with Oh My Zsh. How do I migrate?](
    docs/faq.md#im-using-powerlevel9k-with-oh-my-zsh-how-do-i-migrate)
- [What is the relationship between Powerlevel9k and Powerlevel10k?](
    docs/faq.md#what-is-the-relationship-between-powerlevel9k-and-powerlevel10k)
- [Does Powerlevel10k always render exactly the same prompt as Powerlevel9k given the same config?](
    docs/faq.md#does-powerlevel10k-always-render-exactly-the-same-prompt-as-powerlevel9k-given-the-same-config)

*Troubleshooting*: [Extra or missing spaces in prompt compared to Powerlevel9k](
  docs/troubleshooting.md#extra-or-missing-spaces-in-prompt-compared-to-powerlevel9k).

## Fonts

Powerlevel10k doesn't require custom fonts but can take advantage of them if they are available.
It works well with [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts),
[Source Code Pro](https://github.com/adobe-fonts/source-code-pro),
[Font Awesome](https://fontawesome.com/), [Powerline](https://github.com/powerline/fonts), and even
the default system fonts. The full choice of style options is available only when using
[Nerd Fonts](https://github.com/ryanoasis/nerd-fonts).

👇 **Recommended font**: Meslo Nerd Font patched for Powerlevel10k. 👇

### <a name='recommended-meslo-nerd-font-patched-for-powerlevel10k'></a>Meslo Nerd Font patched for Powerlevel10k

Gorgeous monospace font designed by Jim Lyles for Bitstream, customized by the same for Apple,
further customized by André Berg, and finally patched by yours truly with customized scripts
originally developed by Ryan L McIntyre of Nerd Fonts. Contains all glyphs and symbols that
Powerlevel10k may need. Battle-tested in dozens of different terminals on all major operating
systems.

*FAQ*: [How was the recommended font created?](docs/faq.md#how-was-the-recommended-font-created)

#### Automatic font installation

If you are using iTerm2 or Termux, `p10k configure` can install the recommended font for you.
Simply answer `Yes` when asked whether to install *Meslo Nerd Font*.

If you are using a different terminal, proceed with manual font installation. 👇

#### Manual font installation

Download these four ttf files:

- [MesloLGS NF Regular.ttf](
    https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf)
- [MesloLGS NF Bold.ttf](
    https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf)
- [MesloLGS NF Italic.ttf](
    https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf)
- [MesloLGS NF Bold Italic.ttf](
    https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf)

Double-click on each file and click "Install". This will make `MesloLGS NF` font available to all
applications on your system. Configure your terminal to use this font:

- **iTerm2**: Open *iTerm2 → Preferences → Profiles → Text* and set *Font* to `MesloLGS NF`.
  Alternatively, type `p10k configure` and answer `Yes` when asked whether to install
  *Meslo Nerd Font*.
- **Apple Terminal** Open *Terminal → Preferences → Profiles → Text*, click *Change* under *Font*
  and select `MesloLGS NF` family.
- **Hyper**: Open *Hyper → Edit → Preferences* and change the value of `fontFamily` under
  `module.exports.config` to `MesloLGS NF`.
- **Visual Studio Code**: Open *File → Preferences → Settings*, enter
  `terminal.integrated.fontFamily` in the search box and set the value to `MesloLGS NF`.
- **GNOME Terminal** (the default Ubuntu terminal): Open *Terminal → Preferences* and click on the
  selected profile under *Profiles*. Check *Custom font* under *Text Appearance* and select
  `MesloLGS NF Regular`.
- **Konsole**: Open *Settings → Edit Current Profile → Appearance*, click *Select Font* and select
  `MesloLGS NF Regular`.
- **Tilix**: Open *Tilix → Preferences* and click on the selected profile under *Profiles*. Check
  *Custom font* under *Text Appearance* and select `MesloLGS NF Regular`.
- **Windows Console Host** (the old thing): Click the icon in the top left corner, then
  *Properties → Font* and set *Font* to `MesloLGS NF`.
- **Windows Terminal** (the new thing): Open *Settings* (`Ctrl+,`), search for `fontFace` and set
  value to `MesloLGS NF` for every profile.
- **Termux**: Type `p10k configure` and answer `Yes` when asked whether to install
  *Meslo Nerd Font*.

**IMPORTANT:** Run `p10k configure` after changing terminal font. The old `~/.p10k.zsh` may work
incorrectly with the new font.

_Using a different terminal and know how to set the font for it? Share your knowledge by sending a
PR to expand the list!_

## Try it in Docker

Try Powerlevel10k in Docker. You can safely make any changes to the file system while trying out
the theme. Once you exit Zsh, the image is deleted.

```zsh
docker run -e TERM -e COLORTERM -it --rm debian:buster bash -uec '
  apt update
  apt install -y git zsh nano vim
  git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
  echo "source ~/powerlevel10k/powerlevel10k.zsh-theme" >>~/.zshrc
  cd ~/powerlevel10k
  exec zsh'
```

*Tip*: Install [the recommended font](#meslo-nerd-font-patched-for-powerlevel10k) before
running the Docker command to get access to all prompt styles.

*Tip*: Run `p10k configure` while in Docker to try a different prompt style.

## License

Powerlevel10k is released under the
[MIT license](https://github.com/romkatv/powerlevel10k/blob/master/LICENSE).
