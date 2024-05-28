---
{"dg-publish":true,"permalink":"/technology/obsidian/read-line-length-wider-note-css-snippet/","tags":["code","wider-note","Obsidian"],"noteIcon":"","created":"2024-05-27 4:26:35 pm","updated":"2024-05-27 4:26:54 pm"}
---

Description: allow individual note bypassing of limiting line length set in Settings-->Editor-->Readable Line Length

Filename: wider-note.css
Save to .obsidian\snippets
Add property: cssclasses: wider-note

```css
  /* save this as wider-note.css in your snippet */
.wider-note {

    /*Set the width of your desire here*/
    /* --user-custom-width: 60rem !important; */
    --user-custom-width: 1500px !important;

    /*Code for edit view*/
    --file-line-width: var(--user-custom-width) ;

    /*Code for live read view*/
    /* --content-max-width: 100rem !important; */
    --content-max-width: 1500px !important;
    --content-base-width: var(--user-custom-width);
}
```

Reference:
- https://www.reddit.com/r/ObsidianMD/comments/s55zcw/how_to_have_a_custom_line_width/
- https://github.com/0skater0/obsidian-custom-note-width