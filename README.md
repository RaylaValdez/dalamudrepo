# Dalamud Plugins by Gerry_of_Ravine

Custom third party Dalamud plugin repository for FINAL FANTASY XIV.
Because some of these plugins are automation, they cannot be hosted on
the official Dalamud repository, so they live here instead.

## Install (as a player)

1. In game, open `/xlsettings` and go to the **Experimental** tab.
2. Under **Custom Plugin Repositories**, paste:

   ```
   https://raw.githubusercontent.com/RaylaValdez/dalamudrepo/main/pluginmaster.json
   ```

3. Tick the new entry as **Enabled**, then **Save and Close**.
4. Open `/xlplugins`, switch to **All Plugins**, and install what you want.

Updates arrive through the normal plugin installer once the repo is
subscribed.

## Plugins

| Plugin | Source | Notes |
| --- | --- | --- |
| [ClickToMove](https://github.com/RaylaValdez/ClickToMove) | Click where you wanna go! Shift-click the world to walk there, via vnavmesh pathfinding with a straight line fallback. | Actively maintained. |
| [SimonSays](https://github.com/RaylaValdez/SimonSays) | Syncs emotes by using the chat itself. | Currently unmaintained; built against an older Dalamud API. |

Some plugins need companion plugins from other repos. ClickToMove uses
[vnavmesh](https://puni.sh/api/repository/veyn) for pathfinding when it
is installed, and falls back to straight line walking when it is not.

## Disclaimer

Movement and emote automation are third party and unsupported by
Square Enix or the Dalamud team. Use at your own risk, keep it private,
and be extra careful in PvP or high end duties.

## Repository layout (for maintainers)

- `pluginmaster.json` - the repo manifest Dalamud reads. One entry per
  plugin, with download links, version, API level, and `LastUpdate`.
- `plugins/<Name>/latest.zip` - the distributable: plugin DLL, deps
  json, manifest json, and icon png.
- `plugins/<Name>/<Name>.json` - a copy of the packaged manifest for
  quick inspection.

To publish an update: build the plugin in its release configuration,
replace `plugins/<Name>/latest.zip`, refresh the manifest copy, bump
`AssemblyVersion` and `LastUpdate` (unix seconds) in
`pluginmaster.json`, then commit and push. Dalamud picks the change up
on its next repo refresh.
