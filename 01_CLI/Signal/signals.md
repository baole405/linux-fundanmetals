# Signals & Control Keys
- `Ctrl+C` sends SIGINT: stop the current program (try it on `yes`).
- `Ctrl+D` sends EOF/SIGQUIT to bash: exit the shell session (same as `exit`); many programs ignore SIGQUIT.
- SIGTERM: default from `kill <pid>`; asks a process to stop cleanly.
- SIGKILL: `kill -9 <pid>` forces an immediate stop without cleanup.
- List available signals with `kill -l`.
- Handy line shortcuts: `Ctrl+A` start, `Ctrl+E` end, `Ctrl+K` delete to end, `Ctrl+U` delete to start, `Ctrl+Y` yank back, `Ctrl+L` clear.
