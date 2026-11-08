# Green Audio Tabs

A tiny userChrome.css tweak that paints a Firefox tab green while it's playing
sound.

It leans on the `[soundplaying]` attribute Firefox already sets on noisy tabs,
which means there's no add-on to install and nothing running in the background.

## Setup

1. Open `about:config`, search for
`toolkit.legacyUserProfileCustomizations.stylesheets`, and set it to `true`.
Without this Firefox ignores the file entirely.

2. Open `about:profiles` and click "Open Folder"
next to the **Root Directory** of the profile you're using — not the Local
Directory, which only holds cache and temporary files. An easy way to tell
them apart: the Root path contains `Roaming`, the Local one contains `Local`.
On Windows the Root path looks roughly like:

```
C:\Users\<you>\AppData\Roaming\Mozilla\Firefox\Profiles\xxxx.default-release
```

3. Create a folder named `chrome` inside the profile if
it isn't there, and put `userChrome.css` in it:

```
...\Profiles\<profile>\chrome\userChrome.css
```

4. Restart Firefox.

## Customizing

The color sits at the top of `userChrome.css`:

```css
--playing-green: #09b01c;
```

The active tab uses a slightly darker green so it doesn't blend into the
background tabs. There's also an optional block near the bottom for muted tabs
— delete it if you only want green while sound is actually playing.

## Notes

Desktop Firefox only. If a Firefox update ever breaks it, Mozilla most likely
renamed the internal tab classes (`.tab-background` and the like), and the
selectors would need a quick update to match.
