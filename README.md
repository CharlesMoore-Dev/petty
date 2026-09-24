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
- [ ] Binaries (`wezterm` → `petty`, `wezterm-gui` → `petty-gui`, ...)
- [ ] macOS app bundle (`peTTY.app`, bundle ID, icon)
- [ ] Config file and paths (`~/.config/petty/petty.lua`)
- [ ] Window titles, about dialog, and user-visible strings
- [ ] Opinionated defaults and passive-aggressive error messages

## Building

Requires a Rust toolchain ([rustup](https://rustup.rs)) and, on macOS, the
Xcode Command Line Tools.

```sh
git clone --recurse-submodules git@github.com:CharlesMoore-Dev/petty.git
cd petty
cargo build --release
./target/release/wezterm
```

Until the rename lands, the binaries are still called `wezterm`. peTTY is
aware of this and is not happy about it.

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
