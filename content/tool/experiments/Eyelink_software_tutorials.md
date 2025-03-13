---
title: "Eyelink software tutorial"
date: 2025-01-28
draft: false

---

## Introduction to Experiment Builder: A Step-by-Step Guide
[video link](https://www.youtube.com/watch?v=qCMgHiGbWN4&list=PLOdF-B36TwspI-XgKuRC2xFfa768Lsngv)

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

---

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

---

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

------------------------------------------------------


### Tutorial 05 - Nodes, Connections & Messages

#### Introduction

In this tutorial, we will discuss how actions and triggers connect in **Experiment Builder** to ensure experimental events occur in the correct sequence. We will also explore how **messages** can be used to mark the occurrence of these events in the **EyeLink data file**. 

We will use a **Posner task example** to illustrate these concepts.

---

#### Display Screen Actions

#### *Editing a Display Screen Action*

1. The first display screen action, renamed **"display camera setup instructions"**, presents simple **camera setup and calibration instructions** to the **Display PC monitor**.
2. To **view and edit** the contents of a display screen action:
   - **Double-click** the action node.
   - The **Screen Builder** will open.
   - Here, you can **add images, videos, text, shapes, and interest areas** to create the display content.
3. In this example, a **multi-line text resource** is used to present the instructions.

---

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

---

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

---

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

---

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

---

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

### Populating Data Sources

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

