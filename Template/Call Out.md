<%*

const callouts = {

   note:     '✏ Note',

   info:     'ℹ Information',

   todo:     '🔳 To-do',

   example:  '📑 Example',

   tip:      '🔥 Tip / Hint / Important',

   quote:    '💬 Quote / Cite',

   abstract: '📋 Summary / Abstract / TLDR',

   question: '❓ Question / Help / FAQ',

   success:  '✔ Success / Check / Done',

   warning:  '⚠ Warning / Caution / Attention',

   failure:  '❌ Failure / Fail / Missing',

   danger:   '⚡ Danger / Error',

   bug:      '🐞 Bug',

};

  

const type = await tp.system.suggester(Object.values(callouts), Object.keys(callouts), true, 'Select callout type.');

const fold = await tp.system.suggester(['Expanded', 'Collapsed'], ['+', '-'], true, 'Select callout fold option.');

  

const title = await tp.system.prompt('Title:', '', true);

let content = await tp.system.prompt('Content (New line -> Shift + Enter):', '', true, true);

content = content.split('\n').map(line => `> ${line}`).join('\n')

  

const calloutHead = `> [!${type}]${fold} ${title}\n`;

  

tR += calloutHead + content

-%>