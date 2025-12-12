# Assets inventory

## JetBrains Mono Nerd Font
- **Location:** `assets/JetBrainsMonoNerdFont`
- **Variants:** Mono, Proportional, Ligature-free (NL), and Propo families covering Thin, ExtraLight, Light, Regular, Medium, SemiBold, Bold, ExtraBold, and matching italic styles for each weight.
- **Contents:** Full Nerd Font builds (`JetBrainsMonoNerdFont*.ttf`, `JetBrainsMonoNLNerdFont*.ttf`, `JetBrainsMonoNLNerdFontMono*.ttf`, `JetBrainsMonoNLNerdFontPropo*.ttf`).
- **Source:** [Nerd Fonts](https://www.nerdfonts.com/) release of JetBrains Mono with icon glyphs included.
- **License:** Distributed under the SIL Open Font License via Nerd Fonts.
- **Integration notes:** Embedded via `include_bytes!` in `src/ui/fonts.rs` and registered for both proportional and monospace families so the entire UI, including icon glyphs, renders with JetBrains Mono Nerd Font by default.

## Nerd Font Icons
- **Location:** Included inside the JetBrains Mono Nerd Font files above.
- **Usage:** UI leverages Nerd Font glyphs for provider branding (e.g., GitHub `U+F408`, GitLab `U+F296`) and other icons rendered directly from the font stack.
- **Fallbacks:** None required; the default font families already include the icon-capable font files.
