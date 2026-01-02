## 2. Wildcards and Replacements
- `*` matches any string; `?` matches exactly one char; ranges like `[1-5]`; negate with `[^...]`; shell expands these before running the command.
- Examples: `rm *.txt`, `ls file?.txt`, `ls file[1-5].txt`.
- Brace expansion to create/echo many items: `touch file{4,5,6}.txt`; `touch {Aisha,Lanie,Joumana,Krista}-profile.txt`.
- Numeric/alpha ranges: `touch file{0..10}.txt`; `echo {a..z}`, `{z..a}`; stepped `echo {0..100..2}` or `{100..0..5}`; combos `echo {a..z}{1..5}`.
