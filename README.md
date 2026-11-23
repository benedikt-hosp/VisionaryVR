# VisionaryVR

Research code accompanying the **VisionaryVR** publication: a Unity project for running controlled vision experiments in virtual reality, with eye tracking, depth calibration, autofocal-display control, questionnaires and structured logging.

- **Paper:** the publication on VisionaryVR (B. W. Hosp et al.). No DOI is given in this repository; see the reference list of the paper.
- **Status:** research code, not maintained. Issues and pull requests may not be answered.
- **Unity version:** 6000.0.11f1.
- **License:** MIT, see [LICENSE](LICENSE). The license covers the code in this repository only, **not** the third-party SDKs and plugins listed below.

## What is in this repository

- `Assets/Scripts/`: experiment management (state machine, conditions, protocols), eye-tracking controller modules (`Module_ETController`), depth calibration and regression (`Module_DepthCalibration`), autofocal controller (`Module_AutofocalController`), experiment recorder and logging (`DataInformation`, `Module_ExperimentRecorder`), questionnaire UI (`Source/DataInformation`), XTAL / SteamVR controller input (`Module_VrgControllers`).
- `Assets/Resources/`: protocols (`Protocols/`), questionnaires (`Questionnaires/TLX.json`, `PIS.json`), UI prefabs, instruction images and stimulus textures.
- `Assets/Scenes/`: main menu, base, experiment and questionnaire scenes.
- `Assets/Resources/EyeTrackingProviders/*/*Provider.cs`: the adapter scripts for the supported eye trackers (SDKs not included, see below).

No study data are included. Log files and questionnaire results are written by the experiment at run time and are excluded by `.gitignore`.

## Third-party SDKs

The vendor SDKs and several third-party plugins are **not** included, because their licenses do not allow redistribution or because they are large binaries. Download them yourself and copy them to the folders below (paths relative to `Assets/`).

| Component | What to download | Where to put it |
|---|---|---|
| Tobii Pro SDK (Unity) | Tobii Pro SDK for Unity from Tobii (End User License Agreement applies) | `Resources/EyeTrackingProviders/TobiiPro/` (next to `TobiiProProvider.cs`) |
| Tobii XR SDK | Tobii XR SDK Unity package from Tobii | `Resources/EyeTrackingProviders/TobiiXR/` (next to `TobiiXRProvider.cs`) |
| HTC Vive Pro Eye (SRanipal) | SRanipal / Vive Eye Tracking SDK from HTC | `Resources/EyeTrackingProviders/SuperRealityAnipal/ViveSR/` |
| XTAL (VRgineers) | XTAL Unity plugin from VRgineers | `Resources/EyeTrackingProviders/XTAL/vrgineers/` (next to `XTALProvider.cs`) |
| SteamVR Unity Plugin | <https://github.com/ValveSoftware/steamvr_unity_plugin> (also in the Unity Asset Store) | `SteamVR/` (default location). After import, let the plugin regenerate its input actions; `Assets/SteamVR_Input/` is generated code. |
| Libraries for depth calibration, recording and networking | NuGet / vendor downloads: Emgu.CV, Newtonsoft.Json, SharpLearning (AdaBoost, Containers, CrossValidation, DecisionTrees, Ensemble, FeatureTransformations, GradientBoost, InputOutput, Metrics, Optimization, RandomForest, XGBoost, Common.Interfaces), XGBoost.dll and libxgboost.dll, SkLearnForNet, websocket-sharp, OpenH264 (openh264-2.3.1-win32.dll) | `Plugins/` |
| NuGetForUnity | NuGetForUnity (its editor DLL) | `NuGet/Editor/` |
| Room and interior models (desk, keyboard, mug, screen, smartphone, TV) | Not redistributed (license unclear). Use your own models. | `Room/` |

Notes:

- The folders above are listed in `.gitignore`.
- Without the SDKs the project does not compile as is. Import the SDKs of the eye tracker you use and the plugins in `Plugins/`, or remove the modules you do not need.
- `Assets/Prefabs/Interior*.prefab` and the experiment scene refer to the removed room models and show missing references until you assign your own.
- `Assets/Scenes/02_Experiment/Content/` contains Roboto Condensed fonts (Apache License 2.0).
