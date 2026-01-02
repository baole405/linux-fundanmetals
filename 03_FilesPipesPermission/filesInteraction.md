# Files, Pipes, and Permissions

## 1. Interacting with Files
- `less`: view files with paging; `q` quits, `/` searches, `n`/`N` cycle matches, space/`b` page nav; prefer over `more`.
- `man`: uses `less`; `man <cmd>` for manuals; `--help` is shorter when available.
- `cat`: print entire file to stdout; best for short files.
- `head`/`tail`: first/last 10 lines by default; `-n <count>` custom lines; `tail -f` follows updates live.
- `mkdir`: create directories; `-p` builds parent paths; `cd` to enter new folder.
- `touch`: create empty files or just update modified/accessed time.
- `rm`: delete files; `-r` for directories, `-f` to skip prompts; avoid `rm -rf /`; consider `trash-cli` for safety.
- `cp`: copy files; `cp src dest` or `cp src dir/`; `-R` copies directories recursively.
- `mv`: move or rename files/directories.
- `tar`: archive; `tar -cf archive.tar files...`; add `-z` for gzip (`.tar.gz`); extract with `tar -xzf archive.tar.gz -C dest/`.

