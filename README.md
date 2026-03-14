# org.openxtalk.macosmenubar

A LiveCode Builder (LCB) extension that exposes macOS menu bar information via Objective-C bindings to `NSMenu`.

## Requirements

- LiveCode 9.0 or later
- OpenXTalk 1.14 or greater
- macOS (handlers return safe defaults on other platforms)

## API

### `MenuBarHeight()`

Returns the height of the macOS menu bar in points.

```livecode
put MenuBarHeight() into tHeight
-- tHeight is typically 24 on standard displays
```

**Returns:** `Number` — height in points, or `0` on non-Mac platforms.

---

### `MenuBarVisible()`

Returns whether the macOS menu bar is currently visible.

```livecode
if MenuBarVisible() then
    put MenuBarHeight() into tHeight
    answer "Menu bar is" && tHeight && "points tall"
else
    answer "Menu bar is hidden"
end if
```

**Returns:** `Boolean` — `true` if visible, `false` if hidden or on non-Mac platforms.

---

### `SetMenuBarVisible(pVisible)`

Shows or hides the macOS menu bar.

```livecode
-- Hide the menu bar
SetMenuBarVisible(false)

-- Show the menu bar
SetMenuBarVisible(true)
```

**Parameters:** `pVisible` — `Boolean`  
**Returns:** nothing

> **Note:** Hiding the menu bar does not enter full-screen mode.

## Platform Notes

| Handler                | macOS | Windows | Linux |
|------------------------|-------|---------|-------|
| `MenuBarHeight()`      | ✅    | returns `0` | returns `0` |
| `MenuBarVisible()`     | ✅    | returns `false` | returns `false` |
| `SetMenuBarVisible()`  | ✅    | no effect | no effect |

## Objective-C Bindings

| LCB Handler             | Objective-C                          |
|-------------------------|--------------------------------------|
| `MenuBarHeight()`       | `+[NSMenu menuBarHeight]`            |
| `MenuBarVisible()`      | `+[NSMenu menuBarVisible]`           |
| `SetMenuBarVisible()`   | `+[NSMenu setMenuBarVisible:]`       |

