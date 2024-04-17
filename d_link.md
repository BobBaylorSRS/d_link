

[[<% app.workspace.lastActiveFile.basename %>]]


## Punch list


<%*
// d_link Templater template
// Create and add a new doubly-linked file to the vault.
// The current file (at template invocation) gets a link to the new file.
// The new file gets a link back to the invocation file.
//
// New file name will conform to my convention:
// "prefix date [optional suffix]"
// prefix standard options mean
//   td: todo
//   wj: work journal
//   wd: work todo
//   pr: prep for event 
//   po: post event
// Note: User can escape out of the standard prefixes and enter 
//   a comma-separated pair of arbitrary "prefix, suffix". 

const std_pre_txts = ["td", "wj", "wd", "pr", "po"];
// date fits easily on the obsidian tab bar
const today_text = tp.date.now("MM.DD.YY");
const prev_file_name = app.workspace.lastActiveFile.basename;
let prefix_text = await tp.system.suggester(item => item, std_pre_txts);
let suffix_text = "";

// If user hit `Escape` key (`back` button on mobile)
// then input the comma-separated prefix and suffix
if (!prefix_text) {
  custom_text = await tp.system.prompt("Type custom prefix");
  split_text = custom_text.split(",");
  prefix_text = split_text[0];
  if (!prefix_text) {
  // user entered nothing: "ef" denotes an "ephemeral" note
	  prefix_text = 'ef'
  }
  suffix_text = split_text[1];
  if (!suffix_text) {
	  suffix_text = ''
  }
}
// Rename the new file
const new_file_name = prefix_text.trim() + ' ' + today_text + ' ' + suffix_text.trim();
const link_to_new = "\n[["+new_file_name+"]]\n";
await tp.file.rename(new_file_name);

// Insert a link to the new file into the most recent active file
const note = tp.file.find_tfile(`${prev_file_name}.md`);
const insertedContent = `\n\nchild note is [[${new_file_name}]]\n\n`;
const fileContent = await app.vault.read(note);

const updatedContent = fileContent +`${insertedContent}`;
await app.vault.modify(note, updatedContent);
-%>
