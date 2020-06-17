smart_borders for awesomewm
==================

<p align="center">
  <img src="https://i.imgur.com/ozjXeyi.gif">
</p>

Features:
------------
- Full titlebar functionality without sacrificing space
- Improved mouse controls
- Custom client menu
- Various configuration options
- Easy installation

How does it work:
------------
`smart_borders` are essentially 4 individual titlebars that offer full titlebar functionality and controls while being minimalistic and aesthetically pleasing like borders.
The regular `X11` borders are additionally available and can be used to achieve a *double-border-look* (like `2bwm`).

Installation:
------------

Clone the repo and import the module:

1. `git clone https://github.com/intrntbrn/smart_borders ~/.config/awesome/smart_borders`
1. `echo "require('smart_borders'){ show_button_tooltips = true }" >> ~/.config/awesome/rc.lua`

To disable the regular `X11` borders, set `theme.border_width = 0` in `theme.lua`.

If you end up using this module, consider removing default titlebar initialization code (e.g. `request::titlebars` signal handlers) from `rc.lua` to improve startup times and performance.

Controls:
------------

| button | default action | handler |
|---|---|---|
| <kbd>left click</kbd> | move client | `button_left_click`
| <kbd>right click</kbd> | open client menu | `button_right_click`
| <kbd>double left click</kbd> | toggle maximize | `button_double_click`
| <kbd>middle click</kbd> | resize client | `button_middle_click`
| <kbd>mousewheel up</kbd> | increase client height | `button_wheel_up`
| <kbd>mousewheel down</kbd> | decrease client height | `button_wheel_down`
| <kbd>mouse forward</kbd> | swap client with next client by index | `button_forward`
| <kbd>mouse back</kbd> | swap client with previous client by index | `button_back`

Customization:
------------

| name | default | description |
|---|---|---|
| `positions` | { "left", "right", "top", "bottom" } | border positions
| `button_positions` | { "top" } | button positions |
| `buttons` | { "floating", "minimize", "maximize", "close" } | possible values: { "floating", "minimize", "maximize", "close", "sticky", "top" } |
| `border_width` | dpi(6) | width of border |
| `show_button_tooltips` | false | show a tooltip on button mouse over |
| `show_title_tooltips` | false | show a tooltip of client title on border mouse over (might cause issues when sloppy focus mode (focus follows mouse) is enabled) |
| `align_horizontal` | "right" | alignment of buttons on top and bottom positions. possible values: { "left", "center", "right" } |
| `align_vertical` | "center" | alignment of buttons on left and right positions. possible values: { "bottom", "center", "top" }  |
| `layout` | "fixed" | possible values: { "fixed", "ratio" }. "fixed": every button size can be configured individually (see `buttion_size`). "ratio": each button is assigned a ratio (percentage) equally of the total space (see `button_ratio`). |
| `button_size` | dpi(40) | default button size when layout is set to "fixed". each button size can be configured individually. |
| `button_ratio` | 0.2 | relative size of buttons in percent when layout is set to "ratio"  |
| `spacing_widget` | nil | spacing widget (between buttons) |
| `button_maximize_size` | `button_size` | size of maximize button |
| `button_minimize_size` | `button_size` | size of minimize button |
| `button_floating_size` | `button_size` | size of floating button |
| `button_sticky_size` | `button_size` | size of sticky button |
| `button_close_size` | `button_size` | size of close button |
| `button_top_size` | `button_size` | size of top button |
| `color_normal` | "#56666f" | border color |
| `color_focus` | "#a1bfcf" | border color when client is focused |
| `color_maximize_normal` | "#a9dd9d" |  color of maximize button |
| `color_maximize_focus` | "#a9dd9d" |  color of maximize button when client is focused |
| `color_maximize_hover` | "#c3f7b7" |  color of maximize button on mouse hover |
| `color_minimize_normal` | "#f0eaaa" |  color of minimize button |
| `color_minimize_focus` | "#f0eaaa" |  color of minimize button when client is focused |
| `color_minimize_hover` | "#f6ffea" |  color of minimize button on mouse hover |
| `color_floating_normal` | "#ddace7" |  color of floating button |
| `color_floating_focus` | "#ddace7" |  color of floating button when client is focused |
| `color_floating_hover` | "#f7c6ff" |  color of floating button on mouse hover |
| `color_sticky_normal` | "#fb8965" |  color of sticky button |
| `color_sticky_focus` | "#fb8965" |  color of sticky button when client is focused |
| `color_sticky_hover` | "#ffa37f" |  color of sticky button on mouse hover |
| `color_close_normal` | "#fd8489" |  color of close button |
| `color_close_focus` | "#fd8489" |  color of close button when client is focused |
| `color_close_hover` | "#ff9ea3" |  color of close button on mouse hover |
| `color_top_normal` | "#7fc1ca" |  color of top button |
| `color_top_focus` | "#7fc1ca" |  color of top button when client is focused |
| `color_top_hover` | "#99dbe4" |  color of top button on mouse hover |
| `menu_selection_symbol` | "✔" | default menu selection indicator |
| `resize_factor` | 0.01 | default client resize factor |
| `stealth` | false | show only button colors on hover (set button colors to border colors) |


Example Configuration (as shown on gif): 
------------
```
require("smart_borders"){
	show_button_tooltips = true,

	button_positions = { "top" },
	buttons = { "floating", "minimize", "maximize", "close" },

	layout = "fixed",
	button_ratio = 0.3,
	align_horizontal = "center",
	button_size = 40,
	button_floating_size = 60,
	button_close_size = 60,
	border_width = 6,

	color_close_normal = {
		type = "linear",
		from = { 0, 0 },
		to = { 60, 0 },
		stops = { { 0, "#fd8489" }, { 1, "#56666f" } }
	},
	color_close_focus = {
		type = "linear",
		from = { 0, 0 },
		to = { 60, 0 },
		stops = { { 0, "#fd8489" }, { 1, "#a1bfcf" } }
	},
	color_close_hover = {
		type = "linear",
		from = { 0, 0 },
		to = { 60, 0 },
		stops = { { 0, "#FF9EA3" }, { 1, "#a1bfcf" } }
	},
	color_floating_normal = {
		type = "linear",
		from = { 0, 0 },
		to = { 40, 0 },
		stops = { { 0, "#56666f" }, { 1, "#ddace7" } }
	},
	color_floating_focus = {
		type = "linear",
		from = { 0, 0 },
		to = { 40, 0 },
		stops = { { 0, "#a1bfcf" }, { 1, "#ddace7" } }
	},
	color_floating_hover = {
		type = "linear",
		from = { 0, 0 },
		to = { 40, 0 },
		stops = { { 0, "#a1bfcf" }, { 1, "#F7C6FF" } }
	},

	-- custom control example:
	button_back = function(c)
		-- set client as master
		c:swap(awful.client.getmaster())
	end
}

```
