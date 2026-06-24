---
title: '## Installing OSS-DBS v2[OS...'
---

````
## Installing OSS-DBS v2

[OSS-DBS v2]() is an electric field and pathway activation modeling platform used by Lead-DBS. It is installed automatically in the background (via conda) the first time you select it in the Lead-DBS GUI. If the automatic installation succeeds, no further steps are needed.

{% hint style="warning" %}
The automatic conda-based installation may fail in the following cases:
- **Windows**: `git` is not installed (see prerequisites above)
- **All platforms**: a conflicting Anaconda installation is present on the system
- **All platforms**: firewall policies block the download

In these cases, follow the manual installation instructions below.
{% endhint %}

### Manual installation via pre-built binaries (Windows only)

If the automatic conda-based installation of OSS-DBS fails, you can link a pre-built binary bundle manually:

1. Download the OSS-DBS binary bundle:
   [ossdbs_bundle.zip]()
2. Extract the zip to a permanent location on your system, e.g. `C:\software\ossdbs_bundle`.
3. In the Lead-DBS GUI, go to `Preferences` -> `Edit Preferences File`
4. Add the following line at the end of the file:
```matlab
prefs.oss_bin_path = 'C:\software\ossdbs_bundle';
```
5. Lead-DBS will use the binary bundle instead of the conda environment.

### Manual installation via pip (Linux and macOS)

If the automatic installation fails on Linux or macOS, you can install OSS-DBS via pip:

1. Run the following commands in your terminal:
```bash
python3 -m venv ossdbs-env
source ossdbs-env/bin/activate
pip install ossdbs
```
2. In the Lead-DBS GUI, go to `Preferences` -> `Edit Preferences File` and add the following line at the end, replacing the path with your actual venv location:
```matlab
prefs.ext_oss_env = '/home/username/ossdbs-env/';
```

{% hint style="info" %}
On Ubuntu 24.04 and later, a virtual environment is required for pip installs (enforced via PEP 668). The commands above create and activate one before installing. You can confirm the correct path by activating the environment (`source ossdbs-env/bin/activate`) and running `which ossdbs` — use the output path without the trailing `/bin/ossdbs`.
````
