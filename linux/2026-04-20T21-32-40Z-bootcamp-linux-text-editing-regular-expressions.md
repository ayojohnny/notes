# Linux | Text Editing - Regular Expressions

Regular expression (aka "Regex")
- patterns used to match text
- help filter, search, and transform text

Regex Symbol        | Type          | Meaning
--                  | --            | --
^                   | Anchor        | Start of line
$                   | Anchor        | End of line
.                   | Anchor        | Any single character
`*`                 | Modifier      | Zero or mor characters
[abc]               | Modifier      | Match anything inside the brackets
[a-z]               | Modifier      | Match within range


```bash
# Find all users who have o as second letter.
# Searches from beginning of line, checking in range a-z.
grep `^[a-z]o' /etc/passwd

# Sample output could be
nobody:x:65534:65534:...
pollincate:x:106:106:...
polkadot:x:1010:1010:...
```

Best practices:
1. Always single quote the expression to prevent Bash interpreting special characters.
2. Test with `grep` tool before modifying any system files
3. Always create backups of files before editing
