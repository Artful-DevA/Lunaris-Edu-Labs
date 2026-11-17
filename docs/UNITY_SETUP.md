# First laptop setup | Unity + Meta Quest 3

## Important
The repository is **not yet a complete Unity project**. Cloning it is the first step; create the Unity editor project after cloning, in `unity-vr-client`. This keeps Unity's generated `Assets/`, `Packages/`, and `ProjectSettings/` in source control.

## Before you begin
- Your laptop dual-boots Windows 11 and Ubuntu 26. Unity's officially supported Linux list may not include Ubuntu 26, so Windows 11 is the simpler first path.
- Install Unity Hub and a **Unity 6 LTS** editor. Use a version compatible with the project and stick to it afterward.
- During editor install enable **Android Build Support**, **Android SDK & NDK Tools**, and **OpenJDK**.
- Install Git (or GitHub Desktop on Windows).
- Enable Meta Quest developer mode using the official Meta developer instructions and allow USB debugging.

## Clone
Git terminal:
```bash
git clone https://github.com/Artful-DevA/Lunaris-Edu-Labs.git
cd Lunaris-Edu-Labs
```
Alternatively, GitHub Desktop → File → Clone Repository → Artful-DevA/Lunaris-Edu-Labs.

## Create Unity project
1. Unity Hub → New project.
2. Pick a supported **Universal 3D (URP)** template.
3. Project name: `unity-vr-client`.
4. Project location: **the cloned repo root**, so project files appear directly at `Lunaris-Edu-Labs/unity-vr-client/Assets`, `Packages`, `ProjectSettings`. Double-check the preview path before clicking Create.
5. Open project; ensure editor opens and saves cleanly.
6. Install XR Interaction Toolkit and OpenXR Plugin via Package Manager according to documentation for the chosen editor.
7. Enable OpenXR for Android, add Quest-compatible features and controller profiles, verify Input System and XR interaction configuration.
8. Switch Build Profile / Build Settings to Android; use ARM64 and suitable graphics settings.
9. Use a minimal XR Origin test scene. Build and Run to Quest via USB.
10. Check head tracking and controllers on-device, then commit only source/project files.

## Git after Unity creates the project
```bash
git status
git add .
git commit -m "feat: initialize Unity URP Quest project"
git push
```
Review `git status` before adding anything. Do **not** commit generated `Library/` or huge binary builds. The first `git status` may take time while the editor is creating assets.

## Later 3D assets
Request one full assembled reference scene and separated Unity-compatible modules from Claude, all exported using a shared origin and real-world meter scale. Actual scene assembly and VR profiling will be later steps.
