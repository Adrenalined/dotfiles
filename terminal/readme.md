# Windows Terminal

Color schemes for Windows Terminal, loaded as JSON fragments.

## What's here

| Path | Purpose |
|------|---------|
| `fragments/` | Color scheme files (one scheme per file) |

## How it works

Windows Terminal automatically loads any JSON file it finds in:

```
%LOCALAPPDATA%\Microsoft\Windows Terminal\Fragments\<folder>\
```

That folder is a **junction** pointing at `fragments/` in this repo, so any
scheme added here shows up in Terminal, and any edit is tracked by git.

## Setup on a new PC

Run in Command Prompt (no admin needed):

```
mkdir "%LOCALAPPDATA%\Microsoft\Windows Terminal\Fragments"
mklink /J "%LOCALAPPDATA%\Microsoft\Windows Terminal\Fragments\adrenalined" "C:\dev\adrenalined-dotfiles\windows-terminal\fragments"
```

Then restart Windows Terminal (close all windows).

## Adding a new scheme

1. Create a new `.json` file in `fragments/`, wrapped like this:

   ```json
   {
     "schemes": [
       { "name": "Scheme Name", "background": "#000000", ... }
     ]
   }
   ```

2. Restart Windows Terminal.
3. Set it on a profile in `settings.json`: `"colorScheme": "Scheme Name"`

## Notes

- Don't also define the same scheme in `settings.json`; keep the fragment as
  the only copy.
- Fragments are only read at startup, so changes need a restart.