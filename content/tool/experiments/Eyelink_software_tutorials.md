---
title: "Eyelink software tutorial"
date: 2025-01-28
draft: false

---

## Introduction to Experiment Builder: A Step-by-Step Guide

### Overview
This tutorial provides a fundamental understanding of the Experiment Builder software. You'll learn about its user interface, core components, and how to structure experiments using sequences, triggers, and data sources.


### **Introduction to Experiment Builder**

Welcome to the Experiment Builder introductory tutorial series! This guide will walk you through the basics of using Experiment Builder, a Python-based programming environment with a graphical drag-and-drop interface designed for creating experimental designs.

---

## **What is Experiment Builder?**

Experiment Builder is a powerful tool for creating experimental designs with the following features:

- **Graphical Interface:** Drag-and-drop interface for intuitive programming.
- **EyeLink Integration:** Built-in support for implementing eye-tracking experiments, including gaze-contingent designs.
- **Stimuli Presentation:** Precise control over visual stimuli (images, videos, text) and audio timing down to the screen retrace level.
- **Data Analysis Features:** Tools to auto-segment text into interest areas and track smooth pursuit targets over time for easier data comparison.
- **Cross-Platform Support:** Compatible with both Windows and macOS. Projects can be edited and opened seamlessly across both platforms.

---

### ** Tutorial 1: Experiment Lifecycle in Experiment Builder**

The typical process for designing an experiment in Experiment Builder includes the following steps:

#### **1. Creating and Saving a Project**

1. Open the Experiment Builder application and use the **graphical user interface** to design the experiment by building a flowchart.
2. Save your project by specifying:
   - **Name of the project.**
   - **Location to save the project.**
3. Saving creates a folder structure for your experiment.  
   Example: The Posner task example project follows this structure.  
   - The main folder contains a file called `graph.ebd`.  
   - Open the project by double-clicking the `graph.ebd` file or loading it through the Experiment Builder interface.

> **Note:** Always manage files within Experiment Builder. Avoid manually editing or deleting files in the project folder.

---

### **2. Packaging a Project**

If you need to share or move a project (e.g., send to a colleague), use the **File → Package** command. This will:

- Create a single `.ebz` file.
- Use **File → Unpack** to expand it back into a full project folder.

---

#### **3. Test Running the Experiment**

1. Perform a **test run** to ensure everything works as intended:
   - Go to **Experiment → Test Run** or click the **play button** in the toolbar.
2. The test run will:
   - Generate an EyeLink data file.
   - Allow you to verify the collected data for analysis.

> **Important:** Test runs should not be used for actual participant data collection. Only the latest test run's data file is saved, and previous test data is overwritten.

---

#### **4. Deploying the Experiment**

Once the experiment is finalized:

1. Go to **Experiment → Deploy**:
   - This creates a new folder containing an executable file (replacing the `graph.ebd` file).
2. Use this **deployed folder** for real participant data collection:
   - Run the experiment by double-clicking the executable file.
   - Each run will prompt you to enter an **EDF file name** (EyeLink Data File).  
   - At the end of the run, the EDF file will be saved in the deployed folder's `results` subfolder.

---

#### **5. HASP License Key**

- A license key is required to build and edit experiments.  
- However, you **do not need a license key** to run deployed experiments for data collection.

---

#### **6. Data Analysis Preparation**

When preparing for data analysis, ensure that you:

1. Copy the **entire deployed project folder** to the analysis computer, not just the EDF files.
2. The deployed folder contains:
   - Image and video files.
   - Interest area files essential for analysis in Data Viewer.

> **Tip:** Without the full folder, you may lose access to experimental stimuli and interest area data during analysis.

---

#### **Summary**

Experiment Builder simplifies experimental design and eye-tracking data collection with its graphical interface and precise timing controls. By following this guide, you’ll be able to:

1. Create and save projects effectively.
2. Perform test runs to ensure proper functionality.
3. Deploy experiments for real data collection.
4. Prepare for data analysis with all necessary files.

For more details, refer to the official documentation or continue to the next tutorial in this series.


-------------------------------------------

### Tutorial 2: Graphical User Interface Overview

#### 1. Getting Started with Experiment Builder
Before building an experiment, it's essential to understand the interface and key elements.

#### User Interface Overview
The Experiment Builder interface consists of three main sections:

**Graph Editor Window (Right Panel):**
- The main workspace where you construct experiments using nodes to create a flowchart.

**Experiment Component Toolbox (Top Panel):**
- Contains different nodes categorized into:
  - **Action Nodes** – Perform actions like displaying stimuli or recording responses.
  - **Trigger Nodes** – Wait for events (e.g., keypress, mouse click) before proceeding.
  - **Other Nodes** – Handle variables and special functions.

**Left-Side Panels:**
- **Overview Panel** – Allows quick navigation within the Graph Editor.
- **Structure Panel** – Provides a hierarchical view of the project and hardware settings.
- **Properties Panel** – Displays properties of selected nodes and allows editing.
- **Notes Panel** – Used for adding comments to nodes for record-keeping.

#### 2. Adding Components to an Experiment
##### Action Nodes (Defining Experiment Steps)
These nodes execute specific tasks, such as:
- **Display Screen** – Presents stimuli on the screen.
- **Drift Check** – Ensures eye-tracking stability.
- **Play/Record Audio** – Handles auditory stimuli.

##### Trigger Nodes (Handling User Input)
Trigger nodes control when the experiment advances:
- **Keyboard Trigger** – Waits for a specific keypress.
- **Mouse Trigger** – Detects a mouse click at a specified location.
- **Eye-Based Triggers** – Detect gaze-contingent events (not used in this example).

##### Other Nodes (Managing Data & Variables)
- **Variable Nodes** – Store values like reaction times and accuracy.

#### 3. Using Sequences to Structure an Experiment
##### Sequences (Blue Rectangles):
- Special action nodes that repeat the same structure multiple times.
- Used to create blocks and trials in experiments.

##### Data Sources (Defining Trial Conditions):
- Allows customization of stimuli and responses across trials.
- Each row represents a trial; each column represents a changing variable (e.g., stimulus name, location).

##### How to Use Data Sources in a Sequence
- Click on the Data Source property of a sequence.
- Define variables (e.g., stimulus file names, correct responses).
- Reference these variables in node properties to dynamically change trial conditions.
- Enable randomization to shuffle trial orders.

#### 4. Summary & Next Steps
- The Graph Editor is where you visually structure your experiment.
- Nodes are essential building blocks categorized into actions, triggers, and variables.
- Sequences allow repetition of trial structures with varying stimuli.
- Data Sources ensure trial conditions change dynamically while keeping the experiment structured.


---------------------------------------------------

### Tutorial 3: Overview of the Posner Task


## Overview of the Experiment Design  

In this video, we will discuss the design of the experiment covered in this tutorial series. We will highlight various components of the project that handle different aspects of the experiment as we go along. However, this video primarily provides an overview of the methodological design.  

For more detailed information regarding the implementation of different aspects of the design, please refer to other videos in the series.  

This tutorial series uses the **Posner Task** to illustrate the fundamental concepts of **Experiment Builder**. The goal is to demonstrate how Experiment Builder works within the context of a familiar task.  

This implementation of the Posner Task showcases how to:  

- Present different stimuli on each trial  
- Modify stimulus characteristics such as location  
- Randomly assign variables that control timer duration  
- Randomize trial and block orderings  
- Collect participant responses and log response data  

While specific experimental paradigms may differ, the techniques demonstrated in this example can be applied to other paradigms. The tutorial aims to introduce fundamental building blocks, techniques, and best practices for implementing any experimental task.  

---

#### Posner Task Structure  

The **Posner Task** presented in this tutorial consists of a series of trials, each composed of several key events:  

##### 1. Fixation & Cue Presentation  
- The trial begins with a **fixation cross** and **two placeholder boxes** on the left and right.  
- A **cue** appears centrally near the fixation cross, which can be:  
  - **Valid**: The cue correctly predicts the target location.  
  - **Invalid**: The cue indicates the opposite side of the target.  
  - **Neutral**: The cue does not provide location information.  
- The cue remains on the screen for **500 milliseconds** before disappearing.  

##### 2. Target Onset & Response Collection  
- After a **randomly chosen interval**, a target appears in one of the two placeholder boxes.  
- The participant must press one of two keys to indicate whether the target is on the left or right:  
  - `Z` key → **Left target**  
  - `/` key → **Right target**  

##### 3. Predictions & Attention Effects  
- Participants are expected to respond **faster** to targets preceded by a **valid cue**, as attention is directed toward the target location.  
- This attentional shift may also result in **faster eye movements** toward the target position.  

---

## Implementing the Posner Task in Experiment Builder  

The experiment is implemented as an **EyeLink experiment** within **Experiment Builder**. The procedure follows these steps:  

##### 1. Camera Setup & Calibration  
- At the start, **camera setup and calibration instructions** are presented.  
- The **camera setup action** puts the **Host PC** and **Display PC** into a special camera mode for **eye tracker calibration**.  

##### 2. Trial Blocks & Instructions  
The experiment consists of **three blocks of trials**:  

- **Practice Block**: 2 trials  
- **Experimental Blocks**: 10 trials each  
  - 4 **valid** trials  
  - 1 **invalid** trial  
  - 5 **neutral** trials  

The **practice block always appears first**, but the order of experimental blocks is **randomized**. Within each block, the **trial order is also randomized**.  

##### 3. Trial Execution  
Each trial follows this sequence:  

1. **Fixation cross** and **placeholder boxes** appear (*1000 milliseconds*).  
2. The **cue appears** and remains for *500 milliseconds*, then disappears.  
3. After a **random delay**, the **target appears** (*up to 5000 milliseconds*).  
4. The participant presses the appropriate key (`Z` or `/`).  
5. **Immediate feedback** is provided (correct or incorrect).  
6. If **no response** is made within *5 seconds*, the trial times out, and a message prompts the participant to respond faster.  
7. Feedback remains on-screen for **2 seconds**, followed by a **blank screen**.  

### 4. Experiment Completion & Data Transfer  
- After all **22 trials**, the experiment **ends automatically**.  
- The **EDF data file** is transferred from the **Host PC** to the **Display PC**.  

---

#### Test Run of the Posner Task  

To test the experiment **without** an **EyeLink Host PC** or **eye tracker**, we can enable **Dummy Mode** in Experiment Builder.  

##### Enabling Dummy Mode  
1. Navigate to the **EyeLink section** in the **Devices tab** of the **Structure Panel**.  
2. Check the box for **Dummy Mode** to disable eye tracking functionality.  
3. This prevents the experiment from attempting to connect to a **Host PC**.  

##### Running the Experiment  
1. Go to **Experiment → Test Run**.  
2. When prompted for an **EDF file name**, use the default:  

   ```plaintext
   test.edf
   ```

3. Since Dummy Mode is enabled, a notification will confirm this.

4. The program will ask which counterbalanced version of the experiment to use.

      This project includes two versions of the experiment.
      Select a version to proceed.
5. The experiment begins as usual.

##### Key Points During Test Run
Instructions and block transitions function as they would in a real experiment.
The camera setup mode and drift check procedures are automatically skipped.
The participant proceeds through practice trials and then experimental trials.
A break screen appears between blocks.
Pressing any key on the Display PC continues the experiment.
Ending the Experiment Early
To terminate a test run, press:
  ```CTRL + C```

   - CTRL + C ensures proper shutdown and retrieval of the EDF file from the Host PC.
   - Even in Dummy Mode (where no data transfer occurs), CTRL + C remains the best exit method.
   - This method is recommended for both test runs and real data collection.


##### Conclusion
This tutorial introduces the Posner Task implementation in Experiment Builder using EyeLink. The experiment follows a structured trial sequence, including fixation, cueing, response collection, and feedback.

The tutorial also demonstrates how to enable Dummy Mode for test runs and highlights best practices for running and terminating experiments.

For further details on EyeLink setup and experiment implementation, refer to the additional learning materials linked in the video description.


------------------------------------------

### Tutorial 4: Hardware settings


#### Introduction  

When setting up an **Experiment Builder** project, one of the first steps is to **configure hardware properties**. These settings ensure proper communication between the experiment software and devices such as **eye trackers, display screens, and audio equipment**.  

This tutorial will guide you through the necessary steps to configure:  

- **Eye tracker type and settings**  
- **Display resolution and refresh rate**  
- **Background color for consistency**  
- **Audio and other external devices**  

---

#### Accessing Hardware Settings  

You can edit hardware properties in **two ways**:  

1. **Devices Tab (Structure Panel)**  
   - Open the **Devices tab** in the **Structure panel** to quickly access and modify hardware settings.  

2. **Preferences Menu**  
   - Go to **Edit → Preferences**  
   - Navigate to the **Devices** section under **Preferences**  
   - Adjust hardware settings from there  

---

#### **Setting Up the Eye Tracker**  

##### **Choosing Your Eye Tracker Type**  

The first step is to specify the type of **EyeLink** eye tracker being used. This is done under the **EyeLink section** in the **Devices tab**.  

- Configuring these properties allows Experiment Builder to send the correct **commands** to the **Host PC** for proper hardware setup.  
- If you **do not** want Experiment Builder to send configuration commands, you can set these properties to `"current"` (explained later).  

### **Selecting Your Eye Tracker Model**  

From the **Tracker Version** dropdown menu, choose the **EyeLink model** you are using:  

- **EyeLink 1 or 2** → Simply select the correct version.  
- **EyeLink 1000** → Additional settings for mount type and illuminator position.  
- **EyeLink 1000 Plus** → Similar to the EyeLink 1000, but without the illuminator position setting.  
- **EyeLink Portable Duo** → Only requires selecting the mount usage mode.  

#### **Configuring EyeLink 1000 and 1000 Plus Settings**  

If using **EyeLink 1000** or **1000 Plus**, specify additional properties:  

##### **1. Mount Type**  
- **Tower Mount**  
- **Desktop Mount**  
- **Arm Mount**  
- **Long-Range Mount**  

##### **2. Illuminator Position (for Desktop Mount only, EyeLink 1000)**  
- **Left**  
- **Right**  

##### **3. Mount Usage**  
- **Head Stabilized Mode (Chin Rest)**  
- **Head Free Remote Mode**  
- **Monocular vs. Binocular Tracking**  

For **EyeLink 1000 Plus**, you can use **binocular tracking in head-free mode**, unlike the standard EyeLink 1000.  

### **Configuring EyeLink Portable Duo**  

For **EyeLink Portable Duo**, select one of the following:  

- **Head Stabilized (Chin Rest) Mode**  
- **Head Free Remote Mode**  

##### **Using "Current" for Custom Host PC Settings**  

If you prefer to configure the **eye tracker settings manually on the Host PC**, you can select **"current"** in the properties menu.  

- This prevents Experiment Builder from **overriding** existing Host PC settings.  
- The Host PC will use whatever **configuration** has already been selected in its interface.  

---

#### **Setting Display Screen Resolution and Refresh Rate**  

When running an **Experiment Builder** project, the software **temporarily changes the monitor's resolution and refresh rate** based on the display settings in the project.  

##### **1. Why Correct Display Settings Matter**  
- **Positioning of stimuli** is based on **pixel coordinates**, so the resolution must be accurate.  
- A **higher refresh rate** is important for **gaze-contingent** studies, ensuring rapid screen updates.  

##### **2. Choosing the Best Resolution and Refresh Rate**  
- **Use the native resolution** of the monitor → Maximizes performance and timing accuracy.  
- **Set the highest refresh rate** the monitor supports → Critical for studies requiring fast visual updates.  

###### **Example Settings (Standard Monitor)**
| Setting        | Recommended Value |
|---------------|------------------|
| Resolution    | **Native resolution** (e.g., 1920×1080) |
| Refresh Rate  | **60 Hz** (or higher if supported) |

For this tutorial’s experiment, **60 Hz and native resolution** are used, as **no gaze-contingent features** require ultra-fast updates.  

---

#### **Maintaining a Consistent Background Color**  

Ensuring a **consistent background color** across all stages of the experiment is **critical** for maintaining calibration accuracy.  

##### **1. Why Background Color Matters**  
- **Sudden changes in brightness** between calibration, drift check, and stimuli presentation **affect pupil size**.  
- This variation can **disrupt eye tracker calibration** and reduce accuracy.  

##### **2. Setting a Uniform Background**  
To prevent large pupil size fluctuations:  

- **Use the same background color** for:  
  - **Camera Setup**  
  - **Drift Check & Drift Correction**  
  - **Display Screen Actions**  
  - **Stimulus Presentation**  

For this tutorial, a **gray background** is used **throughout the experiment** to minimize pupil dilation changes.  

##### **3. Pre-setting Background Color in Preferences**  
- If you set the background color **in preferences before adding nodes**, all newly created nodes will automatically **match the chosen color**.  
- This saves time and ensures **consistency** across the experiment.  

---

#### **Configuring Audio and Other External Devices**  

If your experiment includes **audio playback** or uses **additional hardware devices**, configure them in the **Devices tab**.  

##### **1. Checking Audio Properties**  
- Ensure that the **correct audio device** is selected.  
- Test audio playback to verify **volume levels** and **latency**.  

##### **2. Managing Additional Devices**  
- If using response boxes, button presses, or other external input devices, set their properties correctly.  
- Experiment Builder will automatically detect and allow configuration for **compatible devices**.  

---

#### **Saving Default Hardware Settings**  

To **save your project settings as defaults**, follow these steps:  

1. Go to **Edit → Preferences**  
2. Navigate to the **Devices** section  
3. Click **Save as Defaults**  

This ensures that **future projects** automatically apply the same hardware settings, reducing setup time.  

---

## **Summary**  

In this tutorial, we covered **essential hardware settings** in Experiment Builder, including:  

✔ **Selecting the correct EyeLink model and configuring tracking options**  
✔ **Setting the display resolution and refresh rate for accurate stimulus presentation**  
✔ **Ensuring a uniform background color to maintain pupil stability**  
✔ **Configuring audio and external devices**  
✔ **Saving settings as defaults for future projects**  

By properly setting up hardware configurations, you ensure **smooth experiment execution** and **accurate data collection**. 🚀  

---
