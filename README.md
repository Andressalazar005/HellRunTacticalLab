# Hell Run Tactical Lab

## Overview
Hell Run Tactical Lab is an Unreal Engine 5 tactical-AI authoring and analysis environment built around repeatable scenarios rather than one-off debug maps. It combines runtime tactical evaluation with editor-side scenario assets, deterministic simulation, map/surface data, GOAP inspection, and analysis tooling so AI positioning and decision rules can be exercised, compared, and debugged under controlled conditions.

## Features
- `UTacticalLabScenarioAsset` for reusable authored test scenarios.
- Runtime `FHellRunTacticalLab` simulation/orchestration layer.
- `FHellRunTacticalEvaluator` for evaluating tactical choices and candidate states.
- EQS context integration for tactical query workflows.
- Integration points for Hell Run GOAP and Traversal Navigation.
- Dedicated editor asset definition and scenario editing surface.
- Goal-graph visualization for inspecting scenario/GOAP relationships.
- Deterministic simulation support for comparing AI behavior across the same setup.
- Map/surface baking and tactical data preparation tools.
- Architecture audit/documentation included under `Docs/` for the broader system design.

## Architecture
The plugin is split into runtime and editor modules. Runtime code contains the tactical evaluator, scenario/runtime types, EQS context, and integration hooks. The editor module owns scenario-asset editing and visualization, including the large Tactical Lab surface and goal graph. This keeps the analysis UI out of packaged runtime code while allowing the same scenario data to drive tests and simulations.

## Installation
1. Install **HellRunTraversalNavigation** and **HellRunGOAP** first; both are declared plugin dependencies.
2. Clone or copy this repository to `<Project>/Plugins/HellRunTacticalLab`.
3. Delete stale `Binaries` and `Intermediate` directories from all three plugins if they came from another Unreal build.
4. Regenerate project files and compile your Editor target.
5. Launch Unreal Editor and verify **Tactical AI Lab**, **Hell Run GOAP**, and **Hell Run Traversal Navigation** are enabled.
6. Restart the editor if Unreal requests a rebuild.

```bash
git clone https://github.com/Andressalazar005/HellRunTraversalNavigation.git <Project>/Plugins/HellRunTraversalNavigation
git clone https://github.com/Andressalazar005/HellRunGOAP.git <Project>/Plugins/HellRunGOAP
git clone https://github.com/Andressalazar005/HellRunTacticalLab.git <Project>/Plugins/HellRunTacticalLab
```

## Basic workflow
1. Create a Tactical Lab Scenario asset for the encounter or tactical problem you want to test.
2. Author the scenario inputs, agents, goals, environment/map data, and any required integration data.
3. Open the Tactical Lab editor surface for that asset.
4. Bake/update the scenario's map or surface data when the environment changes.
5. Run deterministic simulations to compare tactical scoring/planning results without relying on a manually played encounter.
6. Use the goal graph, evaluator output, and GOAP/traversal integration data to understand why a candidate or plan was selected.

## Key types
- `UTacticalLabScenarioAsset` — reusable authored scenario definition.
- `FHellRunTacticalLab` — tactical lab runtime/simulation coordinator.
- `FHellRunTacticalEvaluator` — tactical candidate/state evaluator.
- `UTacticalLabEQSContext` — EQS bridge for tactical queries.
- `FTacticalLabIntegrations` — integration surface for external AI/navigation systems.

## Dependencies
- HellRunGOAP
- HellRunTraversalNavigation

## Status
The plugin is currently beta. It is an analysis and development toolset as much as a runtime library; projects integrating it should treat scenario/editor workflows separately from shipping AI code and validate their own tactical scoring assumptions.

## Support
Use GitHub Issues for reproducible editor, simulation, or integration problems. Include your Unreal Engine version, scenario asset, GOAP/traversal versions, expected result, actual result, and relevant logs.