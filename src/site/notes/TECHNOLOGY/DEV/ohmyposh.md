---
dg-home: false
dg-publish: true
tags:
  - Projects
  - code
date_created: 2024-04-28 11:32:43 am
date_modified: 2024-04-28T11:32:50
date_completed: 2024-04-29T18:20:00
---
[[TRACK/Current Projects\|CURRENT PROJECTS]]

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