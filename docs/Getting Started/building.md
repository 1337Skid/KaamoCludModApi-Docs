# Building from source

If you want to compile KaamoClubModApi yourself rather than using a prebuilt release this tutorial is for you.

---

## Prerequisites

- Windows
- [xmake](https://xmake.io/)

Install xmake from [xmake.io](https://xmake.io/guide/quick-start.html) or via `winget`:

```bash
winget install -e --id Xmake-io.Xmake
```

---

## Clone the repository

```bash
git clone https://github.com/1337Skid/KaamoClubModApi.git
cd KaamoClubModApi
```

---

## Build

```bash
xmake
```

That's it, xmake will compile everything and output the proxy dll and the modding api 

---

## Output

After building, grab the output files located in the `build/` folder and drop them into your game folder per the [Installation](installation.md) guide.
