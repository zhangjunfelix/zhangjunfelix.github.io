---
title: "Eyelink Experimental Builder tutorial"
date: 2025-01-28
draft: false

---

## Introduction to Experiment Builder: A Step-by-Step Guide
[video link](https://www.youtube.com/playlist?list=PLOdF-B36TwspI-XgKuRC2xFfa768Lsngv)

### Overview
This tutorial provides a fundamental understanding of the Experiment Builder software. You'll learn about its user interface, core components, and how to structure experiments using sequences, triggers, and data sources.


### Introduction to Experiment Builder

Welcome to the Experiment Builder introductory tutorial series! This guide will walk you through the basics of using Experiment Builder, a Python-based programming environment with a graphical drag-and-drop interface designed for creating experimental designs.

#### **What is Experiment Builder?**

Experiment Builder is a powerful tool for creating experimental designs with the following features:

- **Graphical Interface:** Drag-and-drop interface for intuitive programming.
- **EyeLink Integration:** Built-in support for implementing eye-tracking experiments, including gaze-contingent designs.
- **Stimuli Presentation:** Precise control over visual stimuli (images, videos, text) and audio timing down to the screen retrace level.
- **Data Analysis Features:** Tools to auto-segment text into interest areas and track smooth pursuit targets over time for easier data comparison.
- **Cross-Platform Support:** Compatible with both Windows and macOS. Projects can be edited and opened seamlessly across both platforms.

---

### Tutorial 1: Experiment Lifecycle in Experiment Builder**

The typical process for designing an experiment in Experiment Builder includes the following steps:

#### 1. Creating and Saving a Project

1. Open the Experiment Builder application and use the **graphical user interface** to design the experiment by building a flowchart.
2. Save your project by specifying:
   - **Name of the project.**
   - **Location to save the project.**
3. Saving creates a folder structure for your experiment.  
   Example: The Posner task example project follows this structure.  
   - The main folder contains a file called `graph.ebd`.  
   - Open the project by double-clicking the `graph.ebd` file or loading it through the Experiment Builder interface.

> **Note:** Always manage files within Experiment Builder. Avoid manually editing or deleting files in the project folder.


#### 2. Packaging a Project

If you need to share or move a project (e.g., send to a colleague), use the **File → Package** command. This will:

- Create a single `.ebz` file.
- Use **File → Unpack** to expand it back into a full project folder.

#### 3. Test Running the Experiment

1. Perform a **test run** to ensure everything works as intended:
   - Go to **Experiment → Test Run** or click the **play button** in the toolbar.
2. The test run will:
   - Generate an EyeLink data file.
   - Allow you to verify the collected data for analysis.

> **Important:** Test runs should not be used for actual participant data collection. Only the latest test run's data file is saved, and previous test data is overwritten.

#### 4. Deploying the Experiment

Once the experiment is finalized:

1. Go to **Experiment → Deploy**:
   - This creates a new folder containing an executable file (replacing the `graph.ebd` file).
2. Use this **deployed folder** for real participant data collection:
   - Run the experiment by double-clicking the executable file.
   - Each run will prompt you to enter an **EDF file name** (EyeLink Data File).  
   - At the end of the run, the EDF file will be saved in the deployed folder's `results` subfolder.

#### 5. HASP License Key

- A license key is required to build and edit experiments.  
- However, you **do not need a license key** to run deployed experiments for data collection.


#### 6. Data Analysis Preparation

When preparing for data analysis, ensure that you:

1. Copy the **entire deployed project folder** to the analysis computer, not just the EDF files.
2. The deployed folder contains:
   - Image and video files.
   - Interest area files essential for analysis in Data Viewer.

> **Tip:** Without the full folder, you may lose access to experimental stimuli and interest area data during analysis.


#### Summary

Experiment Builder simplifies experimental design and eye-tracking data collection with its graphical interface and precise timing controls. By following this guide, you’ll be able to:

1. Create and save projects effectively.
2. Perform test runs to ensure proper functionality.
3. Deploy experiments for real data collection.
4. Prepare for data analysis with all necessary files.

For more details, refer to the official documentation or continue to the next tutorial in this series.


---

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


#### Overview of the Experiment Design  

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


#### Posner Task Structure  

The **Posner Task** presented in this tutorial consists of a series of trials, each composed of several key events:  

#### 1. Fixation & Cue Presentation  
- The trial begins with a **fixation cross** and **two placeholder boxes** on the left and right.  
- A **cue** appears centrally near the fixation cross, which can be:  
  - **Valid**: The cue correctly predicts the target location.  
  - **Invalid**: The cue indicates the opposite side of the target.  
  - **Neutral**: The cue does not provide location information.  
- The cue remains on the screen for **500 milliseconds** before disappearing.  

#### 2. Target Onset & Response Collection  
- After a **randomly chosen interval**, a target appears in one of the two placeholder boxes.  
- The participant must press one of two keys to indicate whether the target is on the left or right:  
  - `Z` key → **Left target**  
  - `/` key → **Right target**  

#### 3. Predictions & Attention Effects  
- Participants are expected to respond **faster** to targets preceded by a **valid cue**, as attention is directed toward the target location.  
- This attentional shift may also result in **faster eye movements** toward the target position.  

#### Implementing the Posner Task in Experiment Builder  

The experiment is implemented as an **EyeLink experiment** within **Experiment Builder**. The procedure follows these steps:  

#### 1. Camera Setup & Calibration  
- At the start, **camera setup and calibration instructions** are presented.  
- The **camera setup action** puts the **Host PC** and **Display PC** into a special camera mode for **eye tracker calibration**.  

#### 2. Trial Blocks & Instructions  
The experiment consists of **three blocks of trials**:  

- **Practice Block**: 2 trials  
- **Experimental Blocks**: 10 trials each  
  - 4 **valid** trials  
  - 1 **invalid** trial  
  - 5 **neutral** trials  

The **practice block always appears first**, but the order of experimental blocks is **randomized**. Within each block, the **trial order is also randomized**.  

#### 3. Trial Execution  
Each trial follows this sequence:  

1. **Fixation cross** and **placeholder boxes** appear (*1000 milliseconds*).  
2. The **cue appears** and remains for *500 milliseconds*, then disappears.  
3. After a **random delay**, the **target appears** (*up to 5000 milliseconds*).  
4. The participant presses the appropriate key (`Z` or `/`).  
5. **Immediate feedback** is provided (correct or incorrect).  
6. If **no response** is made within *5 seconds*, the trial times out, and a message prompts the participant to respond faster.  
7. Feedback remains on-screen for **2 seconds**, followed by a **blank screen**.  

#### 4. Experiment Completion & Data Transfer  
- After all **22 trials**, the experiment **ends automatically**.  
- The **EDF data file** is transferred from the **Host PC** to the **Display PC**.  

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

#### **Selecting Your Eye Tracker Model**  

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

#### **Configuring EyeLink Portable Duo**  

For **EyeLink Portable Duo**, select one of the following:  

- **Head Stabilized (Chin Rest) Mode**  
- **Head Free Remote Mode**  

##### **Using "Current" for Custom Host PC Settings**  

If you prefer to configure the **eye tracker settings manually on the Host PC**, you can select **"current"** in the properties menu.  

- This prevents Experiment Builder from **overriding** existing Host PC settings.  
- The Host PC will use whatever **configuration** has already been selected in its interface.  


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

#### **Configuring Audio and Other External Devices**  

If your experiment includes **audio playback** or uses **additional hardware devices**, configure them in the **Devices tab**.  

##### **1. Checking Audio Properties**  
- Ensure that the **correct audio device** is selected.  
- Test audio playback to verify **volume levels** and **latency**.  

##### **2. Managing Additional Devices**  
- If using response boxes, button presses, or other external input devices, set their properties correctly.  
- Experiment Builder will automatically detect and allow configuration for **compatible devices**.  


#### **Saving Default Hardware Settings**  

To **save your project settings as defaults**, follow these steps:  

1. Go to **Edit → Preferences**  
2. Navigate to the **Devices** section  
3. Click **Save as Defaults**  

This ensures that **future projects** automatically apply the same hardware settings, reducing setup time.  


#### **Summary**  

In this tutorial, we covered **essential hardware settings** in Experiment Builder, including:  

✔ **Selecting the correct EyeLink model and configuring tracking options**  
✔ **Setting the display resolution and refresh rate for accurate stimulus presentation**  
✔ **Ensuring a uniform background color to maintain pupil stability**  
✔ **Configuring audio and external devices**  
✔ **Saving settings as defaults for future projects**  

By properly setting up hardware configurations, you ensure **smooth experiment execution** and **accurate data collection**. 🚀  

------------------------------------------------------


### Tutorial 05 - Nodes, Connections & Messages

#### Introduction

In this tutorial, we will discuss how actions and triggers connect in **Experiment Builder** to ensure experimental events occur in the correct sequence. We will also explore how **messages** can be used to mark the occurrence of these events in the **EyeLink data file**. 

We will use a **Posner task example** to illustrate these concepts.


#### Display Screen Actions

#### *Editing a Display Screen Action*

1. The first display screen action, renamed **"display camera setup instructions"**, presents simple **camera setup and calibration instructions** to the **Display PC monitor**.
2. To **view and edit** the contents of a display screen action:
   - **Double-click** the action node.
   - The **Screen Builder** will open.
   - Here, you can **add images, videos, text, shapes, and interest areas** to create the display content.
3. In this example, a **multi-line text resource** is used to present the instructions.


#### Keyboard and Timer Trigger Nodes

#### *Why Use Triggers?*

Display screen actions must be **followed by at least one trigger** before connecting to other actions. Otherwise, the display will **immediately be replaced** by the next display screen action.

##### Example: Using a Keyboard and Timer Trigger

- The **"display camera setup instructions"** action connects to the subsequent **camera setup action** using:
  - A **keyboard trigger**.
  - A **timer trigger**.
- This means that the experiment will proceed **only when**:
  - The participant **presses a key** (activating the keyboard trigger), OR
  - The **specified time** elapses (activating the timer trigger).
- Both triggers connect to the same **camera setup action**, and **whichever fires first** will continue the experiment.


#### Messages in Action and Trigger Nodes

#### *Why Use Messages?*

Each **action or trigger node** in Experiment Builder has a **message property**. This property:
- **Sends a message** to the **Host PC**.
- **Inserts** the message into the **EyeLink data file** (`.edf`).
- **Timestamp marks** the exact time when an event occurs.

#### How Messages Work

- **Display screen actions** send messages **time-locked to the start of the screen retrace**.
- The **timestamp is accurate within a millisecond** of the retrace event.
- Filling out the **message property** ensures a record of the timing of **experimental events** in the `.edf` file.


#### Using Messages for Interest Periods in Data Analysis

#### What is an Interest Period?

An **Interest Period** allows researchers to **analyze only specific parts** of an experimental trial.

For example, in the **Posner task**, we may want to analyze only:
- **The period from target onset to response**.
- Excluding **fixation cue, SOA, and feedback** phases.

#### How to Set an Interest Period

- Messages associated with actions and triggers **help define the Interest Period** in **Data Viewer**.
- When analyzing data, messages in the **EyeLink data file** (`.edf`) can be used to **mark event occurrences**.
- You can find more details in the **Data Viewer video tutorial series**.


#### Labels vs. Messages

- **Label Property**: 
  - Changes how the **node appears in Experiment Builder**.
  - Does **not** affect the `.edf` file.
- **Message Property**:
  - Specifies **what is written** in the `.edf` file.
  - Ensures experimental events are **timestamped correctly**.

#### Best Practice

- **Give each node meaningful labels**.
- Copy and paste the **label text into the message property**.
- This makes it **easy to associate messages in the `.edf` file`** with Experiment Builder nodes.


#### Conclusion

In this tutorial, we covered:
1. **How actions and triggers connect** to control experimental flow.
2. **Using keyboard and timer triggers** to advance experiments.
3. **How messages mark event occurrences** in the EyeLink data file.
4. **Setting Interest Periods** for precise data analysis.
5. **The difference between labels and messages** in Experiment Builder.

By following these steps, you can **ensure accurate event timing** and **improve data analysis** in your eye-tracking experiments.

------------------------------------------------------



### Tutorial 06 - Hierarchical Organization and Data Source Introduction

#### Introduction
In this tutorial, we'll explore how to use hierarchical organization to avoid redundant structures in your Experiment Builder projects. We'll also introduce how to use data sources to manage trial information efficiently.

#### Hierarchical Organization with Sequences

#### *Avoiding Redundancy*
In Experiment Builder, you don't need to create separate nodes for each trial. Instead, you can use hierarchical organization through sequences to streamline your project.

#### *Using Sequences*
Sequences are special action nodes that allow you to implement looping designs. You can double-click a sequence to go inside and add nodes to define events within that sequence. These events will repeat based on the sequence's iteration count.

#### *Nested Sequences*
Sequences can be nested, allowing for loops within loops. This is useful for designs with multiple blocks of trials. For example, you can have a BLOCK sequence that repeats three times, each containing a TRIAL sequence that repeats for each trial within the block.

#### Implementing BLOCK and TRIAL Sequences

#### *BLOCK Sequence*
At the top level of your project, create a BLOCK sequence to handle the repetition of trial blocks. Double-click the BLOCK sequence to go inside and add nodes for each block.

#### *TRIAL Sequence*
Inside the BLOCK sequence, add a TRIAL sequence to handle individual trials. Set the iteration count of the BLOCK sequence to the number of blocks you want to run.

#### *Conditional Triggers*
Use conditional triggers to control the flow of your experiment. For example, you can check if the current block is the first one and direct the experiment to task instructions or a break screen accordingly.

#### Different Number of Trials Per Block

#### *Split By Property*
To run a different number of trials for each block, use the Split By property of the TRIAL sequence. For example, set it to `[2,10,10]` to have two trials in the first block and ten trials in each of the next two blocks.

#### Introduction to Data Sources

#### *What is a Data Source?*
A data source is a spreadsheet that contains information used on each iteration of a sequence. Typically, you'll have a data source for your trial sequence, containing details for each trial.

#### *Accessing Data Sources*
To access a sequence's data source, click on its data source property. You can also use the dropdown at the top of the interface to select a data source.

#### Populating Data Sources

#### *Adding Rows and Columns*
You can add rows and columns directly in the data source editor. Alternatively, import data from a delimited text file created in spreadsheet software like Excel.

#### *Data Source Structure*
Each row in the data source represents a trial, and columns represent variables that change from trial to trial. For example:
- **identifier**: A unique value for each trial.
- **cueType**: Specifies the type of cue (valid, invalid, neutral).
- **cueImage**: The image file for the cue.
- **targetImage**: The image file for the target.
- **targetSide**: Describes the side of the target.
- **targetLocation**: The coordinates for presenting the target image.
- **nontargetLocation**: Coordinates for the opposite rectangle.
- **practiceStatus**: Distinguishes practice from experimental trials.
- **correctResponse**: The correct key press for each trial.
- **block**: Indicates the block number for randomization.
- **counterbalance**: Used to counterbalance the design.

#### Using Data Sources in Your Experiment

#### *Referencing Data*
While a data source specifies trial information, this data isn't automatically used. You need to reference these values in node and resource properties. For more details on how to use data sources and randomization options, see later tutorials in this series.

#### Conclusion
By using hierarchical organization and data sources, you can efficiently manage complex experimental designs in Experiment Builder. This approach reduces redundancy and makes your project more manageable.


------------------------------------------------------



### Tutorial 07 - Data Source Randomization Options

#### Introduction
In this tutorial, we'll explore the data source randomization options available in Experiment Builder. These options allow you to control the order of experimental trials, randomize trial and block orders, and manage counterbalancing.

#### Overview of Randomization Settings

#### *Accessing Randomization Settings*
The randomization settings button in a project's data source allows you to apply various randomization schemes to the ordering of experimental trials. These settings include options for:
- Blocking trials
- Randomizing trial and block orders
- Forcing trial ordering to limit the number of consecutive trials with a particular feature
- Creating alternative versions of the project for counterbalancing

#### Example: Posner Task Experimental Design

#### *Experimental Design*
The Posner task example is set up as follows:
- Two practice trials always come first.
- Two experimental blocks of 10 trials each follow.
- The order of the experimental blocks is randomized.
- The order of trials within each block is randomized.
- Two alternative lists (counterbalances) are used, and each participant receives trials from only one counterbalance.

#### Data Source Columns

#### *Practice Status Column*
- The first two trials of each list have a value of "practice."
- The remaining 20 trials have a value of "experimental."

#### *Block Column*
- Practice trials have a block value of 1.
- The first block of 10 experimental trials has a block value of 2.
- The second block of 10 experimental trials has a block value of 3.

#### *Counterbalance Column*
- The first 22 rows (counterbalance 1) have a value of 1.
- The last 22 rows (counterbalance 2) have a value of 2.

#### Implementing Randomization

#### *Blocking Levels*
1. **Practice Status (Blocking Level 1)**:
   - Set as blocking level 1.
   - Randomized box unchecked to ensure practice trials come first.
   - Practice trials (value "practice") will precede experimental trials (value "experimental").

2. **Block (Blocking Level 2)**:
   - Set as blocking level 2.
   - Randomized box checked to randomize the order of experimental blocks.
   - Trials within each block remain grouped together, but the order of blocks is randomized.

#### *Trial Randomization*
- **Enable Trial Randomization**:
  - Checked to randomize the order of trials within each block.
  - Constraint: The `cueImage` column is set as the run length control column with a maximum run length of 2.
  - Ensures no more than two consecutive trials with the same cue image.

#### Counterbalancing

#### *Splitting Column*
- **Counterbalance Column**:
  - Chosen as the splitting column.
  - Prompts you to select a counterbalance value (1 or 2) at runtime.
  - Only rows with the selected counterbalance value are used in the experiment.

#### Practical Steps

1. **Open Randomization Settings**:
   - Click the randomization settings button in the trial data source.

2. **Set Blocking Levels**:
   - Set `practiceStatus` as blocking level 1 (randomized unchecked).
   - Set `block` as blocking level 2 (randomized checked).

3. **Enable Trial Randomization**:
   - Check the "Enable Trial Randomization" option.
   - Set `cueImage` as the run length control column with a maximum run length of 2.

4. **Set Splitting Column**:
   - Select the `counterbalance` column as the splitting column.

####  Conclusion
By using the randomization settings in Experiment Builder, you can efficiently manage the order of trials and blocks, ensuring that your experimental design is both randomized and counterbalanced. This approach helps maintain the integrity of your experimental results and ensures that each participant receives a balanced set of trials.

-----------------------------------------------------------------



### Tutorial 08 - Trial Preparation

#### Introduction
In this tutorial, we'll discuss trial preparation considerations in Experiment Builder. Proper trial preparation ensures smooth execution of experimental events and accurate data collection.

#### Trial Preparation Workflow

#### *Basic Trial Events*
Basic trial events, such as the presentation of images to participants, are typically placed inside a sequence labeled **RECORDING**. This setup allows for trial preparation before recording eye movement data and executing critical trial events.

#### PREPARE_SEQUENCE Action Node

#### *Loading Stimuli*
On each iteration of the trial sequence, we typically perform the following steps:
1. **Load Stimuli**:
   - Use the **PREPARE_SEQUENCE** action to load experimental stimuli (e.g., images, videos, audio files) into the Display PC's memory buffers.
   - This ensures that the stimuli are pre-buffered and ready for presentation.

#### *Transferring Display Screen to Host PC*
2. **Transfer Display Screen**:
   - Set the **Draw to EyeLink Host** property of the **PREPARE_SEQUENCE** action to **Image**.
   - Select one **DISPLAY_SCREEN** action in the recording sequence and check its **Use for Host Display** property.
   - Ensure that all other **DISPLAY_SCREEN** actions have their **Use for Host Display** property unchecked.
   - This allows the experimenter to monitor the participant's gaze in relation to experimental stimuli during trials.

#### Drift Check/Correct using the DRIFT_CORRECT Action Node

#### *Drift Correction*
3. **Drift Correction**:
   - The **DRIFT_CORRECT** action presents a fixation target on the Display PC monitor.
   - The position of the target is determined by the **X Location** and **Y Location** properties of the **DRIFT_CORRECT** action.
   - During the experimental session, the experimenter can compare the gaze cursor position to the target position on the Host PC.
   - When the participant's gaze is steady on the fixation target, either the experimenter or the participant can press the space bar to start the trial.
   - Note: The **DRIFT_CORRECT** action is optional but recommended for ensuring accurate calibration and gaze position at the start of each trial.

#### Recording Data using the RECORDING Sequence

#### *Recording Sequence Setup*
4. **Recording Sequence**:
   - The **RECORDING** sequence should have an iteration count of 1.
   - This sequence is not used for looping but for controlling eye tracker recording.
   - The **RECORD** property of the **RECORDING** sequence is checked to start and stop eye data recording.
   - When the experiment exits the **RECORDING** sequence, it logs the values of data source columns and variable nodes, making them accessible in Data Viewer.

#### Real-Time Processing and Host PC Communication

#### *Real-Time Processing*
5. **Real-Time Processing**:
   - Check the **Is Realtime** property of the **RECORDING** sequence to elevate the priority of Experiment Builder and ensure optimal timing of experimental events.

#### *Sending Messages to Host PC*
6. **Sending Messages**:
   - Use the **EyeLink Record Status Message** property of the **RECORDING** sequence to send messages to the experimenter.
   - This message can provide feedback, such as the current trial number and total number of trials.
   - Edit the message using string concatenation and references to the iteration and iteration count properties of the trial sequence.

#### Best Practices and Checklist

#### *Experiment Builder Checklist*
- Refer to the **Experiment Builder Project Checklist** in the user manual (accessed via Help -> Contents) for best practices in trial preparation and other programming tips.
- This checklist helps avoid common pitfalls in data collection and analysis.

#### Conclusion
Proper trial preparation in Experiment Builder ensures that stimuli are pre-loaded, the experimenter can monitor gaze positions, and data is accurately recorded. By following the steps outlined in this tutorial, you can set up efficient and reliable trial preparation for your experiments.

Stay tuned for more tutorials in this series to learn advanced techniques for using Experiment Builder.


-----------------------------------------------------------------


### Tutorial 09 - Trial Events

#### Introduction
In this tutorial, we'll discuss the basic structure of critical trial events in an experiment. We'll explore how the recording sequence and data source work together to control the flow of events during each trial.

#### Recording Sequence Structure

#### *Basic Structure*
The nodes in the recording sequence form a skeleton structure or template for the sequence of events that occur on each trial. The data source provides the information that determines the differences across trials.

#### Update Attribute Action Node

#### *Reset Variables*
The first node in the recording sequence is an **Update Attribute** action called **reset variables**. This action:
- Sets the value of a variable used for the SOA (Stimulus Onset Asynchrony) duration by randomly selecting from a range of possible numbers.
- Resets the values of three variable nodes that store behavioral data collected during the trial.

#### Display Screen and Timer Trigger Nodes

#### *Display Fixation Cross*
- The **display fixation cross** action presents the fixation cross and two placeholder boxes on the screen.
- The **timer fixation cross** trigger fires after 1000 milliseconds (1 second), controlling the duration of the fixation cross presentation.

#### *Display Cue*
- The **display cue** action presents the cue stimulus on the screen.
- The **timer cue** trigger fires after 500 milliseconds, controlling the duration of the cue presentation.

#### *Display Fixation SOA*
- The **display fixation SOA** action presents an exact copy of the fixation cross action, effectively removing the cue from the screen.
- The duration of this screen is determined by the value of a variable node called **SOA duration**, which is set randomly at the beginning of the trial.

#### Display Target

#### *Display Target*
- The **display target** action presents the target stimulus to the participant.
- The **timer target** trigger fires after 5000 milliseconds (5 seconds), controlling the duration of the target presentation.

#### Keyboard or Timer Trigger Nodes

#### *Keyboard Response Trigger*
- The **keyboard response trigger** is set to accept input from specific keys (e.g., slash and z keys).
- If a key is pressed, the **check accuracy** trigger checks the response against the correct response column in the trial data source.

#### Conditional Triggers

#### *Check Accuracy*
- The **check accuracy** trigger determines whether the participant's response was correct.
- Two subsequent **Update Attribute** actions set the values of variable nodes that store the trial's behavioral data.

#### Display Screen and Timer Trigger Nodes for Feedback

#### *Present Feedback*
- Feedback is presented to the participant for 2 seconds, handled by different **display screen** actions based on the response (correct, incorrect, or go faster).
- The **timer feedback** trigger fires after 2 seconds, and the **display blank** action clears the screen.

#### Add to Results File Node

#### *Log Behavioral Data*
- The **add to results file** action logs the values of data source columns and variable nodes for the trial to a tab-delimited text file called **results file**.
- These values are also logged to the EyeLink data file when the recording sequence ends.

#### Adding Message Property for Nodes and Triggers

#### *Event Markers*
- It is important to fill out the **message property** of all actions and triggers in the recording sequence.
- When a node is executed, an event marker (text of the message property) is sent to the EyeLink data file, marking the exact time of the experimental event.
- These messages can be used to set Interest Periods in Data Viewer for focused data analysis.

#### Conclusion
By understanding the basic structure of trial events and how the recording sequence works, you can effectively control the flow of events during each trial. Properly setting up nodes and triggers ensures accurate data collection and analysis. For more detailed information on specific actions and triggers, refer to the videos on behavioral data logging and Interest Periods in Data Viewer.

-------------------------------------------------------


### Tutorial 10 - Screen Building and Referencing

#### Introduction
In this tutorial, we'll learn how to add content to a display screen action using the screen builder and how to reference information in the data source to change experimental characteristics across trials. We'll focus on nodes in the project's recording sequence.

#### Adding Content to Display Screen Actions

#### *Screen Builder Overview*
The screen builder allows you to see and edit the content that will be presented to the participant by a display screen action. It includes buttons to add different types of screen resources, such as:
- Images
- Videos
- Text
- Basic shapes
- Interest areas (for analysis and triggers)

Interest areas are not visible to participants but are useful for specifying regions of interest and can be used as triggering regions for mouse and gaze-based triggers.

#### Adding Image Resources

#### *Adding an Image Resource*
1. **Access the Library Manager**:
   - Click the button that looks like books on a shelf or click "Edit Library Manager".
   - Add image files to your project's library under the "Image" tab.
   - The library manager provides a preview of image files and shows properties of the selected file.

2. **Insert an Image Resource**:
   - Go back to the screen builder for your display screen action.
   - Use the "Insert Image Resource" button to add an image from your library.
   - The properties of the image resource become visible in the properties panel on the left.

3. **Source Filename Property**:
   - The "Source Filename" property specifies the image file to be displayed.
   - If you want the same image on each trial, set the property to a specific image file (e.g., `cross.png`).

#### Adding Shape Resources

#### *Adding a Shape Resource*
1. **Select the Shape Button**:
   - Choose the appropriate shape button (e.g., rectangle).
   - Click and drag to draw the shape on the screen.
   - Set properties such as color and fill (e.g., white color with no fill).

#### Referencing Data Source Columns

#### *Changing Image on Each Trial*
1. **Display Cue Action**:
   - The display cue action is similar to the display fixation cross action but includes an additional image resource for the cue.
   - To change the cue image on each trial, reference the `cueImage` column from the trial data source.

2. **Making a Reference**:
   - Click on the "Source Filename" property in the properties panel.
   - Click the button with three dots to open the attribute editor.
   - Navigate to the data source component of the trial sequence.
   - Double-click the `cueImage` column to create a reference.
   - The reference will be shown at the top of the attribute editor.

3. **Display Target Action**:
   - Similarly, reference the `targetImage` column for the target image resource.
   - Reference the `targetLocation` column for the target image's location property.

#### Example: Display Fixation Cross Action
- The display fixation cross action uses an image resource to present a cross on a gray background.
- The image file (`cross.png`) is added from the library.
- The properties of the image resource can be edited in the screen builder.

#### Example: Display Cue Action
- The display cue action includes an additional image resource for the cue.
- The `cueImage` column in the data source is referenced to change the cue image on each trial.
- The `targetLocation` column is referenced to change the target image's position on each trial.

#### Conclusion
By using the screen builder and referencing data source columns, you can dynamically change experimental characteristics across trials. This approach allows for flexible and efficient experiment design. For more detailed information on specific actions and triggers, refer to the videos on behavioral data logging and Interest Periods in Data Viewer.


-----



## Webinar - Implementing the Visual World Paradigm in Experiment Builder

[Link to video](https://www.youtube.com/watch?v=U3gt2v9_ZN4)

[Data, PPT & Video downloads](https://drive.google.com/drive/folders/1PH312mMMkVTEfzxmwZXrIxZjTrTHAY56)


Example project: *SimpleVisualWorld.ebz*


**Overview**

This tutorial is based on the SR Research webinar *Implementing the Visual World Paradigm in Experiment Builder*.  
It walks you through building a Visual World experiment using the included **SimpleVisualWorld.ebz** project, covering:

- Automatic drift checks between trials
- Balancing stimulus positions
- Marking critical audio times in EDF files
- Logging behavioral responses

**1. Experiment Structure**

- **Blocks:**
  - 1 practice block (2 trials)
  - 4 experimental blocks (4 trials each)
- **Between-block event:** Break screen
- **Counterbalancing:** 2 list versions defined in the Data Source


**2. Trial Start & Auto Drift Check**

**Fixation Cross**
- **Invisible Boundary Trigger**:
  - Region: bounding box over fixation cross
  - Event: *Gaze In Region For* = 500 ms
  - Timeout: 10,000 ms
  - On timeout:
    - **Update Attribute** (`SET_RECALIBRATE`):
      ```
      SHOULD_WE_RECALIBRATE = 1
      ```

**Recalibration Logic**
- **Conditional Trigger** (`CHECK_TO_RECALIBRATE`):
  - If:
    ```
    SHOULD_WE_RECALIBRATE == 1
    ```
    → Go to `EL_CAMERA_SETUP`
  - Else → Continue trial



**3. Stimulus Display & Positioning**

**Goal:** Interest Areas (IAs) code **stimulus type**, not screen position.

- **Image Resources:**
  - `Target_Image`
  - `PhonComp_Image`
  - `SemComp_Image`
  - `Distractor_Image`
- **Interest Areas:**
  - `IA_Target`
  - `IA_PhonComp`
  - `IA_SemComp`
  - `IA_Distractor`
  - Location: Reference → corresponding image resource
- **Variable:**
  - `POSITIONS_LIST` (list of `(x, y)` coordinates)
    - Index `0` unused
    - Codes:  
      `1` = top left  
      `2` = top right  
      `3` = bottom left  
      `4` = bottom right
- **Data Source:**
  - Position codes: `Target_Pos`, `PhonComp_Pos`, `SemComp_Pos`, `Distractor_Pos`
  - File names: `Target_File`, `PhonComp_File`, `SemComp_File`, `Distractor_File`
- **DISPLAY_IMAGES Action:**
  - Position = `POSITIONS_LIST` index from Data Source
  - File = filename from Data Source



**4. Preview and Audio Playback**

- **TIMER_IMAGE_PREVIEW**:
  - Duration = 500 ms
- **PLAY_SOUND** Action:
  - Sound File = `AudioFile` column from Data Source


**5. Critical Audio Event Marking**

- **TIMER_CRIT_WORD** Trigger:
  - Start Time = `PLAY_SOUND.playStartTime`
  - Duration = `CritWordTime` column
  - **Send Message To EDF**:
    ```
    CRIT_WORD_ONSET
    ```

**6. Mouse Response Collection**

**Cursor Setup:**
- Cursor image resource
- **Position is Mouse Contingent** = ON
- **Color Key** = ON
- **Update Attribute**:
  - Reset mouse position before showing images

**Click Detection:**
- **MOUSE_RESPONSE** Trigger:
  - Region Type = INTEREST AREA
  - Linked to: IA_Target, IA_PhonComp, IA_SemComp, IA_Distractor
  - Button = 1 (left click)
  - **Press Events** = ON
  - **Position Triggered** = ON



**7. Logging Behavioral Data**

- **Conditional Trigger** after MOUSE_RESPONSE:
  - If:
    ```
    IA ID == 1
    ```
    → **SET_VARS_CORRECT**:
      ```
      ACCURACY = 1
      ```
  - Else:
    → **SET_VARS_INCORRECT**:
      ```
      ACCURACY = 0
      ```
- Both branches also set:
  - `IMAGE_CLICKED`
  - `RT`
- **Send Message to EDF** and write to results file



**8. Trial End**

- **Feedback Display**: 1 second
- Next trial or block break

**Summary Table**

| Component              | Purpose                         | EB Objects Used |
|------------------------|---------------------------------|-----------------|
| Auto Drift Check       | Maintain calibration            | Invisible Boundary Trigger, Conditional Trigger |
| Stimulus Positioning   | Type-based IA coding            | Image Resources, Interest Areas, `POSITIONS_LIST` |
| Audio Event Marking    | Time-lock to critical words     | Timer Trigger, Send Message to EDF |
| Mouse Response         | Collect participant clicks      | Cursor Resource, Mouse Response Trigger |
| Data Logging           | Store accuracy, RT, choice      | Conditional Trigger, Update Attribute, EDF Msg |

---


##  Step-by-step creation of the Visual World Paradigm in EB

**Series Navigation:**  
Part 1 – Project Setup and Data Source    
Part 2 – Stimulus Display and Interest Areas


### Part 1 – Project Setup and Data Source 

**Overview**

This post begins the step-by-step build of the *SimpleVisualWorld.ebz* experiment as described in the SR Research webinar *Implementing the Visual World Paradigm in Experiment Builder*.  


**1. Create a New Project**

1. Open **Experiment Builder** and select **File → New Project**.
2. Give the project a descriptive name (e.g., `VisualWorldParadigm`).
3. Set the save location for your `.ebz` file.



**2. Define Variables**

From the transcript, the following variables are used later in the build:

1. `SHOULD_WE_RECALIBRATE` – integer, default value `0`.
2. `POSITIONS_LIST` – list, stores `(x, y)` coordinates for positions 1–4.
3. `ACCURACY` – integer.
4. `IMAGE_CLICKED` – string.
5. `RT` – number.

**Steps:**
1. Go to the **Variables** tab.
2. Add each variable with its correct type.
3. For `POSITIONS_LIST`:
   - Add position coordinates:
     ```
     0 = (0,0)   # unused
     1 = top left
     2 = top right
     3 = bottom left
     4 = bottom right
     ```

> **Note on `POSITIONS_LIST`, Image Positions, and Interest Areas in a Visual World Experiment**
> 
> **What**  
> In this experiment, `POSITIONS_LIST` is a variable storing fixed `(x, y)` coordinates for potential stimulus locations on a 1920×1080 display.  
> Each coordinate was chosen so that it lies in a different quadrant:
> 
> ```
> Index 0: (0, 0)        # unused placeholder
> Index 1: (480, 270)    # top left
> Index 2: (1440, 270)   # top right
> Index 3: (480, 810)    # bottom left
> Index 4: (1440, 810)   # bottom right
> ```
> <img src="/images/positionlistVW4Q.png" alt="4-Quadrant positions for POSITIONS_LIST" width="450">
> 
> The screen center is at `(960, 540)`, dividing the display into four quadrants:  
> - **Top left:** `x < 960` and `y < 540`  
> - **Top right:** `x > 960` and `y < 540`  
> - **Bottom left:** `x < 960` and `y > 540`  
> - **Bottom right:** `x > 960` and `y > 540`
> 
> **How**  
> - The Data Source contains position codes (1–4) for each stimulus type (e.g., `Target_Pos`, `PhonComp_Pos`).  
> - EB uses the code as an **index** into `POSITIONS_LIST` to find the corresponding coordinates.  
> - For example, `Target_Pos = 2` → `POSITIONS_LIST[2] = (1440, 270)`  
>   - `1440` > `960` → right half of screen  
>   - `270` < `540` → top half of screen  
>   → Result: **top-right quadrant**.  
> - The Image Resource’s **Position** property references `POSITIONS_LIST`, with the **Index** tied to the relevant Data Source column.  
> - Each Interest Area’s **Location** property references its image resource, so when the image is positioned, the IA moves with it automatically.
> 
> **Why**  
> - **Quadrants ≠ Interest Areas**: Quadrants are just possible screen positions. Interest Areas are named for stimulus type (e.g., `IA_Target`, `IA_PhonComp`) and follow the assigned image to any quadrant.  
> - **Counterbalancing**: The same stimulus type can appear in different quadrants across trials, supporting balanced designs without changing IA definitions.  
> - **Clean analysis**: In Data Viewer, `IA_Target` always refers to the target stimulus, regardless of which quadrant it was displayed in. This avoids the need to re-code locations in post-processing.
> 
> This setup ensures stimulus placement is flexible, Interest Areas always match stimulus identity, and the design supports efficient counterbalancing and straightforward analysis.
> 


**3. Prepare the Data Source**

The Data Source should contain columns matching the variables used to position and display stimuli:

1. **Position columns** (integer values 1–4):
   - `Target_Pos`
   - `PhonComp_Pos`
   - `SemComp_Pos`
   - `Distractor_Pos`
2. **File name columns** (string):
   - `Target_File`
   - `PhonComp_File`
   - `SemComp_File`
   - `Distractor_File`
3. **Audio file column**:
   - `AudioFile`
4. **Critical word timing**:
   - `CritWordTime` (in milliseconds)

**Steps:**
1. Open the **Data Source** editor.
2. Create the columns listed above.
3. Fill in the rows for each trial according to your design.
4. Save the Data Source file.


**4. Create Project Blocks**

From the transcript:

- **1 practice block** (2 trials)
- **4 experimental blocks** (4 trials each)
- Break screen between blocks
- Two counterbalanced list versions in the Data Source

**Steps:**
1. In the timeline, create a **Practice Block**:
   - Number of trials: 2.
2. Create **Experimental Block 1–4**:
   - Number of trials: 4 in each block.
3. Add a **Break Screen** sequence between blocks.
4. Link blocks to the correct Data Source list version.

---

### Part 2 – Stimulus Display and Interest Areas

**Overview**

This post covers the setup of stimulus display and interest areas for the *SimpleVisualWorld.ebz* experiment, following the SR Research webinar transcript step-by-step.


**1. Add Image Resources**

From the transcript, we have four image resources:

1. `Target_Image`
2. `PhonComp_Image`
3. `SemComp_Image`
4. `Distractor_Image`

**Steps:**
1. In the **Resource Manager**, create a new **Image Resource** for each stimulus type.
2. Assign placeholder images for now — these will be replaced with file references from the Data Source later.


**2. Create Interest Areas (IAs)**

The transcript specifies one IA per stimulus type, not per position.

1. `IA_Target`
2. `IA_PhonComp`
3. `IA_SemComp`
4. `IA_Distractor`

**Steps:**
1. On the stimulus display canvas, right-click → **Add Interest Area**.
2. Name it according to stimulus type (e.g., `IA_Target`).
3. In the **Location** property of the IA, set **Reference** to the matching image resource (e.g., `IA_Target` → `Target_Image`).
4. Repeat for all four IAs.



**3. Link Positions from `POSITIONS_LIST`**

The transcript specifies that stimulus positions are controlled by a variable rather than fixed coordinates.

**Steps:**
1. Select `Target_Image` in the display canvas.
2. In the **Position** property, set Reference → `POSITIONS_LIST`.
3. For **Index**, reference the Data Source column `Target_Pos`.
4. Repeat for:
   - `PhonComp_Image` → Index from `PhonComp_Pos`
   - `SemComp_Image` → Index from `SemComp_Pos`
   - `Distractor_Image` → Index from `Distractor_Pos`


**4. Link Image Files from the Data Source**

**Steps:**
1. Select `Target_Image`.
2. In the **File** property, set Reference → `Target_File` (Data Source column).
3. Repeat for:
   - `PhonComp_Image` → `PhonComp_File`
   - `SemComp_Image` → `SemComp_File`
   - `Distractor_Image` → `Distractor_File`


**5. Add DISPLAY_IMAGES Action to the Trial Sequence**

**Steps:**
1. In the trial sequence, insert a **DISPLAY_IMAGES** action.
2. Ensure it references the four image resources already linked to `POSITIONS_LIST` and Data Source columns.
3. Place this action in the correct order in the trial timeline, before the audio playback.

---

## A Triangle Layout in a Visual World Experiment
### Using `POSITIONS_LIST` for a Triangle Layout in a Visual World Experiment
> 
> **What**  
> In this design, we present **three images** arranged in a triangular pattern on a 1920×1080 display. Instead of placing them in rectangular quadrants, we define a `POSITIONS_LIST` with three fixed `(x, y)` coordinates, each representing one vertex of the triangle:
> 
> ```
> Index 0: (0, 0)        # unused placeholder
> Index 1: (960, 270)    # top center
> Index 2: (560, 810)    # bottom left
> Index 3: (1360, 810)   # bottom right
> ```
> > <img src="/images/positionlistVW3Q.png" alt="3-Quadrant positions for POSITIONS_LIST" width="450">
> 
> These coordinates were chosen so that each point lies inside one of the intended positions of the triangle. You can adjust these values to change spacing or alignment.
> 
> **How**  
> 1. **Define `POSITIONS_LIST`**  
>    - In Experimental Builder, create a variable named `POSITIONS_LIST` of type **Point List**.  
>    - Enter the coordinates above, keeping index `0` as an unused placeholder.  
> 
> 2. **Add position columns in the Data Source**  
>    - In your CSV/Excel Data Source, add a **position column** for each image type:  
>      - `Target_Pos`  
>      - `Comp_Pos` (competitor)  
>      - `Distractor_Pos`  
>    - For each trial, assign a number **1–3** indicating where that image should appear.  
>    - Example:
>      | Trial | Target_Pos | Comp_Pos | Distractor_Pos |
>      |-------|------------|----------|----------------|
>      | 1     | 1          | 2        | 3              |
>      | 2     | 2          | 1        | 3              |
>      | 3     | 3          | 2        | 1              |
> 
> 3. **Link images to `POSITIONS_LIST`**  
>    - On the display, select each image resource (`Target_Image`, `Comp_Image`, `Distractor_Image`).  
>    - In the **Position** property:  
>      - Set **Reference** → `POSITIONS_LIST`.  
>      - Set **Index** → the matching Data Source column (`Target_Pos`, `Comp_Pos`, or `Distractor_Pos`).  
>    - This tells EB: *For this trial, place the image at `POSITIONS_LIST[ DataSource.PositionColumn ]`*.
> 
> 4. **Link Interest Areas to image resources**  
>    - Create an Interest Area (IA) for each stimulus type (`IA_Target`, `IA_Comp`, `IA_Distractor`).  
>    - In the IA’s **Location** property, set **Reference** → the associated image resource.  
>    - This ensures the IA moves automatically to follow its image’s position in each trial.
> 
> **Why**  
> - **Flexible positioning**: You can easily change the coordinates in `POSITIONS_LIST` to adjust the triangle’s shape without editing every display.  
> - **Counterbalancing**: Stimulus types can swap positions across trials simply by changing the position codes in the Data Source.  
> - **Clean analysis**: Interest Areas are tied to stimulus identity, not fixed positions. For example, `IA_Target` always means the target stimulus, whether it appears at the top or bottom of the triangle.  
> - **Reusability**: The same trial display works for all position combinations, avoiding the need to create separate layouts for each configuration.
> 
> This method mirrors the standard `POSITIONS_LIST` approach used in quadrant-based designs, but with custom coordinates for a triangle arrangement, ensuring both experimental flexibility and data analysis clarity.

---


### Choosing `POSITIONS_LIST` Coordinates for a Triangle Layout on a 1920×1080 Screen
> 
> **Understanding the Coordinate System**  
> Experimental Builder (EB) uses screen coordinates where:
> - `(0, 0)` = top-left corner of the screen  
> - `(1920, 1080)` = bottom-right corner (for a 1920×1080 display)  
> - By default, the **Position** property for an image refers to its **center point**, not its top-left corner.
> 
> **Goal Layout**  
> For a triangle arrangement of three images:
> - One image at the **top center**
> - Two images at the **bottom**, left and right
> 
> **Step-by-Step Process**  
> 1. **Find the screen center**  
>    ```
>    Center X = 1920 / 2 = 960
>    Center Y = 1080 / 2 = 540
>    ```
> 
> 2. **Top vertex (Image 1)**  
>    - Keep it horizontally centered: `x = 960`  
>    - Move it upward to about 1/4 of the way down the screen: `y = 270`  
>    - Result: `(960, 270)`  
> 
> 3. **Bottom left vertex (Image 2)**  
>    - Shift left from the center: `x = 960 - 400 = 560`  
>    - Move it downward to about 3/4 of the way down the screen: `y = 810`  
>    - Result: `(560, 810)`  
> 
> 4. **Bottom right vertex (Image 3)**  
>    - Shift right from the center: `x = 960 + 400 = 1360`  
>    - Same vertical position as bottom left: `y = 810`  
>    - Result: `(1360, 810)`
> 
> **Final `POSITIONS_LIST`**
> ```
> Index 0: (0, 0)        # unused placeholder
> Index 1: (960, 270)    # top center
> Index 2: (560, 810)    # bottom left
> Index 3: (1360, 810)   # bottom right
> ```
> 
> **Why These Values Work**  
> - **Symmetry:** Equal horizontal shifts from the center produce a balanced triangle.  
> - **Spacing:** Vertical offsets (270 for top, 810 for bottom) keep images apart and leave room for Interest Areas.  
> - **Adjustability:** Changing horizontal or vertical offsets lets you easily resize or reshape the triangle without altering the Data Source or trial displays.
> 
> **Tip**: These values assume that your image’s *center point* is positioned at the given coordinates. If you use large images, test the layout to ensure they don’t overlap and adjust offsets accordingly.

---



## Composite Images and IAS Files for a Triangle Layout in a Visual World Experiment

### Using Composite Images and IAS Files in EyeLink Visual World Experiments"

**🎯 Overview**

In a Visual World eye-tracking experiment, the **Target**, **Competitor**, and **Distractor** are combined into a **single composite image** for each trial.  

This method replaces `POSITIONS_LIST` with **matching Interest Area Set (IAS) files** that define rectangles aligned with the composite layout.  

- Composite images fix the layout of stimuli.  
- IAS files specify screen-relative coordinates of Interest Areas (IAs).  
- This guarantees that the gaze data always maps correctly to each object.


**🛠 How to Implement**

**1. 🖼 Create Composite Images**
- Use **PowerPoint** (or similar) to arrange the three images (Target, Competitor, Distractor).  
- Export each slide as a `.png` (e.g., `1280 × 718`).  
- In EB, these images will be displayed **centered on a `1920 × 1080` screen**, without stretching.  
- Create multiple composites to counterbalance object positions across trials.



**2. 📐 Define Interest Areas (IAS Files)**
For each composite, create a `.ias` file that specifies the Interest Area rectangles.

Coordinates must be relative to the **full screen (1920 × 1080)**, not the composite image size.

Since a `1280 × 718` image is centered on the `1920 × 1080` screen:
- Horizontal offset = (1920 − 1280) / 2 = **320**  
- Vertical offset = (1080 − 718) / 2 = **181**

Add these offsets to the image-relative IA coordinates.

Example conversion:  
If the Target is at (524, 19) in the image, then its screen coordinates are:
- X = 524 + 320 = **844**  
- Y = 19 + 181 = **200**

> Example IAS file:

```
Label X Y Width Height
Target 844 200 233 233
Competitor 475 647 233 233
Distractor 1212 647 233 233
```



- **Label** = stimulus role (Target, Competitor, Distractor)  
- **X, Y** = top-left corner of IA rectangle (screen pixels)  
- **Width, Height** = IA size (screen pixels)  

If stimuli swap positions in another composite, you only change coordinates in the IAS file — labels remain consistent.



**3. 📋 Reference Images and IAS Files in the Data Source**
In the EB Data Source spreadsheet, include:

| Trial | CompositeImage | IASFile   |
|-------|----------------|-----------|
| 1     | comp1.png      | comp1.ias |
| 2     | comp2.png      | comp2.ias |
| 3     | comp3.png      | comp3.ias |

- `CompositeImage` → composite stimulus filename  
- `IASFile` → matching interest area set filename  


**4. ⚙ Configure the Display in EB**
- Insert a single **Image Resource**.  
  - Set **Filename Reference** to the `CompositeImage` column.  
- In the Display **Properties**, set **Interest Area Set Name** to reference the `IASFile` column.  
- Place composites in the `images/` folder and IAS files in the `ias/` folder of the EB project.


**5. 📡 During Recording**
- EB loads the composite image and its IAS file for each trial.  
- IA definitions are written into the `.edf` along with gaze data.



**6. 📊 In Data Viewer**
- The correct interest areas load automatically per trial.  
- Exports include `IA_LABEL` values (`Target`, `Competitor`, `Distractor`), regardless of screen position.  



**✅ Advantages**
- 🔄 Eliminates `POSITIONS_LIST` (layout is fixed in the composite).  
- 🎯 Precise IA mapping (avoids misalignment).  
- 💡 Simplified setup (one image, one IAS file per trial).  
- 🎲 Easy counterbalancing (shuffle composite–IAS pairs in the Data Source).  
- 📊 Streamlined Data Viewer analysis (labels consistent across trials).  



**⚠️ Trade-offs**
- ✏️ Each new layout requires a composite + IAS pair.  
- 🧩 Less flexible — moving images means re-exporting composites and updating IAS files.  
- 📂 Requires careful file management to avoid mismatches.  



**🖼 Example**

<img src="/images/composite_in_full_screen_black_white.png" alt="Composite Image in a full screen" width="450">

*Example: A `1280 × 718` composite centered on a `1920 × 1080` screen, with IAS coordinates offset to align with Target, Competitor, and Distractor. In the actual experiment, the background of both the composite images and the screen are set as black. Only the three interest areas are set as white.*



**📊 Conversion Table**

Here’s how the three IA coordinates from the composite image (`1280 × 718`) were converted into screen-relative coordinates (`1920 × 1080`):

| Label       | Image X | Image Y | Width | Height | +320 (H offset) | +181 (V offset) | Screen X | Screen Y |
|-------------|---------|---------|-------|--------|-----------------|-----------------|----------|----------|
| Target      | 524     | 19      | 233   | 233    | 524 + 320       | 19 + 181        | **844**  | **200**  |
| Competitor  | 155     | 466     | 233   | 233    | 155 + 320       | 466 + 181       | **475**  | **647**  |
| Distractor  | 892     | 466     | 233   | 233    | 892 + 320       | 466 + 181       | **1212** | **647**  |

This table ensures clarity:  
- **Image X/Y** = measured directly on the 1280×718 composite  
- **Offsets** = applied to center the image on the 1920×1080 screen  
- **Screen X/Y** = final values to use in IAS files  





---


### Calculating Interest Area (IA) Coordinates from PowerPoint Measurements

**Prompt**  
Measurements from PowerPoint’s *Size & Position* panel for a composite image:

**Top-center image**  
- X position = 13.45 cm (from top-left corner)  
- Y position = 0.5 cm (from top-left corner)  
- Width = 6 cm  
- Height = 6 cm  

**Bottom-left image**  
- X position = 4 cm (from top-left corner)  
- Y position = 12 cm (from top-left corner)  
- Width = 6 cm  
- Height = 6 cm  

**Bottom-right image**  
- X position = 23 cm (from top-left corner)  
- Y position = 12 cm (from top-left corner)  
- Width = 6 cm  
- Height = 6 cm  

**Slide size**: 1280×718 px  
**Screen size**: 1920×1080 px  
**Export DPI**: 99 pixels/inch  

---

**Step 1 — Conversion Factor**

To convert from cm to pixels:
$$
\text{pixels} = \text{cm} \times \frac{99}{2.54} \approx \text{cm} \times 38.976
$$

At **99 DPI**, every cm ≈ **38.976 px**.


**Step 2 — Convert each measurement**

**Top-center**  
- X = 13.45 × 38.976 ≈ **524 px**  
- Y = 0.5 × 38.976 ≈ **19 px**  
- Width = 6 × 38.976 ≈ **234 px**  
- Height = 6 × 38.976 ≈ **234 px**

**Bottom-left**  
- X = 4 × 38.976 ≈ **156 px**  
- Y = 12 × 38.976 ≈ **468 px**  
- Width = **234 px**  
- Height = **234 px**

**Bottom-right**  
- X = 23 × 38.976 ≈ **896 px**  
- Y = 12 × 38.976 ≈ **468 px**  
- Width = **234 px**  
- Height = **234 px**

---

**Step 3 — IAS File (relative to composite image 1280×718 px)**

```text
# Label        X     Y     Width   Height
TopCenter     524    19     234     234
BottomLeft    156   468     234     234
BottomRight   896   468     234     234
```




---






### How EB Stores IAS References in the EDF 
> 
> When you set **Interest Area Set Name** in a Display to reference the `IASFile` column in your Data Source:
> 
> 1. **During experiment runtime**  
>    - For each trial, EB reads the filename from the `IASFile` column (e.g., `comp1.ias`)  
>    - EB loads that `.ias` file and applies it to the stimulus display for that trial.
> 
> 2. **While recording**  
>    - EB writes a special **IA definition message** into the `.edf` file at the exact moment the trial starts.  
>    - This message contains:
>      - The IA labels (e.g., `Target`, `Competitor`, `Distractor`)
>      - The coordinates and sizes of each IA rectangle
>      - The link between this IA set and the trial ID
> 
> 3. **When you open the EDF in Data Viewer**  
>    - Data Viewer reads the IA definition messages directly from the EDF.  
>    - It reconstructs the IA sets for each trial exactly as they were during the experiment.  
>    - Because your IAS files were named by stimulus role (not position), the exported data’s `IA_LABEL` values always match the correct Target/Competitor/Distractor for that trial.
> 
> **Why this matters**  
> - You don’t need to manually load IAS files later — they’re already embedded in the EDF.  
> - The `IA_LABEL` column in fixation/saccade exports is trustworthy for direct analysis.  
> - Even if the same physical IA coordinates are reused across different trials, the labels are correct because they’re tied to the trial-specific IAS file that EB applied during recording.


---



### Note on Screen and Interest Area Layout
> 
> In this setup:
> - The **full screen resolution** is **1920×1200** pixels (Some computers are **1920*1080**).
> - The **composite stimulus image** is **1280×718** pixels and is positioned in the **center** of the screen.
> - All Interest Area (IA) coordinates are defined **relative to the composite image’s top-left corner**.
> 
> **Interest Area coordinates for this example**:
> ```
> # Label       X     Y     Width   Height
> Target       524   19    233     233
> Competitor   155   466   233     233
> Distractor   892   466   233     233
> ```
> 
> When the composite image is displayed in Experimental Builder:
> - EB draws it centered on the screen (1920×1200).
> - Each IA’s `(X, Y)` coordinate is offset by the composite image’s top-left corner position on the screen.
> - The **Y coordinate** is inverted when converting from EB’s top-left origin to plotting or analysis environments like Matplotlib.
> 
> **Visualization of Layout**:
> 
> <img src="/images/triangleIAS.png" alt="Composite image centered on screen with interest areas" width="500">
> 
> **Why this matters**:
> - The IAS file should always use coordinates relative to the composite image size (1280×718), not the full screen size.
> - As long as the composite image stays centered, the same IAS coordinates will align correctly across trials.


---


### How Gaze Coordinates Are Determined When Using a Centered Composite Image

**Prompt**  
Explain how the coordinates of gazes are determined in this case.


**1. Eye tracker coordinate system**
- The EyeLink tracker samples gaze points in **full screen coordinates**.  
- On this setup, the screen is **1920 × 1080 pixels**.  
- The origin `(0, 0)` is at the **top-left corner of the screen**.


**2. Composite image placement**
- The composite stimulus image is **1280 × 718 px**.  
- Experimental Builder (EB) positions it **centered** on the 1920×1080 screen.  

**Screen offsets:**
- Horizontal offset = (1920 − 1280) ÷ 2 = **320 px** from the left edge.  
- Vertical offset = (1080 − 718) ÷ 2 = **181 px** from the top edge.


**3. Interest Area (IAS) coordinates**
- The `.ias` file stores IA coordinates **relative to the composite image’s top-left corner**.  
- Example: `TopCenter` IA = (524, 19) inside the composite image.

**EB applies offsets when displaying:**

IA_screen_X = Image_offset_X + IA_relative_X   
IA_screen_Y = Image_offset_Y + IA_relative_Y  


For `(524, 19)`:
- Screen X = 320 + 524 = **844**  
- Screen Y = 181 + 19 = **200**


**4. How Data Viewer uses it**
- EB writes the **final screen-space IA coordinates** into the `.edf` file during recording.  
- When the EDF is opened in Data Viewer:
  - The IAs are already in **screen coordinates** matching the gaze samples.
  - If a gaze sample is at `(850, 210)`, Data Viewer checks if it falls inside `(844, 200, width=704, height=704)` and assigns the correct `IA_LABEL`.

**Key takeaway**  
Even though IAS files are designed in **composite image space**, EB applies the **centering offset** at runtime and stores the **true screen coordinates** in the EDF.  
This ensures Data Viewer’s analysis is accurate without any manual coordinate conversion.

---


---

### Mapping Interest Areas from a Centered Composite Image


**🔠 Screen and Image Setup**

* **Experiment screen resolution:** `1920 × 1080` (fullscreen)
* **Composite image size:** `1280 × 718` pixels
* **Composite image position:** **centered** on screen, **not stretched or scaled**
* **Each face tile size (Interest Area):** `233 × 233` pixels (square)

**📀 Composite Image Position on Screen**

Since the image is centered and smaller than the screen:

```
Left/right margin  = (1920 − 1280) / 2 = 320 px  
Top/bottom margin  = (1080 − 718) / 2 = 181 px
```

Thus, the **top-left corner of the composite image** is positioned at **(320, 181)** on the screen.


**🔁 Conversion Rule: Image to Screen Coordinates**

If your interest area (IA) coordinates are defined relative to the image (1280×718), you must convert them to **screen-based coordinates** for use in Experimental Builder (EB).

```text
X_screen = X_image + 320
Y_screen = Y_image + 181
Width and Height remain the same
```

> ⚠️ EB and Data Viewer interpret IA coordinates relative to the full screen, **not** the image. Always apply this conversion before use.


**🧪 Example Conversion**

**Interest Areas in Image Coordinates (1280×718)**

| Label      | X   | Y   | Width | Height |
| ---------- | --- | --- | ----- | ------ |
| Target     | 524 | 19  | 233   | 233    |
| Competitor | 155 | 466 | 233   | 233    |
| Distractor | 892 | 466 | 233   | 233    |

**Converted to Screen Coordinates (1920×1080)**

| Label      | X    | Y   | Width | Height |
| ---------- | ---- | --- | ----- | ------ |
| Target     | 844  | 200 | 233   | 233    |
| Competitor | 475  | 647 | 233   | 233    |
| Distractor | 1212 | 647 | 233   | 233    |


**📄 Ready-to-Use `.ias` Snippet**

```plaintext
# Label       X    Y    Width  Height
Target       844  200  233    233
Competitor   475  647  233    233
Distractor  1212  647  233    233
```

✅ Save this file with `.ias` extension in **plain text**, UTF-8 encoding, and use LF line endings (not Windows CRLF).


**✅ Best Practices for Experimental Builder**

1. **Display**: Set the image action to "centered" and **do not scale** or stretch it.
2. **Interest Areas**: Load the converted `.ias` file as an Interest Area Set.
3. **Test**: Run a test session and visually confirm alignment of the rectangles with image elements.
4. **Environment**: Ensure:

   * Screen resolution is exactly 1920×1080
   * No DPI scaling or OS-level zoom is active
   * Image is not resized at runtime


**🔁 When to Recalculate IA Coordinates**

Recalculate coordinates if:

* You change the **image size**
* You change the **screen resolution**
* You **scale or stretch** the image in EB
* You edit **position or layout** of elements within the composite image


This workflow ensures **pixel-perfect alignment** between your visual stimuli and gaze-tracking data, which is critical for meaningful analysis using Data Viewer.

---