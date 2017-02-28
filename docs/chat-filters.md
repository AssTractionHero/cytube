### Chat Filters
Chat filters provide a way for specific text to be recognized and changed in chat messages.  For example, it could be used to transform profanity to strings of asterisks.  **Please do not use chat filters for image emotes.** Adding them as chat filters is more difficult to manage and uses more server resources. CyTube has an emotes feature (new in CyTube 3.0,) which is better-suited for adding emoticons.   

### Adding a new filter
  * **Filter name**: A name to identify the filter.  For informational purposes only, but must be unique.
  * **Filter regex**: A regular expression describing the text to match.
  * **Flags**: A set of regular expression flags to apply.  `g` means to match all instances in the message (instead of just the first), `i` means to match without case sensitivity.
  * **Replacement**: The HTML that will replace the matched text.

See the MDN page for [RegExp](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp) for reference on Regular Expressions and flags.

### Managing existing filters
Filters will be applied in the order they are listed.  You can click and drag individual filters to rearrange them.  The **Active** checkbox allows you to easily enable / disable individual filters.  Under the **Control** column, the left button with a list icon opens an editor to change the regular expression, flags, and replacement for a filter.  The red button with a trashcan icon will delete the filter.

The **Filter Links** checkbox controls whether this filter will be applied to links in chat.  By default, this is off, to prevent filters from breaking links pasted in chat by changing them.

### Importing / Exporting filters (New in CyTube 3.0)
You can export and import your channel's filter list in order to back it up or transfer it to another channel.  Clicking **Export filter list** will populate the text area with a JSON-encoded list of filter data.  To import a filter list, paste the JSON data in the textbox and click **Import filter list**.  The import tool is very strict on format and will reject invalid filters, so please be careful to store the exported data verbatim.

[Back to the Quick Reference](index.md)
