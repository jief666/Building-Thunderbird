## Thunderbird build scripts

These scripts will build Thunderbird, leaving no trace outside the build folder.

### How to use :

Clone the repository in any folder of choice.

Launch "./Build on macOS [debug|release]". If parameter is omitted, debug will be used.

Everything will be downloaded and setup in the chosen folder, including a local installation of brew and a local installation of rust.

Local brew in installed "local_brew"
Local rust in installed "local_rustc"
MacOs SDK is installed in "MacOSX10.11.sdk" folder
Thunderbird sources are installed in "thunderbird-{version}"

### Offline use

All source downloads are stored in a "offline" sub folder.

After a first successful build, the offline folder will contain everything needed to re-run offline.

To restart a compilation from scratch, without any internet access, delete "local_brew", "local_rustc", "MacOSX10.11.sdk" and "thunderbird-{version}" and re-launch "Build on macOS".

### Debug

Issue these commands :

- . "./Build on macOS env"

- SCRIPT_DIR=$(pwd)

Then, you can issue commands and copy/paste commands from the scripts. For example, you can use the brew command, you can go into thunderbird folder and issue ./mach build, etc.
