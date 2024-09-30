---
{"dg-publish":true,"permalink":"/technology/dev/ohmyposh/","tags":["Projects","code"],"created":"2024-04-28 11:32:43 am","updated":"2024-04-28T11:32:50"}
---

[[TECHNOLOGY/DEV/RaspberryPI Setup\|RaspberryPI Setup]]

https://ohmyposh.dev/docs/installation/prompt

nerd fonts: https://www.nerdfonts.com/font-downloads

- [x] ohmyposh 🛫 2024-04-28 ✅ 2024-04-28

```json
{
//filename: psf-dark.omp.json
  "$schema": "https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/schema.json",

  "blocks": [

    {

      "alignment": "left",

      "segments": [

        {

         // "background": "#0A703E",

          "foreground": "#ffffff",

          "style": "plain",

          "template": " \uf0e7 ",

          "type": "root"

        },

        {

          "background": "#BF231D",

          "foreground": "#ffffff",

          "style": "plain",

          "template": " {{ .Icon }} ",

          "type": "os"

        },

        {

          "background": "#0A703E",

          "foreground": "#ffffff",

          "style": "plain",

          "template": "{{ .UserName }} ",

          "type": "session"

        },

        {

          //"background": "#256C9D",

         // "background": "#BF231D",

         "background": "#0A703E",

          "foreground": "#ffffff",

          "properties": {

            "folder_icon": "\uf115",

            "folder_separator_icon": " \ue0b1 ",

            "max_depth": 2,

            "style": "agnoster_short"

          },

          "style": "plain",

          "template": " {{ .Path }} ",

          "type": "path"

        },

        {

        // "background": "#256C9D",

          "background": "#0A703E",

          "foreground": "#ffffff",

          "properties": {

            "branch_max_length": 30,

            "fetch_stash_count": false,

            "fetch_status": true,

            "fetch_upstream_icon": true

          },

          "style": "plain",

          "template": "[ {{ .UpstreamIcon }}{{ .HEAD }}{{if .BranchStatus }} {{ .BranchStatus }}{{ end }}{{ if .Working.Changed }} \uf044 {{ .Working.String }}{{ end }}{{ if and (.Working.Changed) (.Staging.Changed) }} |{{ end }}{{ if .Staging.Changed }} \uf046 {{ .Staging.String }}{{ end }}{{ if gt .StashCount 0 }} \ueb4b {{ .StashCount }}{{ end }} ]",

          "type": "git"

        },

        {

         "background": "#256C9D",

         // "background": "#0A703E",

          "foreground": "#ffffff",

          "powerline_symbol": "\ue0b0",

          "style": "plain",

          "template": " \ue235 {{ if .Error }}{{ .Error }}{{ else }}{{ if .Venv }}{{ .Venv }} {{ end }}{{ .Full }}{{ end }} ",

          "properties": {

            "text": "\ue0b0"

          },

          "type": "python"

        },

        {

          "foreground": "#256C9D",

        //  "background": "#0A703E",

          "style": "plain",

          "template": "\ue0b0 ",

          "type": "text"

        }

      ],

      "type": "prompt"

    }

  ],

  "version": 2

}
```

## Linux setup

https://www.youtube.com/watch?v=nGHgyPLi7UM

```
mkdir ~/bin
```

```
curl -s https://ohmyposh.dev/install.sh | bash -s -- -d ~/bin
```

```
eval "$(oh-my-posh init bash)"
```

```
sudo nano ~/.bash_profile
```

download themes

```
cd bin
```

```
git clone https://github.com/JanDeDobbeleer/oh-my-posh.git posh-themes
```

change psfrago to alpha, etc.
```
export PATH=$PATH:/home/psfrago/bin

POSH_THEME="blueish"

eval "$(oh-my-posh init bash --config /home/psfrago/bin/posh-themes/themes/$POSH_THEME.omp.json)"

#blue-owl
#atomic
#blue-owl
#blueish
#montys
#quick-term

```

### RENDER
```
 . ~/.bash_profile
```

## Windows setup


find path
```
$PROFILE
```

run as administrator powershell

```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
```

```
notepad $PROFILE
```

```
oh-my-posh init pwsh | Invoke-Expression
& ([ScriptBlock]::Create((oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\blue-owl.omp.json" --print) -join "`n"))
```

render path
```
. $PROFILE
```
## THEMES
https://ohmyposh.dev/docs/themes

- atomic
- blue-owl
- blueish
- montys
- paradox
- pixelrobots
- powerline
- quick-term
