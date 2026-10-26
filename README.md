# PicGo Native for Windows

Native Windows x64 builds of [PicGo](https://github.com/Molunerfinn/PicGo),
compiled from PicGo's unchanged source with
[NativeBoat](https://github.com/XTSoftwareLabs/nativeboat-release). The
executable runs without Chromium, WebView2 or Node.js.

Download a build from the [releases](../../releases) page.

## How it is built

The [Build native PicGo](.github/workflows/build.yml) workflow:

1. checks out a PicGo tag (default `v3.0.3`) from `Molunerfinn/PicGo`,
2. sets up Node.js and pnpm, which NativeBoat uses to install the project's
   dependencies,
3. compiles the project with the
   [NativeBoat Build action](https://github.com/XTSoftwareLabs/nativeboat-action),
4. uploads the executable, a ZIP of the full output folder and
   `SHA256SUMS.txt` as a workflow artifact.

It runs on pushes to `main` and on pull requests, and publishes nothing.

## Releasing

Run the [Release native PicGo](.github/workflows/release.yml) workflow from
the Actions tab. Set `picgo-ref` to the PicGo tag to build and
`nativeboat-version` to a NativeBoat release tag or `latest`. It runs the build
above, then publishes its files to a release named after the PicGo tag.
Running it again for the same tag replaces that release's files.
