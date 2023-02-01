# BackupCLI
a simple script that helps you to manage configs, files

# how to set paths
**backupCli** uses a *path file* to *backup files and folders*

you can find an example of *backup paths* under `paths` folder:

- system 

the syntax is simple, only put *file, folder URLs* there:

**NOTE**: *use comments like you'r using them in bash scripts*

```
# bash config
~/.bashrc

# my documents
~/Documents

# root configs
/etc/NetworkManager/NetworkManager.conf
```

# how to config

open `config` file and read comments:

```
declare -A options=(
  # export options
  #----------------------------

  # path to files and folders
  [backup_paths]='paths/system'

  # where to export backups
  [backup_export]='backup'

  # backup root-directory format {backup_export}/format 
  # [default: username-year-month-day--hour-minute-second]
  [backup_format]="${USER}-$(date +%Y-%m-%d--%T|tr ':' '-')"


  # restore options
  #----------------------------

  # where to restore backups on [default: root]
  # backupcli restores the nested folders from root to you'r file, folders
  [backup_restore]="/"
  
  # for example if a file with:
  # /home/devs/.bashrc
  # and backup_restore is "/"
  # backupcli create nest folders under "/"
  # and if its exist uses it
)
```

# usage

**options**:

![options](https://github.com/devshashtag/backupcli/blob/main/screenshots/options.jpg?raw=true)

**export**:

![options](https://github.com/devshashtag/backupcli/blob/main/screenshots/export.jpg?raw=true)

```
do you want to export loaded paths Y/n > y
-------------------------------------------------------------

==> mkdir -p 'backup/devs-2023-02-01--16-38-33/home/devs'

==> cp -ra '/home/devs/.anydesk' 'backup/devs-2023-02-01--16-38-33/home/devs'

==> cp -ra '/home/devs/.mozilla' 'backup/devs-2023-02-01--16-38-33/home/devs'

==> cp -ra '/home/devs/.bash_history' 'backup/devs-2023-02-01--16-38-33/home/devs'

==> cp -ra '/home/devs/.bash_profile' 'backup/devs-2023-02-01--16-38-33/home/devs'

==> cp -ra '/home/devs/.bashrc' 'backup/devs-2023-02-01--16-38-33/home/devs'

==> cp -ra '/home/devs/.dmrc' 'backup/devs-2023-02-01--16-38-33/home/devs'

==> cp -ra '/home/devs/.gitconfig' 'backup/devs-2023-02-01--16-38-33/home/devs'

==> cp -ra '/home/devs/.gnupg' 'backup/devs-2023-02-01--16-38-33/home/devs'

==> cp -ra '/home/devs/.ssh' 'backup/devs-2023-02-01--16-38-33/home/devs'

==> mkdir -p 'backup/devs-2023-02-01--16-38-33/home/devs/.ssr'

==> cp -ra '/home/devs/.ssr/settings.conf' 'backup/devs-2023-02-01--16-38-33/home/devs/.ssr'

==> mkdir -p 'backup/devs-2023-02-01--16-38-33/home/devs/.config'

==> cp -ra '/home/devs/.config/btop' 'backup/devs-2023-02-01--16-38-33/home/devs/.config'

==> cp -ra '/home/devs/.config/fish' 'backup/devs-2023-02-01--16-38-33/home/devs/.config'

==> cp -ra '/home/devs/.config/flameshot' 'backup/devs-2023-02-01--16-38-33/home/devs/.config'

==> cp -ra '/home/devs/.config/chromium' 'backup/devs-2023-02-01--16-38-33/home/devs/.config'

==> cp -ra '/home/devs/.config/mpv' 'backup/devs-2023-02-01--16-38-33/home/devs/.config'

==> cp -ra '/home/devs/.config/nvim' 'backup/devs-2023-02-01--16-38-33/home/devs/.config'

==> mkdir -p 'backup/devs-2023-02-01--16-38-33/home/devs/.config/copyq'

==> cp -ra '/home/devs/.config/copyq/copyq.conf' 'backup/devs-2023-02-01--16-38-33/home/devs/.config/copyq'

==> mkdir -p 'backup/devs-2023-02-01--16-38-33/home/devs/.config/viewnior'

==> cp -ra '/home/devs/.config/viewnior/viewnior.conf' 'backup/devs-2023-02-01--16-38-33/home/devs/.config/viewnior'

==> cp -ra '/home/devs/.config/gtk-2.0' 'backup/devs-2023-02-01--16-38-33/home/devs/.config'

==> cp -ra '/home/devs/.config/gtk-3.0' 'backup/devs-2023-02-01--16-38-33/home/devs/.config'

==> cp -ra '/home/devs/.config/Thunar' 'backup/devs-2023-02-01--16-38-33/home/devs/.config'

==> cp -ra '/home/devs/.config/xfce4' 'backup/devs-2023-02-01--16-38-33/home/devs/.config'

==> cp -ra '/home/devs/.config/mimeapps.list' 'backup/devs-2023-02-01--16-38-33/home/devs/.config'

==> mkdir -p 'backup/devs-2023-02-01--16-38-33/home/devs/.local/share'

==> cp -ra '/home/devs/.local/share/themes' 'backup/devs-2023-02-01--16-38-33/home/devs/.local/share'

==> mkdir -p 'backup/devs-2023-02-01--16-38-33/home/devs/.local/share/fish'

==> cp -ra '/home/devs/.local/share/fish/fish_history' 'backup/devs-2023-02-01--16-38-33/home/devs/.local/share/fish'

==> mkdir -p 'backup/devs-2023-02-01--16-38-33/etc/NetworkManager'

==> cp -ra '/etc/NetworkManager/NetworkManager.conf' 'backup/devs-2023-02-01--16-38-33/etc/NetworkManager'

==> mkdir -p 'backup/devs-2023-02-01--16-38-33/etc/lightdm'

==> cp -ra '/etc/lightdm/lightdm-gtk-greeter.conf' 'backup/devs-2023-02-01--16-38-33/etc/lightdm'
```

**restore**:

for testing restore function set:

```
[backup_restore]="fake-root"
```

![options](https://github.com/devshashtag/backupcli/blob/main/screenshots/restore.jpg?raw=true)
