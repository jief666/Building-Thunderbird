## Thunderbird 60.5.3 build scripts

These scripts will build Thunderbird, leaving no trace outside the build folder.

Tested on El Capitan and High Sierra. Doesn't work on Mojave and after because of deprecation of stdlibc++.

Jan 2025 : doesn't compile any more because of brew trying to download from now invalid URLs. Maybe fixable, but who want to compile version 60.5.3 in 2025?

### How to use :

Clone the repository into any folder of your choice.

Launch "./Build on macOS [debug|release]". If the parameter is omitted, debug will be used.

Everything will be downloaded and setup in the chosen folder, including a local installation of brew and a local installation of rust.

- Local brew is installed in "local_brew"
- Local rust is installed in "local_rustc"
- MacOS SDK is installed in "MacOSX10.11.sdk"
- Thunderbird sources are installed in "thunderbird-{version}"

### Offline use

All source downloads are stored in an "offline" sub folder.

After a first successful build, the offline folder will contain everything needed to re-run offline.

To restart a compilation from scratch, without any internet access, delete "local_brew", "local_rustc", "MacOSX10.11.sdk" and "thunderbird-{version}" and re-launch "Build on macOS".

### Modify/Debug the scripts

Issue these commands:

- source "./Build on macOS env"

Then, you can issue commands and copy/paste commands from the scripts. For example, you can use the brew command, you can go into the "thunderbird-60.5.3" sources folder and issue "./mach build", etc.

### Modify Thunderbird

To help modify Thunderbird, you can use the Xcode project located in the dev folder. One target calls the build script "./Build on macOS".

If you modify some C++ parts, you can use the target nsMsgComposeLib as an example to quickly compile some C++ files from Thunderbird. This will instantaneously check C++ syntax and avoid having to run the long Thunderbird build process to catch mundane errors.

Once you've modified Thunderbird, you can run dev/generate_patches to generate a patch file named "pacthes.txt".

To apply patches from "pacthes.txt", run "dev/apply_patches".

NOTE: Patches are automatically applied when the script "Build on macOS" untars Thunderbird sources.

#### Tests

August 2021 : Successfully compile, either with download or offline, under El Capitan and High Sierra.

### Contact

Feel free to open an issue, even if it's just for a question.
