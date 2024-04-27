# How to create shortcut to run command on Ubuntu

1. Go to directory which contain all shortcuts:

* For system-wide access : `/usr/share/applications`
* For user-specific access : `~/.local/share/applications`

```shell
cd /usr/share/applications/
# or
cd ~/.local/share/applications/
```

2. Create shortcut for your app:
```shell
nano your-app.desktop
```

3. Insert data below into file:
```shell
[Desktop Entry]
Name=Your-app-name
Comment=
Exec=/full/path/to/your/executable/file-command.sh

# use this
Terminal=false
# OR this
Terminal=true

Type=Application
Icon=/full/path/to/your-icon.png
```

### Short description for every property:
* **[Desktop Entry]** - Every desktop entry starts with this keyword.
* **Name** : Name of the application.
* **Exec** : Path of the executable file.
* **Type** : Set it to application
* **Icon** : Path of the application logo.
* **Comment** : A brief description of the application.
* **Terminal** : Set it to false if the application doesn't require terminal.
* **StartupNotify** : Set it to true to show a notification when the application starts.

4. Refresh desktop environment:
```shell
sudo update-desktop-database && update-desktop-database ~/.local/share/applications
```



## Sample

```shell
[Desktop Entry]
Name=Translator
Comment=My terminal translator

#Exec=/full/path/to/trans_run.sh
Exec=gnome-terminal -- /bin/bash -c "source /full/path/to/trans_func.sh && trans"

Icon=/full/path/to/icon.png

Terminal=true

Type=Application
```