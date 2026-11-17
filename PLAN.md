# Lunaris Edu Labs | Build Plan

Updated: 2026-11-17

## Non-negotiable requirements
- **Primary hardware:** standalone Meta Quest 3 APK. PCVR is optional, not a prerequisite.
- **Game:** One indoor three-module habitat; internal hatches open; exterior airlock closed; no exterior gameplay in V1.
- **Critical feature:** live telemetry, real Mamba inference scores, and genuine diagnostics, with simulator ground truth separated from ML output.
- **Backend:** Python simulator + FastAPI WebSocket + evaluated Mamba time-series anomaly detector. Deploy to remotely hosted service. Free hosting is *not yet secured*: benchmark portable CPU inference and verify provider limitations before choosing. Do not depend on a home PC being online.
- **Fallback:** On cloud disconnection, game stays playable but labels AI offline. Optional *explicitly labeled* replay mode must never appear to be live inference.
- **Performance:** Quest 3 72 Hz target, verified with on-device profiling. 3D assets must be imported at consistent metric scale with separated controls and monitor surfaces.
- **AI evaluation:** train/validation/test separated by simulation run or chronological window as appropriate; compare against Isolation Forest with fair temporal features and threshold-based baselines; report precision, recall, F1, false-alarm rate, detection delay, model latency, and limitations. Never claim Mamba's hidden state is an explanation.

## Phase 0 | Repository and development environment
- [x] Create GitHub repository and README
- [x] Establish project plan, Git ignore, shared protocol, setup instructions
- [ ] Clone on laptop and install Unity 6 LTS + Android build modules
- [ ] Create Unity URP project inside `unity-vr-client/`
- [ ] Set up OpenXR + Quest controller input
- [ ] Deploy a simple native Quest 3 APK that tracks head and controllers

**Exit criterion:** a small scene launches on Quest 3. No model assets required.

## Phase 1 | Habitat and interaction slice
- [ ] Import Claude's source/model exports (editable original + clean FBX/glTF + textures)
- [ ] Verify transforms, meters, scale, normals, colliders and materials
- [ ] Assemble Main Control, Engineering, Life Support and open internal hatches
- [ ] Add comfortable VR locomotion (prototype specialized lunar arm motion separately)
- [ ] One physical failure/repair control and one functioning sensor monitor
- [ ] Confirm 72 Hz performance by profiling actual Quest build

**Exit criterion:** player walks indoors, triggers an event, sees telemetry change, repairs it.

## Phase 2 | Mamba R&D and robust backend
- [ ] Generate labeled, physically motivated, multichannel synthetic habitat telemetry; document assumptions and fault injections
- [ ] Implement portable Mamba model and real training pipeline
- [ ] Train & compare Isolation Forest and threshold / temporal baselines using leakage-resistant splits
- [ ] Benchmark CPU inference on intended cloud architecture; preserve GPU training path
- [ ] Implement validated, versioned WebSocket protocol, per-session state, reconnect, error states
- [ ] Provision candidate free hosting ONLY after proving inference and long-lived connections are feasible
- [ ] Build clear provenance labeling for live AI predictions vs diagnostics vs ground truth

**Exit criterion:** real model predictions arrive via WebSocket, measured and reproducible.

## Phase 3 | Unity monitoring and showcase
- [ ] Map telemetry & anomaly messages to in-world UI
- [ ] Show real graphs, anomaly scores, timestamp, latency and fault-state diagnostics
- [ ] Failure injection and repair send command/ack messages; validate gameplay loop
- [ ] Optional exterior camera via RenderTexture, limited rate & device profiling
- [ ] Finish materials, lights, sounds, tutorial, offline/connection states
- [ ] Test repeated Quest sessions, intermittent Wi-Fi, cloud cold start & reconnection
- [ ] Collect benchmark report, demo recording, reproducibility documentation

**Exit criterion:** a repeatable Quest 3 showcase with real, documented Mamba inference.

## Decisions deferred
- Actual Unity package versions until editor project is created on laptop.
- Mamba variant and trained checkpoint until research evaluation.
- Oracle Cloud vs Cloud Run hosting until proof of CPU and network viability.
- Optional PCVR, multiplayer, working keyboards, exterior exploration until after V1.

## Milestone log
- 2026-11-17: project initialized remotely in GitHub. No Unity editor project has been created or tested.
