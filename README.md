# Animated Game Covers for Playnite

Get animated game covers in Playnite's fullscreen mode — plays on focus, returns to static on blur. Works by combining the Extra Metadata Loader addon with a modified TrailerLovers theme and a small AI-assisted XAML patch.

> 📹 **Demo:** *https://www.reddit.com/r/playnite/comments/1u5y4q2/guide_playnite_animated_covers/*
 
---


## How it works

Playnite's Extra Metadata Loader addon supports a file called `VideoMicrotrailer.mp4` per game. This project patches your chosen fullscreen theme's XAML to hook into that file and display it as an animated cover in the game carousel, looping while the game is focused, hidden when it isn't.

The patch is applied via a GitHub Copilot prompt (using Claude Haiku 4.5) that reads your theme and makes the necessary XAML/WPF changes automatically.

---

## Requirements

| Tool | Purpose |
|---|---|
| [Extra Metadata Loader](https://playnite.link/addons.html) | Loads per-game video micro-trailers |
| Extra Metadata Fullscreen Mode Helper | Enables micro-trailer support in fullscreen themes |
| TrailerLovers theme (this repo) | Modified base theme with carousel video support |
| A compatible fullscreen theme | Your preferred theme that supports the above addons |
| [Visual Studio Code](https://code.visualstudio.com/) + GitHub Copilot | Applies the XAML patch to your chosen theme |
| [WebP Converter](https://github.com/iTroy0/WebP-Converter) | Converts SteamGridDB `.webp` files to `.mp4` |

---

## Setup

### 1. Back up your library
Before making any changes, back up your Playnite library and themes folder.

### 2. Install the addons
In Playnite, install both:
- **Extra Metadata Loader**
- **Extra Metadata Fullscreen Mode Helper**
- **TrailerLovers Fullscreen theme**

### 3. Close Playnite fully


### 4. Install the modified TrailerLovers theme
Download the modified theme from this repository, unzip it and place it in your Playnite themes folder:

```
C:\Users\[yourusername]\AppData\Local\Playnite\Themes\Fullscreen
```
Replace the existing TrailerLovers folder with the one from this repo.


### 5. Apply the XAML patch to your theme

Open VS Code and load the Playnite directory:

```
C:\Users\[yourusername]\AppData\Local\Playnite
```

Open the **GitHub Copilot** chat panel and select **Claude Haiku 4.5** as the model.


Copy the prompt from [`patch-prompt.txt`](./patch-prompt.txt) in this repo. Replace the `[THEME]` placeholder with the name of your chosen fullscreen theme, then paste the prompt into the Copilot chat and run it.

Accept the suggested changes and close VS Code.

### 6. Add an animated cover for a game

1. Go to [SteamGridDB](https://www.steamgriddb.com/) and download an animated grid cover for your game (downloaded as `.webp`).
2. Convert the file to `.mp4` using [WebP Converter](https://github.com/iTroy0/WebP-Converter).
3. In Playnite, right-click the game → **Extra Metadata → Open Extra Metadata Directory**.
4. Paste the converted file into that folder and rename it to:

```
VideoMicrotrailer.mp4
```

### 7. Test it

Launch Playnite in fullscreen mode. Focus the game in the carousel, the animated cover should play on loop. Move to another game and it returns to the static cover.

---

## Generating your own animated covers

If a game doesn't have an animated cover on SteamGridDB, you can create one:

- **Online:** Use AI image-to-video tools (e.g. Kling AI, Runway, etc.)
- **Locally:** If you have a GPU with 8 GB+ VRAM, you can run image-to-video models locally

---

## Compatibility

| Theme | Status |
|---|---|
| TrailerLovers | ✅ Confirmed working |
| Ubiquity | ✅ Confirmed working |
| Other themes with Extra Metadata support | Likely compatible via the Copilot patch |

---

## Contributing

If you've confirmed this works with another theme, open a PR or drop an issue and I'll add it to the compatibility table.

---

## License

MIT
