# Lunaris Edu Labs | Development Plan

Updated: 2026-11-17
Target: TKS Create, April 2027 (exact submission date to be confirmed).

## Current decision: Unity frontend first

**November–December 2026:** Focus on developing and testing the standalone Quest 3 game. **Do not start implementing or training the Python/Mamba backend unless the project owner explicitly asks.** This is intentional scope control, not a technical shortcut. Revisit backend work in **January 2027**.

**January–February 2027 (tentative):** The project owner leads the Python telemetry research, Mamba training and evaluation, with AI assistance for explanation, code review and debugging.

**March–April 2027 (tentative):** Integrate the evaluated backend with the Quest client, test networking and gameplay, finish documentation and presentation. Dates are flexible; reserve time for TKS Iterate requirements and other commitments.

## Strict codebase boundary

```text
Lunaris-Edu-Labs/
├── unity-vr-client/  # standalone Unity project; Unity/C# only
├── mamba-backend/    # independent Python project; leave unimplemented until January
├── protocol/         # language-neutral versioned wire format; no runtime dependencies
└── docs/
```

- Unity runs **without** Python, cloud services, or Mamba during the frontend-first phase.
- Temporary telemetry comes from a small **local Unity simulation**. Label its values and diagnostics as **SIMULATED**.
- Until real model inference is available, displays must say **AI OFFLINE / NOT CONNECTED**. Never fabricate a Mamba anomaly score and present it as real.
- Design a replaceable data-source boundary in Unity so a future WebSocket telemetry provider can replace the local provider without rewriting monitor UI.
- Neither runtime imports code from the other. They communicate later using `protocol/` JSON messages over WebSockets.
- The backend is the owner's core TKS technical contribution: the owner should code meaningful portions of the simulation, training and evaluation.
- Keep Unity assets, packages and project settings inside `unity-vr-client/`. Python environment and dependencies belong only in `mamba-backend/`.
- At present these are **separate projects in one GitHub repository**, not separate GitHub repositories.

## Frontend milestones (the only active development track for now)

### F0 | Clone and Quest 3 setup
- [x] Initialize GitHub repository, documentation, gitignore and proposed protocol
- [ ] Install Unity 6 LTS with Android SDK, NDK and OpenJDK on laptop
- [ ] Clone repository and generate Unity URP project inside `unity-vr-client/`
- [ ] Configure OpenXR / Quest controller input
- [ ] Build an empty room APK and test Quest headset/controller tracking

**Done when:** standalone APK boots with correct VR tracking.

### F1 | Walk through the lunar base
- [ ] Import Claude's assembled reference scene and exported modules
- [ ] Validate coordinate system, meters, room/corridor alignment, normals, materials and scale
- [ ] Build Main Control, Engineering and Life Support scenes/prefabs
- [ ] Add performance-conscious lighting, colliders, and comfortable movement
- [ ] Test performance and readability in Quest 3

**Done when:** player can navigate the actual indoor habitat at an acceptable on-device frame rate.

### F2 | Interactive monitoring without backend
- [ ] Implement local, deterministic simulated sensor streams with a fault-injection control
- [ ] Display **live-updating simulated telemetry** graphs on the in-world monitors
- [ ] Add **simulated system diagnostics** and fault/repair interactions
- [ ] Reserve a screen for an exterior camera feed, subject to Quest performance
- [ ] Clearly label Mamba panel as **AI NOT CONNECTED**
- [ ] Add swappable telemetry-source interface for future server data
- [ ] Test the event cycle on Quest: trigger failure → see graph change → inspect diagnostics → repair

**Done when:** a complete self-contained VR gameplay loop works offline. This does **not** count as completed ML.

### F3 | Frontend polish, only if time permits before January
- [ ] Upgrade usability, visuals, ambient audio, user onboarding and graceful offline states
- [ ] Prioritize one polished interactive workstation over dozens of decorative controls
- [ ] Profile additional cameras and monitor refresh rates on real headset

## Backend research (deliberately deferred)

### B0 | Define real ML task and dataset
- [ ] Specify multichannel telemetry, fault types, and assumptions
- [ ] Author/test dataset generator, sequence windows and careful data splits
- [ ] Establish simple, honestly evaluated threshold / temporal baselines

### B1 | Implement and evaluate genuine Mamba
- [ ] Choose a verifiable Mamba implementation, ensure CPU inference portability
- [ ] Owner codes meaningful parts of data processing, training loop, anomaly scoring and evaluation
- [ ] Train and evaluate without train/test leakage
- [ ] Compare with Isolation Forest and threshold/temporal baselines
- [ ] Report precision, recall, F1, false alarms, detection delay, and inference latency
- [ ] Document what is simulation ground truth, what is heuristic diagnostics and what is model output

### B2 | Remote inference, then integration
- [ ] Prototype FastAPI WebSocket transport and session management
- [ ] Benchmark resource needs before selecting a cloud host; no assumption free-tier cloud is viable
- [ ] Keep Quest independent of the user's laptop while playing
- [ ] Switch Unity telemetry provider from local to server data, retaining an honest offline mode
- [ ] Display actual model score, threshold and timestamp only when supplied by trained model
- [ ] Validate latency, dropped connections, cold starts and failure response

## Scope guardrails

- Standalone Quest 3 APK first; PCVR optional.
- Interior-only three-module habitat. Internal hatches can remain open, exterior airlock closed.
- Essential interactions: fault injection, diagnostics, repair, monitor selection.
- Not priorities: functional keyboards/chairs, multiplayer, exterior exploration.
- 72 Hz is a performance target that must be validated on the device, not assumed.
- No AI-generated score should be represented as genuine Mamba inference until training and serving have been implemented and tested.

## Status log

- 2026-11-17: Repository foundation committed. No working Unity project/APK or trained Mamba exists yet.
- 2026-11-17: Plan revised to Unity-first; backend explicitly paused until January 2027.
