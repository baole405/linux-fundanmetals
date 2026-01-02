# Users, Groups, and Permissions

## Why it matters (DevOps angle)
- Linux is multi-user; services often run as their own users to reduce blast radius (principle of least privilege).
- Keep humans and services separate: e.g., `deploy` user for CI pipelines, `nginx` user for web server, your own account for admin work.

## Users and sudo
- `whoami` shows the current user. `/etc/passwd` lists all users (humans + service accounts).
- `sudo <cmd>` runs one command as root (preferred). `su` or `sudo su` drops you into a root shell, powerful but risky.
- Example: installing packages from your workstation node: `sudo apt-get install htop`. Avoid staying in root; exit with `CTRL+D`.

## Groups and sudoers
- Groups give shared permissions to many users at once (e.g., a `deployers` group that can push releases).
- Add a user to a group: `sudo usermod -aG sudo brian` (makes brian a sudoer). Check with `groups brian`.
- Practical DevOps example: give on-call engineers log-read access without write: `sudo usermod -aG logreaders alex`; set log dir to group-readable (see chmod below).

## Ownership (chown)
- Files/directories belong to a user and a group. `ls -l` shows `owner:group` and permission bits.
- Change ownership: `sudo chown ubuntu:ubuntu /hello` or `sudo chown app:devops /var/log/myapp` so app writes logs and DevOps can read.

## Permissions (chmod)
- Format: `<type><user><group><other>` where `r`=read, `w`=write, `x`=execute. `-rw-rw-r--` means user/group can read+write; others read-only.
- Symbolic: `chmod u=rw,g=r,o= secret.txt` (640). Add/remove with `chmod +x deploy.sh` or `chmod g-w shared.conf`.
- Numeric: add 4 for read, 2 for write, 1 for execute per role. Examples: `644` = user read/write, group read, others read (default for files); `755` = user rwx, group rx, others rx (common for scripts/dirs); avoid `777`.
- Tailored example: app binary owned by `app:devops` with execute for all, write for app only: `sudo chmod 755 /opt/myapp/bin/start.sh`. Logs readable by DevOps group only: `sudo chmod 640 /var/log/myapp/app.log`.

## Handy checks
- `ls -l <path>`: see type/permissions/owner/group.
- `groups` or `groups <user>`: see group membership.
- `id <user>`: see uid/gid details.
- `sudo -l`: see what you can run with sudo.
