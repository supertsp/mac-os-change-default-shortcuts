# mac-os-change-default-shortcuts
How to change Mac OS X's default shortcut keys using file DefaultKeyBinding.dict


## Steps

1. Create the file `"DefaultKeyBinding.dict"` into: `~/Library/KeyBindings/`
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
  "^x" = (cut:);
  "^v" = (paste:);
  "^a" = (moveToBeginningOfDocument:, moveToEndOfDocumentAndModifySelection:);
  "^z" = (undo:);
  "^y" = (redo:);

  //Move to Beginning
  "\UF729" = (moveToBeginningOfLine:);
  //Move to End
  "\UF72B" = (moveToEndOfLine:);

  //Move to Beginning and Select
  "$\UF729" = (moveToBeginningOfLineAndModifySelection:);
  //Move to End and Select
  "$\UF72B" = (moveToEndOfLineAndModifySelection:);

  // Duplicate Line
  "^d" = (setMark:, moveToBeginningOfParagraph:, moveToEndOfParagraphAndModifySelection:, copy:, swapWithMark:, moveToEndOfParagraph:, moveRight:, insertNewline:, moveLeft:, paste:);

  // Move Line up
  "~\UF700" = (selectParagraph:, setMark:, deleteToMark:, moveLeft:, moveToBeginningOfParagraph:, yank:, moveLeft:, selectToMark:, moveLeft:);
  // Move Line down
  "~\UF701" = (selectParagraph:, setMark:, deleteToMark:, moveToEndOfParagraph:, moveRight:, setMark:, yank:, moveLeft:, selectToMark:);

  // Comment Line with //
  "^$>" = (moveToBeginningOfParagraph:, insertText:, "// ", moveToEndOfParagraph:);
  // Uncomment Line with //
  "^$<" = (moveToBeginningOfParagraph:, moveRight:, moveRight:, moveRight:, deleteBackward:, deleteBackward:, deleteBackward:, moveToEndOfParagraph:);

  // Uppercase current paragraph
  "^u" = (setMark:, selectParagraph:, uppercaseWord:, swapWithMark:);
  // Lowercase current paragraph
  "^$U" = (setMark:, selectParagraph:, lowercaseWord:, swapWithMark:);

}
```

3. Restart your Mac

## Shortcuts

### New
| ***ACTION***                  | ***SHORTCUT ON WIN KEYBOARD*** | ***SHORTCUT ON MAC KEYBOARD*** | 
|:-----------------------------------------:|:------------------:|:------------------------------:|
| **Copy**                                  | Ctrl + C           | ^ + C                          |
| **Cut**                                   | Ctrl + X           | ^ + X                          |
| **Paste**                                 | Ctrl + V           | ^ + V                          |
| **Select All**                            | Ctrl + A           | ^ + A                          |
| **Undo**                                  | Ctrl + Z           | ^ + Z                          |
| **Redo**                                  | Ctrl + Y           | ^ + Y                          |
| **Move to Beginning of Line**             | Home               | none                           |
| **Move to End of Line**                   | End                | none                           |
| **Move to Beginning of Line and Select**  | Shift + Home       | none                           |
| **Move to End of Line and Select**        | Shift + End        | none                           |
| **Duplicate Line**                        | Ctrl + D           | ^ + D                          |
| **Move Line Up**                          | Alt + &uarr;       | ⌥ + &uarr;                    |
| **Move Line Down**                        | Alt + &darr;       | ⌥ + &darr;                    |
| **Comment Line with //**                  | Ctrl + Shift + >   | ^ + ⇧ + >                      |
| **Uncomment Line with //**                | Ctrl + Shift + <   | ^ + ⇧ + <                      |
| **Uppercase current Paragraph**           | Ctrl + U           | ^ + U                          |
| **Lowercase current Paragraph**           | Ctrl + Shift + U   | ^ + ⇧ + U                      |

### Current
| ***ACTION***                  | ***SHORTCUT ON WIN KEYBOARD*** | ***SHORTCUT ON MAC KEYBOARD*** | 
|:-----------------------------------------:|:------------------:|:------------------------------:|
| **Copy**                                  | Win + C            | ⌘ + C                         |
| **Cut**                                   | Win + X            | ⌘ + X                         |
| **Paste**                                 | Win + V            | ⌘ + V                         |
| **Select All**                            | Win + A            | ⌘ + A                         |
| **Undo**                                  | Win + Z            | ⌘ + Z                         |
| **Redo**                                  | Win + Y            | ⌘ + ⇧ + Z                     |
| **Jumping by Words - To Left**            | Alt + &xrarr;      | ⌥ + &xrarr;                   |
| **Jumping by Words - To Right**           | Alt + &xlarr;      | ⌥ + &xlarr;                   |
| **Move to Left Desktop**                  | Ctrl + &xrarr;     | ^ + &xrarr;                    |
| **Move to Right Desktop**                 | Ctrl + &xlarr;     | ^ + &xlarr;                    |
| **Show All Desktops (Mission Control)**   | Ctrl + &uarr;      | ^ + &uarr;                     |
| **Show Only Current Window**              | Ctrl + &darr;      | ^ + &darr;                     |
| **Spy Desktop**                           | F11                | F11                            |
| **Close App**                             | Win + Q            | ⌘ + Q                         |
| **Block/Lock Screen**                     | Ctrl + Win + Q     | ^ + ⌘ + Q                     |



## References

1. https://github.com/microsoft/vscode/issues/111950
2. https://gist.github.com/trusktr/1e5e516df4e8032cbc3d
3. https://github.com/ttscoff/KeyBindings