# d_link
Obsidian Templater template that creates a new note doubly linked to the previous note.

## My Obsidian flow
I don't use the daily notes plug-in. Instead, I append to a note until it gets too long 
and then start a new note. Since the new note is a continuation of the old note, it would be nice
to have a link in the new note (child) that points back to the old note and to have a link in the old note (parent)
point forward to the new note.

## My naming convention
I tend to have a dozen or more notes active in my workspace (open for veiwing or editing) and I've found that 
it can be hard to tell which tab is which. So I came up with a naming convention that suits my style. 

File (note) names start with a two-letter code indicating what kind of note it is. Examples:
- td: todo
- wj: work journal
- wd: work todo
- pr: prep for event 
- po: post event

## Template invocation
- while editing a note that will be the parent (old) note.
- command pallet / Templater: Create New Note From Template.
- select d_link from the drop-down list.
- select a two-letter code.
  
A new note will be created with a little boilerplate and a link to the parent note. The parent note will have a link to the new note.

## Alternate invocation
When presented with the drop-down list of two-letter codes.
- press escape (back button on Android).
- enter a custom comma-separated text for a prefix code and suffix text (prefix,suffix).

The new name will be in the form "prefix date suffix". Any prefix and sufix text is allowed (within the rules of file naming) in this alternate invocation - but the date will always be there. 

If the alternate entry is entirely blank, then the new note will be named "ef date" (ef for ephemeral)

## My Obsidian Setup
- New notes are created in the same folder as the current note (Settings/Files and links/Default location for new notes).
- The Templates Core plug-in is **dis-abled**.
- Templater community plug-in is installed and enabled.
- This template (d_link.md) is in the Templater template folder.
