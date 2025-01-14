# NorEnglish keys

Hacks to get Norwegian letters åøæ on English keyboard layout.

I write using three keyboard layouts on a daily basis:

* Norwegian: I actually only need three special letters: åøæ and their capital versions ÅØÆ
* Latvian: the special letters āēū, etc.
* English/coding: Some special characters such as ` and #

The problem is that some characters are located on different keys in the different keyboard layouts.

I found a solution (a hack) on how to keep using the Latvian keyboard layout while getting access to
the three necessary Norwegian letters.

Long story short: you can use a software which listens to all key-presses and re-maps some of the
keys. What I found convenient: to map ctrl+[ to å, ctrl+; to ø and ctr+' to æ; as well as
ctrl+shift+[ to Å, ctrl+shift+; to Ø and ctrl+shift+' to Æ.

# On a Mac

On a Mac you can use [Hammerspoon](https://www.hammerspoon.org/) tool, and write the following
configuration script:

```lua
-- å and Å
hs.hotkey.bind({"ctrl"}, "[", function()
  hs.eventtap.keyStrokes('å')
end)
hs.hotkey.bind({"ctrl", 'shift'}, "[", function()
  hs.eventtap.keyStrokes('Å')
end)

-- ø and Ø
hs.hotkey.bind({"ctrl"}, ";", function()
  hs.eventtap.keyStrokes('ø')
end)
hs.hotkey.bind({"ctrl", 'shift'}, ";", function()
  hs.eventtap.keyStrokes('Ø')
end)

-- æ and Æ
hs.hotkey.bind({"ctrl"}, "'", function()
  hs.eventtap.keyStrokes('æ')
end)
hs.hotkey.bind({"ctrl", 'shift'}, "'", function()
  hs.eventtap.keyStrokes('Æ')
end)

-- Have normal Backticks and # on Latvian keyboard
hs.hotkey.bind({}, "§", function()
  hs.eventtap.keyStrokes('`')
end)
hs.hotkey.bind({"shift"}, "3", function()
  hs.eventtap.keyStrokes('#')
end)
```

# On Windows

On a Windows PC you can use [AutoHotKey](https://www.autohotkey.com/) with the following script
(Note - it is important you save it in ISO-8859-1 Encoding (Western Europe), not UTF-8, otherwise you will get weird two-character blocks instead of åøæ)!
:
```
#NoEnv  ; Recommended for performance and compatibility with future AutoHotkey releases.
SendMode Input  ; Recommended for new scripts due to its superior speed and reliability.
SetWorkingDir %A_ScriptDir%  ; Ensures a consistent starting directory.

;------ Ctrl+; -> ø
^;::
Send, ø
return

;------ Ctrl+Shift+; -> ø
^+;::
Send, Ø
return


;------ Ctrl+[ -> å
^[::
Send, å
return

;------ Ctrl+Shift+[ -> Å
^+[::
Send, Å
return


;------ Ctrl+' -> æ
^'::
Send, æ
return

;------ Ctrl+Shift+' -> Æ
^+'::
Send, Æ
return

```
