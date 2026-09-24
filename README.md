<p align="center">
  <img src="assets/petty/petty-icon.png" alt="peTTY icon" width="256">
</p>

<h1 align="center">peTTY</h1>

<p align="center"><em>A GPU-accelerated terminal emulator that holds grudges.</em></p>

---

peTTY is a terminal emulator for people who have been paged at 3 AM, told
"it's probably DNS," and were right about it being DNS.

It remembers the command you ran without `sudo`. It remembers the time you
typed `rm -rf` into the wrong tab. It will not bring these things up unless
provoked. It will be provoked.

## Features

- **Fast.** Very fast. Faster than your change-approval process.
- **Scrollback.** Everything you've ever done, kept forever, for reference.
- **Tabs and splits.** So you can ignore several servers at once.
- **Ligatures.** Your `->` looks great while prod is on fire.
- **Side-eye.** Included at no extra charge.

## Status

peTTY is a fork of [WezTerm](https://github.com/wezterm/wezterm), being
rebuilt as its own application: new name, new icon, and a worse attitude.

Rename in progress:

- [x] Fork, icon, README
- [x] Binaries (`petty`, `petty-gui`, `petty-mux-server`)
- [x] macOS app bundle (`peTTY.app`, `dev.charlesmoore.petty`, new icon)
- [x] Config file and paths (`~/.config/petty/petty.lua`, with `wezterm.lua` fallback)
- [x] macOS menu bar, quit dialogs, and default pane title
- [ ] Linux and Windows packaging (rpm, deb, AppImage, Flatpak, installer)
- [ ] Opinionated defaults and passive-aggressive error messages

## Building

Requires a Rust toolchain ([rustup](https://rustup.rs)) and, on macOS, the
Xcode Command Line Tools.

```sh
git clone --recurse-submodules git@github.com:CharlesMoore-Dev/petty.git
cd petty
cargo build --release
./target/release/petty start
```

To build `peTTY.app` on macOS, run `bash ci/deploy.sh` after the build.

## Configuration

peTTY looks for its config in this order and uses the first one it finds:

1. `$PETTY_CONFIG_FILE` (or the older `$WEZTERM_CONFIG_FILE`)
2. `~/.petty.lua`, then `~/.config/petty/petty.lua`
3. `~/.wezterm.lua`, then `~/.config/wezterm/wezterm.lua`

An existing WezTerm config keeps working unchanged. In Lua, `require "petty"`
and `require "wezterm"` return the same module, so either spelling works.

## Deliberately still called WezTerm

These keep the old name on purpose, so shells, editors, and plugins keep
working:

- `TERM_PROGRAM=WezTerm` and the `wezterm` terminfo entry, which tools use to
  detect features like inline images and hyperlinks
- `WEZTERM_*` environment variables inside panes, which the shell integration
  uses
- The `wezterm` Lua module, now also available as `petty`
- Internal Rust crate names, to keep merging from upstream painless

The update checker is off by default because it would advertise WezTerm
releases.

## Staying in sync with upstream

```sh
git remote add upstream https://github.com/wezterm/wezterm.git
git fetch upstream
git merge upstream/main
```

## Credit where it's due

peTTY exists because [Wez Furlong](https://github.com/wez) and the WezTerm
contributors built an excellent terminal. All the good parts are theirs; the
attitude is ours. For WezTerm's own documentation, see
[wezterm.org](https://wezterm.org/).

## License

MIT, same as upstream. The original WezTerm copyright notice is preserved in
[LICENSE.md](LICENSE.md).
