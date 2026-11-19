<p align="center"><i> note: that's plant and alexandria (as in the Library of Alexandria) merged together </i></p>
 
<p align="center">
  <img src="image.jpg" alt="New Splash"/>
</p>

<p align="center"> A desktop app for keeping track of your houseplants, built with C++17 and Qt. Add plants, log their care, and check weather conditions, all stored locally on your machine. </p>

## Current To-do List
- Replace deprecated HTML scraping with proper Weather-based API capabilities; there's better ways to collect the information needed for this app.
   - Update how plant data behaves as a consequence of these changes (e.g. how it interacts with weather changes).
- Deprecate Login feature; there's absolutely no need for it.

# For current deployment:

## What You'll Need
 
- A C++17-compatible compiler
- CMake 3.16 or newer
- Qt 5 or Qt 6 with these modules:
  - Qt Widgets
  - Qt Network
  - Qt Multimedia
- Platform tools:
  - **Windows:** Visual Studio or MinGW
  - **macOS:** Xcode Command Line Tools
  - **Linux:** A C++ compiler and Qt development packages
The build scripts reference Qt 6.5, so that's the safest choice.
 
## Getting Started
 
### macOS
 
```bash
git clone https://github.com/realtafaitel/Plant-Health-Plus-Continued.git
cd Plant-Health-Plus-Continued
chmod +x build.sh
./build.sh
```
 
The script finds Qt, configures CMake, builds the project, and bundles the Qt frameworks with `macdeployqt`.
 
Then launch the app:
 
```bash
open PlantHealthPlus/PlantHealthPlus.app
```
 
### Windows
 
From a Command Prompt at the repository root:
 
```bat
build.bat
```
 
The script checks for CMake and Qt, configures and builds the project, and bundles the Qt runtime dependencies with `windeployqt`.
 
### Manual CMake Build
 
```bash
cmake -S PlantHealthPlus -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build --config Release
```
 
On macOS and Windows, if Qt isn't found automatically, set `CMAKE_PREFIX_PATH` to the directory containing your Qt CMake package config.
 
## Running the Tests
 
The test suite lives in `PlantHealthPlus/tests`:
 
```bash
cd PlantHealthPlus/tests
chmod +x run_tests.sh
./run_tests.sh
```
 
It covers:
 
- `PlantManager`
- `PlantCard`
- `LogbookManager`
- `RangeIndicator`
- `UserManager`
- General application behavior
Test executables are built into the test directory or its build output directory.
 
## Where Your Data Lives
 
Everything is saved locally as JSON files in Qt's platform-specific application-data location:
 
- `users.json` holds account records
- `plants_<username>.json` holds each user's plant collection
- Preferences, including notification volume, are saved with the account data
Typical locations:
 
- **Windows:** Qt application-data directory
- **macOS:** `~/Library/Application Support`
- **Linux:** Qt application-data directory
## Good to Know
 
- **Weather** is pulled by scraping HTML, not from a documented weather API. If the source website changes its markup, the selectors may break.
- **Accounts** use local authentication with JSON storage. It isn't meant to replace a security-reviewed authentication or database system.
- **vcpkg.json** is included, but the current CMake configuration mainly uses Qt components directly.
## Credits
 
**Original contributors:**
 
- Jefffrey Hansen
- Tal Faitelson
- Daniel Hernandez Vigil

**Current contributor:** Tal Faitelson
