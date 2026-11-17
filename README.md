# Lunaris Edu Labs 🌕

**TKS Create | Solo project | In development**

Lunaris Edu Labs is a standalone **Meta Quest 3** lunar-habitat VR game. The intended final project combines immersive equipment-failure gameplay with **live telemetry, system diagnostics and a genuinely trained Mamba time-series anomaly detector**.

> **Current status (Nov 2026): Frontend first.** No Unity APK or trained model has been built. We are developing the Unity experience first; **Python/Mamba work is planned to resume in January 2027**, at the project owner's pace.

## Scope

- **Environment:** Three interconnected indoor modules: Main Control, Engineering, Life Support. Open internal hatches, closed exterior airlock.
- **Gameplay:** Trigger an equipment fault, inspect evolving telemetry and diagnostics, then repair.
- **Quest:** Native standalone Meta Quest 3 APK using Unity 6 LTS and URP.
- **Displays now:** Live-updating **simulated** telemetry from a local Unity data source; simulated diagnostics; AI monitor labeled **NOT CONNECTED**.
- **Displays later:** Genuine Mamba anomaly scores from an evaluated Python backend; optional model activation visualization, responsibly labeled.
- **Optional:** Real-time exterior surveillance camera view, subject to Quest performance.
- **Excluded from V1:** Multiplayer, outside walking, functional keyboards, interactive chairs, and hundreds of individual controls.

## Two separate development projects

```text
Lunaris-Edu-Labs/
  unity-vr-client/    Unity project, C# frontend; current development focus
  mamba-backend/      Independent Python / Mamba project; postponed until January
  protocol/           Language-neutral JSON transport schema and examples
  docs/               Setup and design documentation
  PLAN.md             Active frontend roadmap, future ML roadmap, honest status
  .gitignore
```

They are **independent projects in the same GitHub repository**. Unity must run offline with a local simulator and must not require Python to be installed. When the model is ready, the projects will communicate through a WebSocket protocol, without sharing runtime source code. We will never label placeholder scores as actual Mamba inference.

## First development milestone

1. Clone this repository on the laptop.
2. Install Unity 6 LTS with Android Build Support, Android SDK/NDK tools and OpenJDK.
3. In Unity Hub, create a new **Universal 3D (URP)** project at `unity-vr-client/` under the cloned repository root.
4. Configure Quest-compatible OpenXR + XR interaction.
5. Build an empty-room native Quest 3 APK, test on the actual headset.
6. Import Claude's habitat assets and start the frontend milestones.

Read [Unity setup](docs/UNITY_SETUP.md), [development plan](PLAN.md), and [provisional future data contract](protocol/schema.json).

## Development philosophy

AI can implement much of the **Unity frontend**, with the project owner testing and reviewing it. The **Mamba backend** is the owner's core TKS technical work: prioritize understanding, writing substantive code, evaluation and proper disclosure of AI assistance.

## Credits

Asset sources, authorship and licenses will be documented before release. AI-assisted work requires human review and on-device testing.
