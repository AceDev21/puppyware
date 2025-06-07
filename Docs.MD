# GitHub Documentation for UI Library

Here's the documentation for the UI library you provided. This will help you understand how to use it to create your own scripts.

## Overview

This UI library provides a customizable interface for Roblox scripts with various elements like toggles, buttons, sliders, dropdowns, color pickers, and more. It supports themes, config saving/loading, and has a clean design.

## Getting Started

### Initialization

```lua
local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/AceDev21/puppyware/refs/heads/main/lib"))()
local window = library:new({
    name = "UI Name",
    color = Color3.fromRGB(225, 58, 81), -- Accent color
    textsize = 12, -- Font size
    font = "RobotoMono" -- Font
})
```

## Window Methods

### `window:new(props)`
Creates a new window.

**Parameters:**
- `props` (table):
  - `name` - Name of the UI
  - `color` - Accent color (default: Color3.fromRGB(225, 58, 81))
  - `textsize` - Font size (default: 12)
  - `font` - Font family (default: "RobotoMono")

### `window:watermark()`
Creates a watermark that can display information.

**Methods:**
- `:update(content)` - Updates watermark content (table of key-value pairs)
- `:updateside(side)` - Changes watermark position ("topright", "topleft", "bottomright", "bottomleft")
- `:toggle(bool)` - Shows/hides the watermark

### `window:loader(props)`
Creates a login/close loader screen.

**Parameters:**
- `props` (table):
  - `name` - Loader name
  - `scriptname` - Script name
  - `close` - Callback for close button
  - `login` - Callback for login button

**Methods:**
- `:toggle()` - Shows the loader

### `window:saveconfig()`
Saves the current configuration to a string.

### `window:loadconfig(cfg)`
Loads a configuration from a file path.

### `window:settheme(theme, color)`
Changes a theme color.

### `window:setkey(key)`
Sets the toggle key (EnumItem).

### `window:settoggle(side, bool)`
Enables/disables window movement on X or Y axis.

### `window:setfont(font)`
Changes the font for all elements.

### `window:settextsize(size)`
Changes the text size for all elements.

## Page Methods

### `window:page(props)`
Creates a new tab/page.

**Parameters:**
- `props` (table):
  - `name` - Page name
  - `pointer` - Optional pointer name for external access

**Methods:**
- `:openpage()` - Opens this page

## Section Methods

### `page:section(props)`
Creates a section in the page.

**Parameters:**
- `props` (table):
  - `name` - Section name
  - `side` - "left" or "right"
  - `size` - Height of the section
  - `pointer` - Optional pointer name

### `page:multisection(props)`
Creates a multi-tab section.

**Parameters:** Same as regular section

## Element Types

### Toggle
```lua
section:toggle({
    name = "Toggle Name",
    def = false, -- Default state
    callback = function(state) end,
    pointer = "optional_pointer"
})
```

**Methods:**
- `:set(bool)` - Changes toggle state

### Button
```lua
section:button({
    name = "Button Name",
    callback = function() end
})
```

### Slider
```lua
section:slider({
    name = "Slider Name",
    def = 50, -- Default value
    min = 0,
    max = 100,
    rounding = false, -- Round to integers
    ticking = false, -- Snap to integer values
    measurement = "%", -- Unit text
    callback = function(value) end,
    pointer = "optional_pointer"
})
```

**Methods:**
- `:set(value)` - Changes slider value

### Dropdown
```lua
section:dropdown({
    name = "Dropdown Name",
    def = "Option1", -- Default selection
    options = {"Option1", "Option2"},
    max = 4, -- Max visible options
    callback = function(selected) end,
    pointer = "optional_pointer"
})
```

**Methods:**
- `:set(value)` - Changes selected option

### Multibox
```lua
section:multibox({
    name = "Multibox Name",
    def = {"Option1"}, -- Default selections
    options = {"Option1", "Option2"},
    max = 4, -- Max visible options
    callback = function(selected) end,
    pointer = "optional_pointer"
})
```

**Methods:**
- `:set(table)` - Changes selected options

### Buttonbox
```lua
section:buttonbox({
    name = "Buttonbox Name",
    def = "Option1", -- Default selection
    options = {"Option1", "Option2"},
    max = 4, -- Max visible options
    callback = function(selected) end,
    pointer = "optional_pointer"
})
```

**Methods:**
- `:set(value)` - Changes selected option

### Textbox
```lua
section:textbox({
    name = "Textbox Name",
    def = "", -- Default text
    placeholder = "Placeholder",
    callback = function(text) end,
    pointer = "optional_pointer"
})
```

**Methods:**
- `:set(text)` - Changes textbox content

### Keybind
```lua
section:keybind({
    name = "Keybind Name",
    def = Enum.KeyCode.RightShift, -- Default key
    allowed = 1, -- 1 = allow mouse buttons
    callback = function(key) end,
    pointer = "optional_pointer"
})
```

**Methods:**
- `:set(key)` - Changes bound key (EnumItem)

### Colorpicker
```lua
section:colorpicker({
    name = "Colorpicker Name",
    cpname = "Picker Title", -- Optional different name
    def = Color3.fromRGB(255,255,255), -- Default color
    callback = function(color) end,
    pointer = "optional_pointer"
})
```

**Methods:**
- `:set(color)` - Changes color (Color3 or table {r,g,b})

### Configloader
```lua
section:configloader({
    folder = "Folder/Path/" -- Where to save configs
})
```

## Example Usage

```lua
local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/AceDev21/puppyware/refs/heads/main/lib"))()
local window = library:new({
    name = "My UI",
    color = Color3.fromRGB(255, 0, 0)
})

local page = window:page({name = "Main"})
local section = page:section({name = "Settings", side = "left"})

section:toggle({
    name = "Enable Feature",
    def = true,
    callback = function(state)
        print("Feature enabled:", state)
    end
})

section:slider({
    name = "Speed",
    def = 50,
    min = 0,
    max = 100,
    callback = function(value)
        print("Speed set to:", value)
    end
})
```

## Notes

1. The UI can be toggled with RightShift by default (configurable with `:setkey()`)
2. Configurations can be saved and loaded using the configloader
3. All elements can be accessed externally using pointers
4. The UI is draggable by clicking and dragging the title bar

This documentation covers all the main functionality of the library. You can now use this to create your own scripts with this UI framework.
