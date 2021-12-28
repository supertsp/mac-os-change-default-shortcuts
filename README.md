# mac-os-change-default-shortcuts
How to change Mac OS X's default shortcut keys using file DefaultKeyBinding.dict


## Steps

1. Create the file `"DefaultKeyBinding.dict"` into: `~/Library/KeyBindings/DefaultKeyBinding.dict`
2. Copy & Paste the code bellow:
```
/*
Key Modifiers
^ : Ctrl
$ : Shift
~ : Option (Alt)
@ : Command (Win)
# : Numeric Keypad
Non-Printable Key Codes

Standard
Up Arrow:     \UF700        Backspace:    \U0008        F1:           \UF704
Down Arrow:   \UF701        Tab:          \U0009        F2:           \UF705
Left Arrow:   \UF702        Escape:       \U001B        F3:           \UF706
Right Arrow:  \UF703        Enter:        \U000A        ...
Insert:       \UF727        Page Up:      \UF72C
Delete:       \UF728        Page Down:    \UF72D
Home:         \UF729        Print Screen: \UF72E
End:          \UF72B        Scroll Lock:  \UF72F
Break:        \UF732        Pause:        \UF730
SysReq:       \UF731        Menu:         \UF735
Help:         \UF746

OS X
delete:       \U007F
*/
{
  "^c" = (copy:);
  "^v" = (paste:);
  "^x" = (cut:);
  "^a" = (moveToBeginningOfDocument:, moveToEndOfDocumentAndModifySelection:);
  "^z" = (undo:);
  "^y" = (redo:);

  //Jumping by words - to left
  "$\UF702" = (moveWordLeft:);
  //Jumping by words - to right
  "$\UF703" = (moveWordRight:);

  //Move to Beginning
  "\UF729" = (moveToBeginningOfLine:);
  //Move to End
  "\UF72B" = (moveToEndOfLine:);

  //Move to Beginning and Select
  "$\UF729" = (moveToBeginningOfLineAndModifySelection:);
  //Move to End and Select
  "$\UF72B" = (moveToEndOfLineAndModifySelection:);

  // Commenting commands
  "^@c" = {
    // comment with "//"
    "/" = (moveToBeginningOfParagraph:, insertText:, "// ", moveToEndOfParagraph:, moveForward:);
    // comment with "#"
    "3" = (moveToBeginningOfParagraph:, insertText:, "# ", moveToEndOfParagraph:, moveForward:);
    // HTML commenting
    "!" = (setMark:, swapWithMark:, delete:, insertText:, "<!-- ", yank:, insertText:, " -->", swapWithMark:, moveRight:, moveRight:, moveRight:, moveRight:, moveRight:);
    // Css Commenting
    "*" = (setMark:, swapWithMark:, delete:, insertText:, "/* ", yank:, insertText:, " */", swapWithMark:, moveRight:, moveRight:, moveRight:);
  };

  // Duplicate line down
  "^d" = (setMark:, moveToBeginningOfParagraph:, moveToEndOfParagraphAndModifySelection:, copy:, swapWithMark:, moveToEndOfParagraph:,moveRight:,insertNewline:,moveLeft:, paste:);

  // Move line up
  "~\UF700" = (selectParagraph:, setMark:, deleteToMark:, moveLeft:, moveToBeginningOfParagraph:, yank:, moveLeft:, selectToMark:, moveLeft:);
  // Move line down
  "~\UF701" = (selectParagraph:, setMark:, deleteToMark:, moveToEndOfParagraph:, moveRight:, setMark:, yank:, moveLeft:, selectToMark:);
}
```

## References

1. https://github.com/microsoft/vscode/issues/111950
2. https://gist.github.com/trusktr/1e5e516df4e8032cbc3d
3. https://github.com/ttscoff/KeyBindings