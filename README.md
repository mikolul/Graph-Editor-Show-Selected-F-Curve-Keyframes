# Graph Editor: Show Selected F-Curve Keyframes

In new versions of Blender, "Show Selected F-Curve Keyframes" has been moved from Graph Editor to Preferences. This addon restores access to "Show Selected F-Curve Keyframes" setting in the Graph Editor using Keymap.

Creating an operator from Preferences to create a hotkey for displaying selected F-Curve Keyframes in the Graph Editor.

There are two ways to run the addon:
- [Standard installation](#installation)
- [Run in the current session / current .blend file](#run-in-current-session)

> [!NOTE]
>**Supported Blender Versions:** 3.6+

## Installation

1. Download the latest `Graph-Editor-Show-Selected-F-Curve-Keyframes.zip` from [<ins>Releases</ins>](https://github.com/mikolul/Graph-Editor-Show-Selected-F-Curve-Keyframes/releases)
2. In Blender:
    - `Edit` -> `Preferences` -> `Add-ons`
    - Click `Install...` and select the downloaded file
    - Enable the addon
3. Go to:
    - `Edit` -> `Preferences` -> `Keymap` -> `Graph Editor` -> `Graph Editor Generic`
    - Click `Add new`
    - Set Identifier from `none` to `graph.toggle_only_show_selected`
    - Assign any hotkey (example): `Ctrl + Shift + H`
4. Save Preferences

## Run in current session

1. `Scripting` tab
2. Paste code:
```python
import bpy

class GRAPH_OT_toggle_only_show_selected(bpy.types.Operator):
    bl_idname = "graph.toggle_only_show_selected"
    bl_label = "Toggle Only Show Selected F-Curve Keyframes"

    def execute(self, context):
        prefs = context.preferences
        prefs.edit.show_only_selected_curve_keyframes ^= True
        return {'FINISHED'}
        
def register():
    bpy.utils.register_class(GRAPH_OT_toggle_only_show_selected)

def unregister():
    bpy.utils.unregister_class(GRAPH_OT_toggle_only_show_selected)

if __name__ == "__main__":
    register()
```

3. Click `play icon`
4. Go to:
    - `Edit` -> `Preferences` -> `Keymap` -> `Graph Editor` -> `Graph Editor Generic`
    - Click `Add new`
    - Set Identifier from `none` to `graph.toggle_only_show_selected`
    - Assign any hotkey (example): `Ctrl + Shift + H`
