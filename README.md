# hyprscrolling

A [Niri](https://github.com/YaLTeR/niri) like scrollable window management plugin for hyprland.

## installation

Update your headers with `hyprpm update` if you haven't.

Then add this repository and enable the plugin

```bash
hyprpm add https://github.com/vaguesyntax/hyprscrolling
hyprpm enable hyprscrolling
```

Set your `general::layout::` to `scrolling` to enable scrolling tiling

```bash
general {
 layout = scrolling
}
```
Set the settings in your config file _(full list available below)_
```bash
plugin {
    hyprscrolling {
        column_width = 0.7
        fullscreen_on_one_column = true
    }
}
```
Add your desired keybinds to work with windowses

This keybinds are mine, tweak it to your liking
```bash
bind = Super, mouse_up, layoutmsg, move +col
bind = Super, mouse_down, layoutmsg, move -col

bind = Super+Alt, mouse_up, layoutmsg, colresize +conf
bind = Super+Alt, mouse_down, layoutmsg, colresize -conf

bind = Super+Shift, mouse_up, layoutmsg, swapcol r
bind = Super+Shift, mouse_down, layoutmsg, swapcol l

bind = Super, E, layoutmsg, fit active
```

## list of options

| name | description | type | default |
| -- | -- | -- | -- |
| fullscreen_on_one_column | if there's only one column, should it be fullscreen | bool | false |
| column_width | default column width as a fraction of the monitor width | float [0 - 1] | 0.5 |
| explicit_column_widths | a comma-separated list of widths for columns to be used with `+conf` or `-conf` | string | `0.333, 0.5, 0.667, 1.0` |
| focus_fit_method | when a column is focused, what method to use to bring it into view. 0 - center, 1 - fit | int | 0 |
| follow_focus | when a window is focused, the layout will move to make it visible | bool | true |

## list of keybind actions

| name | description | params |
| --- | --- | --- |
| move | move the layout horizontally, by either a relative logical px (`-200`, `+200`) or columns (`+col`, `-col`) | move data |
| colresize | resize the current column, to either a value or by a relative value e.g. `0.5`, `+0.2`, `-0.2` or cycle the preconfigured ones with `+conf` or `-conf`. Can also be `all (number)` for resizing all columns to a specific width | relative float / relative conf |
| movewindowto | same as the movewindow dispatcher but supports promotion to the right at the end | direction |
| fit | executes a fit operation based on the argument. Available: `active`, `visible`, `all`, `toend`, `tobeg` | fit mode |
| focus | moves the focus and centers the layout, while also wrapping instead of moving to neighbring monitors. | direction |
| focusaddr | moves the focus and centers the layout to the given window, note that you have to be in the same workspace in order for this dispatch to work. You have to first call `hyprctl dispatch focuswindow address::___` and call this dispatch **after that** if you want to focus a window from another workspace | window address |
| promote | moves a window to its own new column | none |
| swapcol | Swaps the current column with its neighbor to the left (`l`) or right (`r`). The swap wraps around (e.g., swapping the first column left moves it to the end). | `l` or `r` |
| swapaddr | Swaps the two given windows's places. They have to be in the same workspace | (window address) (window adress) |
| swapaddrdir | Moves the source window to target's windowses right or lef. They have to be in the same workspace| (target win addr) (l-r) (source win addr) |
| movecoltoworkspace | Moves the entire current column to the specified workspace, preserving its internal layout. Works with existing, new, and special workspaces. e.g. like `1`, `2`, `-1`, `+2`, `special`, etc. | workspace identifier|
| togglefit | Toggle the focus_fit_method (center, fit) | none |




- Fork of https://github.com/hyprwm/hyprland-plugins/tree/main/hyprscrolling



