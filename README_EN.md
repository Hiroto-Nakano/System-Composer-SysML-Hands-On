# System Composer Exercises

[日本語](README.md) | **English**

### From importing and executing a SysML model to refining requirements through detailed design.

<img width="1122" height="1402" alt="ChatGPT 画像 2026年10月24日 03_30_48" src="https://github.com/user-attachments/assets/efb6418f-a8a1-4805-b950-1fc14e856307" />

Using an electric throttle control system, you import the system architecture, run a model, and test its behavior against requirements. You then use the simulation results to identify a response issue, specify a detailed requirement, revise the design, and test again.

This repository includes two exercises, with handouts and solutions in Japanese and English.

| Exercise | Purpose | What you do |
| --- | --- | --- |
| **1. Importing and executing a SysML model** | Import the system architecture, inspect model behavior, and check compliance with existing requirements | Import XMI → inspect the architecture → simulate → test |
| **2. Specifying requirements through detailed design** | Turn a response characteristic revealed by simulation into a detailed requirement and improve the design | Inspect the waveform → add a requirement → observe a failing test → revise PID parameters → pass the tests |

[Open the English handout](SystemComposer_exercise_EN.pdf) · [日本語の演習資料を開く](SystemComposer_exercise.pdf)

## Exercise 1: Importing and executing a SysML model

### Import the architecture and examine the model's behavior

Start by importing the electric throttle XMI file with SysML Connector and inspecting the architecture in System Composer. After examining the system's structure, open the supplied project prepared for simulation and testing.

Run the Simulink model and inspect its output in the Simulation Data Inspector. Execute the tests in the Test Manager to confirm that the behavior satisfies the existing requirements.

| What you do | What you inspect |
| --- | --- |
| Import the [electric throttle XMI file](SysMLImport/SystemModels/ElectricThrottleControlSysMLModel.xml) with SysML Connector | The architecture imported into System Composer |
| Simulate `ElectricThrottleControl.slx` in the supplied execution project | The response waveforms in the Simulation Data Inspector |
| Open `TestFile/TestManagerFile.mldatx` and run the tests | The results of requirements-based testing |

**Use one example to connect architecture inspection, model execution, and requirements-based testing.** Instructions are on [page 1 of the handout](SystemComposer_exercise_EN.pdf#page=1), with solutions on pages 2–3.

## Exercise 2: Specifying requirements through detailed design

### Look more closely at the waveform after the existing test passes

The design satisfies the existing response requirement. However, a closer look at `PositionSensorVoltage` reveals a temporary drop as the response approaches its target.

This response characteristic was not specified by the high-level requirement alone. In Exercise 2, you turn that observation into the following detailed requirement:

> After the response starts, the drop in PositionSensorVoltage from its previous maximum must be no greater than 0.10 V.

In the Requirements Editor, add `3.1 Monotonic Response` beneath `3 Response`. Link it to the supplied monotonic-response test and run the test. The issue observed in the waveform now has a test result.

**After adding the detailed requirement: the existing step-response test passes, while the monotonic-response test fails.**

<img width="1442" height="833" alt="response-before-fail" src="https://github.com/user-attachments/assets/8d947a1d-3388-4d0e-9d63-b662e9230495" />

Compare the test results on the left with the orange response waveform. Although the existing test passes, the added criterion produces the red Fail interval.

### Revise the design and satisfy both requirements

Change the PID controller parameters, run the simulation, and compare the waveforms in the Simulation Data Inspector. Choose parameters that suppress the temporary drop while maintaining the existing response performance, then run the tests again.

**After revising the design: both the step-response test and the monotonic-response test pass.**

<img width="1442" height="833" alt="response-after-pass" src="https://github.com/user-attachments/assets/819e4af8-061a-4bdb-994a-e14981b90232" />

**In Exercise 2, you work through waveform inspection, requirement definition, test linking, design revision, and re-verification yourself.** Instructions are on [page 4 of the handout](SystemComposer_exercise_EN.pdf#page=4), with solutions on pages 5–6.

## Materials and getting started

| Language | Exercises and solutions PDF | PowerPoint |
| --- | --- | --- |
| 日本語 | [Japanese handout](SystemComposer_exercise.pdf) | [Japanese slides](SystemComposer_exercise.pptx) |
| English | [English handout](SystemComposer_exercise_EN.pdf) | [English slides](SystemComposer_exercise_EN.pptx) |

Begin Exercise 1 by importing the XMI file with SysML Connector, following the handout. For model execution and testing, use the corresponding project below.

| Purpose | MATLAB project to open |
| --- | --- |
| Exercise 1: Model execution and testing | [SysMLImport/SysMLArchModel/SysMLArchModel.prj](SysMLImport/SysMLArchModel/SysMLArchModel.prj) |
| Exercise 2: Specifying requirements through detailed design | [SimDrivenReqRefinement/SysMLArchModel.prj](SimDrivenReqRefinement/SysMLArchModel.prj) |
| Exercise 2 solution | [SimDrivenReqRefinement/SimDrivenReqRefinement_ans/SysMLArchModel.prj](SimDrivenReqRefinement/SimDrivenReqRefinement_ans/SysMLArchModel.prj) |

## Products used

The exercises use MATLAB, Simulink, System Composer, Requirements Toolbox, and Simulink Test. Importing the SysML model also uses [SysML Connector](https://www.mathworks.com/products/sysml.html).

## References and contributions

These materials build on the models, requirements, and tests in [mathworks/JP-SysML-Connector-Simple-Workflow](https://github.com/mathworks/JP-SysML-Connector-Simple-Workflow) and were developed in part in collaboration with 鎌谷. Exercise 2 incorporates 鎌谷's advice on extending the training story from verifying existing requirements to discovering missing requirements, revising the design, and verifying again.

See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for source attribution and copyright notices.

## License

The exercise materials and original additions and modifications created for these exercises may be used for personal, non-commercial study. Commercial use, including use in paid training courses and the sale of these materials or modified versions, requires prior written permission from The MathWorks, Inc. See [LICENSE](LICENSE) for the scope and terms.

Upstream material remains under BSD-3-Clause. The upstream copyright notices and license are retained.
