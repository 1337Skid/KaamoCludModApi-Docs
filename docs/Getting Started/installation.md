# Installation

Having KaamoClubModApi running only takes a minute.

---

## Step 1 - Download the latest build

Go to the [Releases](https://github.com/1337Skid/KaamoClubModApi/releases) tab and download the latest zip named `kaamoclubmodapi.zip`

Alternatively, check the [GitHub Actions page](https://github.com/1337Skid/KaamoClubModApi/actions) tab if you want to download the really latest build (You need a github account).

---

## Step 2 - Drop files into the game folder

Extract the zip and drag everything into your **Galaxy On Fire 2 HD folder** (the folder containing the game's `.exe`).

Your game folder should look something like this afterwards:
```
Galaxy On Fire 2 HD/
├── GOF2.exe <- the new GOF2.exe from the `kaamoclubmodapi.zip`
├── GOF2Launcher.exe
├── d3d9.dll <- proxy dll (will load the modding api) from the zip
├── kaamoclubmodapi.dll <- the modding api core from the zip
├── fmod*.dll
├── steam_api.dll
├── installscript.vdf
├── DefaultInputMapping.ini
├── data/
├── directxsetup/
└── mods/ <- the mods that will be loaded
```

---

## Step 3 - Launch the game

Start the game normally. The proxy dll will load automatically and inject the modding api. Any mods in the `mods/` folder will be loaded at startup. You should see a console pop up
