## Thunderbird build scripts

Portable and duplicable build script for building Thunderbird 128.6.0esr on macOS.
Tested on Ventura in January 2025.

### Why:

People usually have only one install of brew per computer. This makes it impossible to use different version of a dependency needed for different projects, or different version of the same project.
Often, if you need to compile on old project (by old, I mean few months!) your brew repository evolved, installed formula has been upgraded and your compilation, that works great few months ago, is broken.

### How to use.

Clone the repository into any folder of your choice. Switch to a branch to choose which version of Thunderbird you'd like to compile.

Launch "./Build on macOS [debug|release]". If the parameter is omitted, debug will be used.

Everything will be downloaded and setup in the chosen folder, including a local installation of brew.

- Local brew is installed in "local_brew"
- MacOS SDK is installed in "MacOSX14.4.sdk"
- Thunderbird sources are installed in "thunderbird-{version}"
- a folder mozbuild is created by the mozilla build system

### Offline use.

All source downloads are stored in an "offline" sub folder.

After a first successful build, the offline folder will contain everything needed to re-run offline.

To restart a compilation from scratch, without any internet access, delete "local_brew", "MacOSX10.11.sdk" and "thunderbird-{version}", keep"offline" and re-launch "Build on macOS".

### Modify/Debug the scripts.

Issue these commands:

- source "./Build on macOS env"

Then, you can issue commands and copy/paste commands from the scripts. For example, you can use the brew command, you can go into the thunderbird sources folder and issue "./mach build", etc.

### Modify Thunderbird.

To help modify Thunderbird, you can use the Xcode project located in the dev folder. One target calls the build script "./Build on macOS".

If you modify some C++ parts, you can use the target nsMsgComposeLib as an example to quickly compile some C++ files from Thunderbird. This will instantaneously check C++ syntax and avoid having to run the long Thunderbird build process to catch mundane errors.

Once you've modified Thunderbird, you can run dev/generate_patches to generate a patch file named "pacthes.txt".

To apply patches from "pacthes.txt", run "dev/apply_patches".

NOTE: Patches are automatically applied when the script "Build on macOS" untars Thunderbird sources.

### Contact.

Feel free to open an issue, even if it's just for a question.
