# SAKE: Simple ASCII Kodi Emulator
[![License](https://img.shields.io/github/license/retrospect-addon/kodi.emulator.ascii?color=brightgreen)](LICENSE.md)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=retrospect-addon%3Akodi.emulator.ascii&metric=alert_status)](https://sonarcloud.io/dashboard?id=retrospect-addon%3Akodi.emulator.ascii)
[![Python](https://img.shields.io/badge/python-2.7%20%7C%203.6-blue?logo=python)](https://kodi.tv/article/attention-addon-developers-migration-python-3)

![alt text](sake.png "Simple ASCII Kodi Emulator")

## _SAKE_: your favourite 'drink' for debugging and developiong Kodi Python add-ons
SAKE can help you to debug and develop Kodi Python add-ons. It contains a set of libraries that try to mimic the functionality of the corresponding Kodi modules:

| Module        | Purpose                   |
|---------------|---------------------------|
|`xbmc`         | General functions on Kodi |
|`xbmcaddon`    | Kodi’s addon class        |
|`xbmcgui`      | GUI functions on Kodi.    |
|`xbmcplugin`   | Plugin functions on Kodi. |


Not all libraries are present and certainly not all methods are implemented. Currently missing are:

| Module        | Purpose                   |
|---------------|---------------------------|
|`xbmcvfs`      | Virtual file system functions on Kodi.|
|`xbmcdrm`      | Kodi’s DRM class          |

Feel free to contribute to the completion using Pull Requests for this repository.

### Using _SAKE_
In order to use _SAKE_ for development Kodi add-ons, you will need to include its path the the Python paths. Eiter via:

```Python
sys.path.append('<path to SAKE>')
```

Or by appending the _SAKE_ path to the Python path environment variable: `PYTHONPATH`

### Configuration
_SAKE_ requires you to run with your add-on as the main _working directory_. Running it outside of that directory will fail. 

If your add-on is in a subfolder of Kodi's `addons` folder, you are done. _SAKE_ will try to find its own way and determine what your Kodi path is and where your profile is stored. However, if you are running it standalone, so without Kodi at all, or if _SAKE_ got 'drunk' and lost its way, you can always specify some directions using environment variables as follows:

| Environment Variable | Description |
|----------------------|-------------|
| `KODI_HOME`          | If specified, will force _SAKE_ to look at that path for Kodi's home path. |
| `KODI_ACTIVE_PROFILE` | _SAKE_ will asume that you don't have any Kodi profiles, but in case  you have, you can specify what profile to use for the add-on settings. |
| `KODI_INTERACTIVE`   | Normally, _SAKE_ will try to interact with you: Whenever there should be a dialog shown within Kodi, _SAKE_ will present you with an ASCII version and wait for a response. You can disable this by setting this environment variable to "0". _SAKE_ will not disturb you and will continue. However, _SAKE_ will answer those dialogs for you and that **might result in unwanted actions**, but it might come in handy while running unit tests.|
| `KODI_STUB_VERBOSE` | If set to "1" will make _SAKE_ a bit more verbose. |
