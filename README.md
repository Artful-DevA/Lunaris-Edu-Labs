# Lunaris Edu Labs 🌕

**TKS Create | Solo project | In development**

Lunaris Edu Labs is a standalone **Meta Quest 3** lunar-habitat VR experience. Players investigate simulated equipment failures, examine live telemetry, and see the outputs of a **genuinely trained Mamba-based time-series anomaly detector**.

> Status: **Milestone 0, repository initialization.** The Unity project, Quest APK, and trained Mamba model do not exist yet.

## Project scope

- **Environment:** Three interconnected indoor habitat modules: Main Control, Engineering, and Life Support. No exterior exploration in V1. Internal hatches are normally open; exterior airlock stays closed.
- **Core interaction:** Trigger a simulated failure, observe evolving telemetry, examine a model-generated anomaly score, diagnose the problem, and restore normal operation.
- **VR:** Native standalone Meta Quest 3 APK, built with Unity 6 LTS and URP. PCVR is optional later.
- **Backend:** Python simulation, FastAPI secure WebSocket transport, and trained Mamba inference hosted remotely so the player's PC does not need to remain on.
- **AI integrity:** Model outputs must come from actual inference; simulation fault ground truth must be kept distinct from predictions. Compare Mamba to Isolation Forest and a temporal/threshold baseline.
- **Display:** Live sensor plots, system diagnostics, anomaly scores, optional AI activation visualizations clearly labeled as *activations*, and an exterior camera view if performance permits.
- **Not in V1:** Multiplayer, exterior walking, fully functional keyboards, interactive chairs, or hundreds of independent switches.

## Layout

```text
lunaris-edu-labs/
  PLAN.md                   Milestones and success criteria
  README.md                 Project overview
  .gitignore                Unity, Python, secret, and build exclusions
  docs/UNITY_SETUP.md       First install / clone / Unity project instructions
  protocol/schema.json      Versioned WebSocket message schema
  protocol/examples/        Valid example messages
  unity-vr-client/          Unity project will be created here on the laptop
  mamba-backend/            Python project will be added in later milestones
```

## First development milestone

1. Install Unity Hub and a verified compatible Unity 6 LTS editor with Android Build Support (SDK/NDK + OpenJDK).
2. Clone the repository to the development laptop.
3. Create a **Universal 3D (URP)** project named `unity-vr-client` in the cloned repository's root. Do not create a second nested `unity-vr-client/unity-vr-client` folder.
4. Add XR/OpenXR support and configure Android build settings.
5. Test an empty VR room in a standalone Quest 3 APK.
6. Only then import the evolving habitat assets and assemble the scene.

See [Unity setup](docs/UNITY_SETUP.md), [plan](PLAN.md), and [WebSocket contract](protocol/schema.json).

## Credits

3D assets: project author and contributors, with source/license details to be documented before distribution. AI-assisted tools may support coding and modeling; all outputs require review and testing.
