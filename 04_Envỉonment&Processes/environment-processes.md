# Environments and Processes

## Environment variables
- `printenv` lists your session variables (PATH, USER, HOME, AWS_PROFILE, etc.).
- Inline override for one command: `USER=brian echo "hi $USER"`; original session stays unchanged. Handy for one-offs like `ENV=dev npm run build`.
- Session-only variable: `GREETING=hello` then `echo $GREETING`; disappears when the shell closes.
- Persistent: put exports in `~/.bashrc` then `source ~/.bashrc`. Common pattern in `~/.bash_profile`:

```bash
if [ -f ~/.bashrc ]; then
    source ~/.bashrc
fi
```

- DevOps examples: prepend CLI tools to PATH `export PATH="$HOME/.local/bin:$PATH"`; set kube context `export KUBECONFIG=~/.kube/prod`; one-off cloud call `AWS_PROFILE=prod aws s3 ls`.

## Processes
- `ps` shows your running processes; each has a pid and owner. Background a task with `sleep 100 &` then confirm via `ps`.
- Full view/search: `ps aux | grep nginx` to locate service pids during debugging.
- Kill gently with `kill -s SIGTERM <pid>`; force with `kill -9 <pid>` if hung.
- Foreground vs background: append `&` to run in background; pause with `CTRL+Z`, list via `jobs`, resume in background `bg %1`, bring to foreground `fg %1`.
- DevOps examples: tail logs while you continue deploying `tail -f /var/log/myapp/app.log &`; if a deploy script wedges, find its pid with `ps aux | grep deploy.sh` and `kill` it instead of rebooting.
