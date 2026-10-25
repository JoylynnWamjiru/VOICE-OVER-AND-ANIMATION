# Running on Windows

Tested on Windows 11 with Git Bash. Known quirks and their workarounds:

| Quirk | Workaround |
|---|---|
| `bash` launched from PowerShell is WSL with no distro | run the `.sh` scripts from **Git Bash**; if a script still fails, launch `node scripts/render.js frames …` workers directly and run the ffmpeg mix/encode from PowerShell |
| faster-whisper `base` drifts into gibberish after ~30 s | use `small`, and transcribe with `language="en"` and `condition_on_previous_text=False` |
| Unicode errors printing transcripts | `set PYTHONIOENCODING=utf-8` (PowerShell: `$env:PYTHONIOENCODING="utf-8"`) |
| `fill_template.py` can't symlink `vendor/` | handled: it falls back to a directory junction (`mklink /J`) |
| `contact-sheet.sh` glob finds no files | tile stills with an ffmpeg concat list: `ls *.jpg \| sed "s/.*/file '&'/" > l.txt; ffmpeg -f concat -safe 0 -i l.txt -vf "scale=360:-1,tile=6x5" -frames:v 1 contact.jpg` |
| Long encodes (160 s ≈ 10+ min on 4 cores) | run in the background; never start a second encode into the same file |
| Low disk space | `pip cache purge`; delete `work/frames/` after a successful encode |
