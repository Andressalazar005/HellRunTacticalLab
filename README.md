# Tactical AI Lab

Native Unreal Engine 5 tactical-AI tooling for scenario authoring, deterministic simulation, map baking, GOAP debugging, and lifetime analysis.

**Version:** 0.1.0  
**Category:** AI  
**Status:** Beta  
**Modules:** `HellRunTacticalLab` (Runtime), `HellRunTacticalLabEditor` (Editor)

## Required project plugins

Tactical AI Lab declares these plugin dependencies:

- `HellRunTraversalNavigation`
- `HellRunGOAP`

Install both before compiling Tactical AI Lab.

## Installation

From your Unreal project's `Plugins` directory:

```bash
git clone https://github.com/Andressalazar005/HellRunTraversalNavigation.git HellRunTraversalNavigation
git clone https://github.com/Andressalazar005/HellRunGOAP.git HellRunGOAP
git clone https://github.com/Andressalazar005/HellRunTacticalLab.git HellRunTacticalLab
```

Expected layout:

```text
YourProject/
  Plugins/
    HellRunTraversalNavigation/
      HellRunTraversalNavigation.uplugin
    HellRunGOAP/
      HellRunGOAP.uplugin
    HellRunTacticalLab/
      HellRunTacticalLab.uplugin
```

Then:

1. Close Unreal Editor.
2. Delete stale `Binaries/` and `Intermediate/` folders from all three plugins if they were built against another engine version.
3. Regenerate project files if required.
4. Build your project's **Development Editor** target, or launch Unreal and allow it to compile the source plugins.
5. Open **Edit > Plugins** and confirm all three plugins are enabled.
6. Restart the editor if prompted.

## What the plugin provides

- Tactical AI scenario editor tooling.
- Deterministic simulation support.
- Map-baking workflow.
- Integration with GOAP debugging.
- Lifetime/behavior analysis tooling.
- Runtime and editor modules with plugin-owned content support.

## Verify the installation

- Confirm `HellRunTraversalNavigation` and `HellRunGOAP` load before Tactical AI Lab.
- Confirm both Tactical AI Lab modules compile successfully.
- Open the editor and check the Output Log for missing dependency/module errors.
- Validate a small tactical scenario before migrating or baking larger maps.

## Updating

Keep all three repositories compatible with one another:

```bash
cd YourProject/Plugins/HellRunTraversalNavigation && git pull
cd ../HellRunGOAP && git pull
cd ../HellRunTacticalLab && git pull
```

When changing Unreal Engine versions, remove plugin `Binaries/` and `Intermediate/` folders before rebuilding.

## Support

Use GitHub Issues for reproducible editor, simulation, baking, GOAP-integration, or runtime problems. Include the Unreal Engine version, dependency revisions, reproduction steps, and relevant logs.
