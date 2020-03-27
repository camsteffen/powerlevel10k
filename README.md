# Powerlevel10k
[![Gitter](https://badges.gitter.im/powerlevel10k/community.svg)](
  https://gitter.im/powerlevel10k/community?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

Powerlevel10k is a theme for Zsh. It emphasizes [speed](#uncompromising-performance),
[flexibility](#extremely-customizable) and [out-of-the-box experience](#configuration-wizard).

![Powerlevel10k](
https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/prompt-styles-high-contrast.png)

To see what Powerlevel10k is about, scroll through [features](#features).

Powerlevel9k users, go [here](#powerlevel9k-compatibility).

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

The full [table of contents](#table-of-contents) is at the bottom.

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
    #some-prompt-styles-are-missing-from-the-configuration-wizard).
- [Question mark in prompt](#question-mark-in-prompt).
- [Icons, glyphs or powerline symbols don't render](#icons-glyphs-or-powerline-symbols-dont-render).
- [Sub-pixel imperfections around powerline symbols](
    #sub-pixel-imperfections-around-powerline-symbols).
- [Directory is difficult to see in prompt when using Rainbow style](
    #directory-is-difficult-to-see-in-prompt-when-using-rainbow-style).

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
  #directory-is-difficult-to-see-in-prompt-when-using-rainbow-style)

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
[troubleshooting](#cannot-make-powerlevel10k-work-with-my-plugin-manager) for help.

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

- [Question mark in prompt](#question-mark-in-prompt).
- [Icons, glyphs or powerline symbols don't render](#icons-glyphs-or-powerline-symbols-dont-render).
- [Sub-pixel imperfections around powerline symbols](
    #sub-pixel-imperfections-around-powerline-symbols).
- [Directory is difficult to see in prompt when using Rainbow style](
    #directory-is-difficult-to-see-in-prompt-when-using-rainbow-style).

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
  #extra-or-missing-spaces-in-prompt-compared-to-powerlevel9k).

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

## Troubleshooting

### Question mark in prompt

If it looks like a regular `?`, that's normal. It means you have untracked files in the current Git
repository. Type `git status` to see these files. You can change this symbol or disable the display
of untracked files altogether. Search for `untracked files` in `~/.p10k.zsh`.

*FAQ*: [What do different symbols in Git status mean?](
  docs/faq.md#what-do-different-symbols-in-git-status-mean)

You can also get a weird-looking question mark in your prompt if your terminal's font is missing
some glyphs. See [icons, glyphs or powerline symbols don't render](
  #icons-glyphs-or-powerline-symbols-dont-render).

### Icons, glyphs or powerline symbols don't render

Restart your terminal, [install the recommended font](#meslo-nerd-font-patched-for-powerlevel10k)
and run `p10k configure`.

### Sub-pixel imperfections around powerline symbols

![Powerline Prompt Imperfections](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/powerline-imperfections.png)

There are three imperfections on the screenshot. From left to right:

1. A thin blue line (a sub-pixel gap) between the content of a prompt segment and the following
powerline connection.
1. Incorrect alignment of a powerline connection and the following prompt segment. The connection
appears shifted to the right.
1. A thin red line below a powerline connection. The connection appears shifted up.

Zsh themes don't have down-to-pixel control over the terminal content. Everything you see on the
screen is made of monospace characters. A white powerline prompt segment is made of text on white
background followed by U+E0B0 (a right-pointing triangle).

![Powerline Prompt Imperfections](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/powerline-anatomy.png)

If Powerlevel10k prompt has imperfections around powerline symbols, you'll see exactly the same
imperfections with all powerline themes (Agnoster, Powerlevel9k, Powerline, etc.)

There are several things you can try to deal with these imperfections:

- Try [the recommended font](#meslo-nerd-font-patched-for-powerlevel10k). If you are already using
  it, switching to another font may help but is unlikely.
- Change terminal font size one point up or down. For example, in iTerm2 powerline prompt looks
  perfect at font sizes 11 and 13 but breaks down at 12.
- Enable builtin powerline glyphs in terminal settings if your terminal supports it (iTerm2 does).
- Change font hinting and/or anti-aliasing mode in the terminal settings.
- Shift all text one pixel up/down/left/right if your terminal has an option to do so.
- Try a different terminal.

A more radical solution is to switch to prompt style without background. Type `p10k configure` and
select *Lean*. This style has a modern lightweight look. As a bonus, it doesn't suffer from
rendering imperfections that afflict powerline-style prompt.

### Error: character not in range

Type `echo '\u276F'`. If you get an error saying "zsh: character not in range", your locale
doesn't support UTF-8. You need to fix it. If you are running Zsh over SSH, see
[this](https://github.com/romkatv/powerlevel10k/issues/153#issuecomment-518347833). If you are
running Zsh locally, Google "set UTF-8 locale in *your OS*".

### Cursor is in the wrong place

Type `echo '\u276F'`. If you get an error saying "zsh: character not in range", see the
[previous section](#zsh-character-not-in-range).

If the `echo` command prints `❯` but the cursor is still in the wrong place, install
[the recommended font](#meslo-nerd-font-patched-for-powerlevel10k) and run
`p10k configure`.

If this doesn't help, add `unset ZLE_RPROMPT_INDENT` at the bottom of `~/.zshrc`.

Still having issues? Run the following command to diagnose the problem:

```zsh
() {
  emulate -L zsh
  setopt err_return no_unset
  local text
  print -rl -- 'Select a part of your prompt from the terminal window and paste it below.' ''
  read -r '?Prompt: ' text
  local -i len=${(m)#text}
  local frame="+-${(pl.$len..-.):-}-+"
  print -lr -- $frame "| $text |" $frame
}
```

#### If the prompt line aligns with the frame

```text
+------------------------------+
| romka@adam ✓ ~/powerlevel10k |
+------------------------------+
```

If the output of the command is aligned for every part of your prompt (left and right), this
indicates a bug in the theme or your config. Use this command to diagnose it:

```zsh
print -rl -- ${(eq+)PROMPT} ${(eq+)RPROMPT}
```

Look for `%{...%}` and backslash escapes in the output. If there are any, they are the likely
culprits. Open an issue if you get stuck.

#### If the prompt line is longer than the frame

```text
+-----------------------------+
| romka@adam ✓ ~/powerlevel10k |
+-----------------------------+
```

This is usually caused by a terminal bug or misconfiguration that makes it print ambiguous-width
characters as double-width instead of single width. For example,
[this issue](https://github.com/romkatv/powerlevel10k/issues/165).

#### If the prompt line is shorter than the frame and is mangled

```text
+------------------------------+
| romka@adam ✓~/powerlevel10k |
+------------------------------+
```

Note that this prompt is different from the original as it's missing a space after the check mark.

This can be caused by a low-level bug in macOS. See
[this issue](https://github.com/romkatv/powerlevel10k/issues/241).

This can also happen if prompt contains glyphs designated as "wide" in the Unicode standard and your
terminal incorrectly displays them as non-wide. Terminals suffering from this limitation include
Konsole, Hyper and the integrated VSCode Terminal. The solution is to use a different terminal or
remove all wide glyphs from prompt.

#### If the prompt line is shorter than the frame and is not mangled

```text
+--------------------------------+
| romka@adam ✓ ~/powerlevel10k |
+--------------------------------+
```

This can be caused by misconfigured locale. See
[this issue](https://github.com/romkatv/powerlevel10k/issues/251).

### Prompt wrapping around in a weird way

See [cursor is in the wrong place](#cursor-is-in-the-wrong-place).

### Right prompt is in the wrong place

See [cursor is in the wrong place](#cursor-is-in-the-wrong-place).

### Configuration wizard runs automatically every time Zsh is started

When Powerlevel10k starts, it automatically runs `p10k configure` if no `POWERLEVEL9K_*`
parameters are defined. Based on your prompt style choices, the configuration wizard creates
`~/.p10k.zsh` with a bunch of `POWERLEVEL9K_*` parameters in it and adds a line to `~/.zshrc` to
source this file. The next time you start Zsh, the configuration wizard shouldn't run automatically.
If it does, this means the evaluation of `~/.zshrc` terminates prematurely before it reaches the
line that sources `~/.p10k.zsh`. This most often happens due to syntax errors in `~/.zshrc`. These
errors get hidden by the configuration wizard screen, so you don't notice them. When you exit
configuration wizard, look for error messages. You can also use
`POWERLEVEL9K_DISABLE_CONFIGURATION_WIZARD=true zsh` to start Zsh without automatically running the
configuration wizard. Once you can see the errors, fix `~/.zshrc` to get rid of them.

### Some prompt styles are missing from the configuration wizard

If Zsh version is below 5.7.1 or `COLORTERM` environment variable is neither `24bit` nor
`truecolor`, configuration wizard won't offer Pure style with Snazzy color scheme. *Fix*: Install
Zsh >= 5.7.1 and use a terminal with truecolor support. Verify with `print -P '%F{#ff0000}red%f'`.

If the terminal can display fewer than 256 colors, configuration wizard preselects Lean style with
8 colors. All other styles require at least 256 colors. *Fix*: Use a terminal with 256 color support
and make sure that `TERM` environment variable is set correctly. Verify with
`print $terminfo[colors]`.

If there is no UTF-8 locale on the system, configuration wizard won't offer prompt styles that use
Unicode characters. *Fix*: Install a UTF-8 locale. Verify with `locale -a`.

When a UTF-8 locale is available, the first few questions asked by the configuration wizard assess
capabilities of the terminal font. If your answers indicate that some glyphs don't render correctly,
configuration wizard won't offer prompt styles that use them. *Fix*: Restart your terminal and
install [the recommended font](#meslo-nerd-font-patched-for-powerlevel10k). Verify by running
`p10k configure` and checking that all glyphs render correctly.

The minimum screen size at which configuration wizard can function is 55 columns by 21 lines.
However, not all prompt styles are offered at such small screen size as there is simply not enough
space to present them. *Fix*: Resize your terminal to at least 80 columns by 25 lines prior to
running `p10k configure`. Verify with `print ${COLUMNS}x${LINES}`.

### Cannot install the recommended font

Once you download [the recommended font](#meslo-nerd-font-patched-for-powerlevel10k),
you can install it just like any other font. Google "how to install fonts on *your OS*".

### Extra or missing spaces in prompt compared to Powerlevel9k

tl;dr: Add `ZLE_RPROMPT_INDENT=0` and `POWERLEVEL9K_LEGACY_ICON_SPACING=true` to `~/.zshrc` to get
the same prompt spacing as in Powerlevel9k.

When using Powerlevel10k with a Powerlevel9k config, you might get additional spaces in prompt here
and there. These come in two flavors.

#### Extra space without background on the right side of right prompt

tl;dr: Add `ZLE_RPROMPT_INDENT=0` to `~/.zshrc` to get rid of that space.

From [Zsh documentation](
  http://zsh.sourceforge.net/Doc/Release/Parameters.html#index-ZLE_005fRPROMPT_005fINDENT):

> `ZLE_RPROMPT_INDENT <S>`
> 
> If set, used to give the indentation between the right hand side of the right prompt in the line
> editor as given by `RPS1` or `RPROMPT` and the right hand side of the screen. If not set, the
> value `1` is used.
> 
> Typically this will be used to set the value to `0` so that the prompt appears flush with the
> right hand side of the screen.

Powerlevel10k respects this parameter. If you set `ZLE_RPROMPT_INDENT=1` (or leave it unset, which
is the same thing as setting it to `1`), you'll get an empty space to the right of right prompt. If
you set `ZLE_RPROMPT_INDENT=0`, your prompt will go to the edge of the terminal. This is how it
works in every theme except Powerlevel9k.

![ZLE_RPROMPT_INDENT: Powerlevel10k vs Powerlevel9k](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/p9k-vs-p10k-zle-rprompt-indent.png)

Powerlevel9k issue: [powerlevel9k#1292](https://github.com/Powerlevel9k/powerlevel9k/issues/1292).
It's been fixed in the development branch of Powerlevel9k but the fix hasn't yet made it to
`master`.

Add `ZLE_RPROMPT_INDENT=0` to `~/.zshrc` to get the same spacing on the right edge of prompt as in
Powerlevel9k.

*Note:* Several versions of Zsh have bugs that get triggered when you set `ZLE_RPROMPT_INDENT=0`.
Powerlevel10k can work around these bugs when using powerline prompt style. If you notice visual
artifacts in prompt, or wrong cursor position, try removing `ZLE_RPROMPT_INDENT` from `~/.zshrc`.

#### Extra or missing spaces around icons

tl;dr: Add `POWERLEVEL9K_LEGACY_ICON_SPACING=true` to `~/.zshrc` to get the same spacing around
icons as in Powerlevel9k.

Spacing around icons in Powerlevel9k is inconsistent.

![ZLE_RPROMPT_INDENT: Powerlevel10k vs Powerlevel9k](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/p9k-vs-p10k-icon-spacing.png)

This inconsistency is a constant source of annoyance, so it was fixed in Powerlevel10k. You can add
`POWERLEVEL9K_LEGACY_ICON_SPACING=true` to `~/.zshrc` to get the same spacing around icons as in
Powerlevel9k.

*Note:* It's not a good idea to define `POWERLEVEL9K_LEGACY_ICON_SPACING` when using
`p10k configure`.

### Weird things happen after typing `source ~/.zshrc`

It's almost always a bad idea to run `source ~/.zshrc`, whether you are using Powerlevel10k or not.
This command may result in random errors, misbehaving code and progressive slowdown of Zsh.

If you've made changes to `~/.zshrc` or to files sourced by it, restart Zsh to apply them. The most
reliable way to do this is to type `exit` and then start a new Zsh session. You can also use
`exec zsh`. While not exactly equivalent to complete Zsh restart, this command is much more reliable
than `source ~/.zshrc`.

### Transient prompt stops working after some time

See [weird things happen after typing `source ~/.zshrc`](
  #weird-things-happen-after-typing-source-zshrc).

### Cannot make Powerlevel10k work with my plugin manager

If the [installation instructions](#installation) didn't work for you, try disabling your current
theme (so that you end up with no theme) and then installing Powerlevel10k manually.

1. Disable the current theme in your framework / plugin manager.

- **oh-my-zsh:** Open `~/.zshrc` and remove the line that sets `ZSH_THEME`. It might look like this:
  `ZSH_THEME="powerlevel9k/powerlevel9k"`.
- **zplug:** Open `~/.zshrc` and remove the `zplug` command that refers to your current theme. For
  example, if you are currently using Powerlevel9k, look for
  `zplug bhilburn/powerlevel9k, use:powerlevel9k.zsh-theme`.
- **prezto:** Open `~/.zpreztorc` and put `zstyle :prezto:module:prompt theme off` in it. Remove
  any other command that sets `theme` such as `zstyle :prezto:module:prompt theme powerlevel9k`.
- **antigen:** Open `~/.zshrc` and remove the line that sets `antigen theme`. It might look like
  this: `antigen theme powerlevel9k/powerlevel9k`.

2. Install Powerlevel10k manually.

```zsh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>! ~/.zshrc
```

This method of installation won't make anything slower or otherwise sub-par.

### Directory is difficult to see in prompt when using Rainbow style

In Classic style the current working directory is shown with bright white white text on blue
background. The white is fixed and always looks the same but the appearance of "blue" is defined
by your terminal color palette. If it's very light, it's difficult to see white text on it.

There are several ways to fix this.

- Type `p10k configure` and choose a more readable prompt style.
- [Change terminal color palette](#change-the-color-palette-used-by-your-terminal). Try Tango Dark
  or Solarized Dark, or change just the "blue" color.
- [Change directory background color](#set-colors-through-Powerlevel10k-configuration-parameters).
  The parameter you are looking for is called `POWERLEVEL9K_DIR_BACKGROUND`. You can find it in
  in `~/.p10k.zsh`. Uncomment it if it's commented out and try different values.

### Horrific mess when resizing terminal window

When you resize terminal window horizontally back and forth a few times, you might see this ugly
picture.

![Powerlevel10k Resizing Mess](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resizing-mess.png)

tl;dr: This is a bug in Zsh that isn't specific to Powerlevel10k. See [mitigation](#mitigation).

#### Zsh bug

This issue is caused by a bug in Zsh that gets triggered when the vertical distance between the
start of the current prompt and the cursor (henceforth `VD`) changes when the terminal window is
resized. This bug is not specific to Powerlevel10k.

When a terminal window gets shrunk horizontally, there are two ways for a terminal to handle long
lines that no longer fit: *reflow* or *truncate*.

Terminal content before shrinking:

![Terminal Content Before Shrinking](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resize-original.png)

Terminal reflows text when shrinking:

![Terminal Reflows Text When Shrinking](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resize-reflow.png)

Terminal truncates text when shrinking:

![Terminal Truncates Text When Shrinking](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resize-truncate.png)

Reflowing strategy can change the height of terminal content. If such content happens to be between
the start of the current prompt and the cursor, Zsh will print prompt on the wrong line. Truncation
strategy never changes the height of terminal content, so it doesn't trigger this bug in Zsh.

Let's see how the bug plays out in slow motion. We'll start by launching `zsh -df` and pasting
the following code:

```zsh
function pause() { read -s }
functions -M pause 0

reset
print -l {1..3}
setopt prompt_subst
PROMPT=$'${$((pause()))+}left>${(pl.$((COLUMNS-12))..-.)}<right\n> '
```

When `PROMPT` gets expanded, it calls `pause` to let us observe the state of the terminal. Here's
the initial state:

![Zsh Resizing Bug 1](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resize-bug-1.png)

Zsh keeps track of the cursor position relative to the start of the current prompt. In this case it
knows that the cursor is one line below. When we shrink the terminal window, it looks like this:

![Zsh Resizing Bug 2](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resize-bug-2.png)

At this point the terminal sends `SIGWINCH` to Zsh to notify it about changes in the terminal
dimensions. Note that this signal is sent *after* the content of the terminal has been reflown.

When Zsh receives `SIGWINCH`, it attempts to erase the current prompt and print it anew. It goes to
the position where it *thinks* the current prompt is -- one line above the cursor (!) -- erases all
terminal content that follows and prints reexpanded prompt there. However, after resizing prompt is
no longer one line above the cursor. It's two lines above! Zsh ends up printing new prompt one line
too low.

![Zsh Resizing Bug 3](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resize-bug-3.png)

In this case we ended up with unwanted junk content because `VD` has *increased*. When you make
terminal window wider, `VD` can also *decrease*, which would result in the new prompt being printed
higher than intended, potentially erasing useful content in the process.

Here are a few more examples where shrinking terminal window increased `VD`.

Simple one-line left prompt with right prompt. No `prompt_subst`. Note that the cursor is below the
prompt line (hit *ESC-ENTER* to get it there).

![Zsh Prompt That Breaks on Terminal Shrinking 1](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resize-breakable-1.png)

Simple one-line left prompt. No `prompt_subst`, no right prompt. Here `VD` is bound to increase
upon terminal shrinking due to the command line wrapping around.

![Zsh Prompt That Breaks on Terminal Shrinking 2](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/resize-breakable-2.png)

#### Zsh patch

The bug described above has been fixed in [this branch](
  https://github.com/romkatv/zsh/tree/fix-winchanged). The idea behind the fix is to use `sc` (save
cursor) terminal capability before printing prompt and `rc` (restore cursor) to move cursor back
to the same position when prompt needs to be refreshed.

There are two alternative approaches to fixing the bug that may seem to work at fight glance but in
fact don't:

- Instead of `sc`, use `u7` terminal capability to query the current cursor position and then `cup`
  to go back to it. This doesn't work because the absolute position of the start of the current
  prompt changes when text gets reflown.
- Recompute `VD` based on new terminal dimensions before attempting to refresh prompt. This doesn't
  work because Zsh doesn't know whether terminal reflows text or truncates it. If Zsh could somehow
  know that the terminal reflows text, this approach still wouldn't work on terminals that
  continuously reflow text and rapid-fire `SIGWINCH` when the window is being resized. In such
  environment real terminal dimensions go out of sync with what Zsh thinks the dimensions are.

There is no ETA for the patch making its way into upstream Zsh. See [discussion](
  https://www.zsh.org/mla/workers//2019/msg00561.html).

#### Mitigation

There are a few mitigation options for this issue.

- Apply [the patch](#zsh-patch) and [rebuild Zsh from source](
    https://github.com/zsh-users/zsh/blob/master/INSTALL).
- Disable text reflowing on window resize in terminal settings. If your terminal doesn't have this
  setting, try a different terminal.
- Avoid long lines between the start of prompt and cursor.
  1. Disable ruler with `POWERLEVEL9K_SHOW_RULER=false`.
  1. Disable prompt connection with `POWERLEVEL9K_MULTILINE_FIRST_PROMPT_GAP_CHAR=' '`.
  1. Disable right frame with `POWERLEVEL9K_MULTILINE_FIRST_PROMPT_SUFFIX=` and
     `POWERLEVEL9K_MULTILINE_NEWLINE_PROMPT_SUFFIX=` and
     `POWERLEVEL9K_MULTILINE_LAST_PROMPT_SUFFIX=`.
  1. Remove all elements from `POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS`. Right prompt on the last prompt
     line will cause resizing issues only when the cursor is below it. This isn't very common, so
     you might want to keep some elements in `POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS` provided that
     none of them are succeeded by `newline`.

### Icons cut off in Konsole

When using Konsole with a non-monospace font, icons may be cut off on the right side. Here
"non-monospace" refers to any font with glyphs wider than a single column, or wider than two columns
for glyphs designated as "wide" in the Unicode standard.

![Icons cut off in Konsole](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/konsole-non-monospace-font.png)

The last line on the screenshot shows a cut off Arch Linux logo.

There are several mitigation options for this issue.

1. Use a different terminal. Konsole is the only terminal that exhibits this behavior.
2. Use a monospace font.
3. Manually add an extra space after the icon that gets cut off. For example, if the content of
   `os_icon` prompt segment gets cut off, open `~/.p10k.zsh`, search for
   `POWERLEVEL9K_OS_ICON_CONTENT_EXPANSION` and change it as follows:
```zsh
typeset -g POWERLEVEL9K_OS_ICON_CONTENT_EXPANSION='${P9K_CONTENT} '  # extra space at the end
```
4. Use a different icon that is monospace. For example, if Arch Linux logo gets cut off, add
   the following parameter to `~/.p10k.zsh`:
```zsh
typeset -g POWERLEVEL9K_LINUX_ARCH_ICON='Arch'  # plain "Arch" in place of a logo
```
5. Disable the display of the icon that gets cut off. For example, if the content of
   `os_icon` prompt segment gets cut off, open `~/.p10k.zsh` and remove `os_icon` from
   `POWERLEVEL9K_LEFT_PROMPT_ELEMENTS` and `POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS`.

*Note*: [Non-monospace fonts are not officially supported by Konsole](
  https://bugs.kde.org/show_bug.cgi?id=418553#c5).

### Arch Linux logo has a dot in the bottom right corner

![Arch Linux Logo with a dot](
  https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/arch-linux-logo-dot.png)

Some fonts have this incorrect dotted icon in bold typeface. There are two ways to fix this issue.

1. Use a font with a correct Arch Linux logo in bold typeface. For example,
  [the recommended Powerlevel10k font](#meslo-nerd-font-patched-for-powerlevel10k).
2. Display the icon in regular (non-bold) typeface. To do this, open `~/.p10k.zsh`, search for
   `POWERLEVEL9K_OS_ICON_CONTENT_EXPANSION` and remove `%B` from its value.
```zsh
typeset -g POWERLEVEL9K_OS_ICON_CONTENT_EXPANSION='${P9K_CONTENT}'  # not bold
```

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
- [Troubleshooting](#troubleshooting)
  - [Question mark in prompt](#question-mark-in-prompt)
  - [Icons, glyphs or powerline symbols don't render](#icons-glyphs-or-powerline-symbols-dont-render)
  - [Sub-pixel imperfections around powerline symbols](#sub-pixel-imperfections-around-powerline-symbols)
  - [Error: character not in range](#error-character-not-in-range)
  - [Cursor is in the wrong place](#cursor-is-in-the-wrong-place)
  - [Prompt wrapping around in a weird way](#prompt-wrapping-around-in-a-weird-way)
  - [Right prompt is in the wrong place](#right-prompt-is-in-the-wrong-place)
  - [Configuration wizard runs automatically every time Zsh is started](#configuration-wizard-runs-automatically-every-time-zsh-is-started)
  - [Some prompt styles are missing from the configuration wizard](#some-prompt-styles-are-missing-from-the-configuration-wizard)
  - [Cannot install the recommended font](#cannot-install-the-recommended-font)
  - [Extra or missing spaces in prompt compared to Powerlevel9k](#extra-or-missing-spaces-in-prompt-compared-to-powerlevel9k)
    - [Extra space without background on the right side of right prompt](#extra-space-without-background-on-the-right-side-of-right-prompt)
    - [Extra or missing spaces around icons](#extra-or-missing-spaces-around-icons)
  - [Weird things happen after typing `source ~/.zshrc`](#weird-things-happen-after-typing-source-zshrc)
  - [Transient prompt stops working after some time](#transient-prompt-stops-working-after-some-time)
  - [Cannot make Powerlevel10k work with my plugin manager](#cannot-make-powerlevel10k-work-with-my-plugin-manager)
  - [Directory is difficult to see in prompt when using Rainbow style](#directory-is-difficult-to-see-in-prompt-when-using-rainbow-style)
  - [Horrific mess when resizing terminal window](#horrific-mess-when-resizing-terminal-window)
  - [Icons cut off in Konsole](#icons-cut-off-in-konsole)
  - [Arch Linux logo has a dot in the bottom right corner](#arch-linux-logo-has-a-dot-in-the-bottom-right-corner)
