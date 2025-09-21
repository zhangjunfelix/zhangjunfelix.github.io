---
title: "Eyelink Date Viewer tutorial"
date: 2025-07-19T13:52:18-04:00
draft: false
---

## Data Viewer: A Beginner's Guide to Eye-Tracking Analysis
[video link](https://www.youtube.com/playlist?list=PLOdF-B36TwsqdfpUssFpXNsV3MC5QtHa9)

Welcome to the first tutorial in our **Data Viewer for Beginners** series. If you're new to eye-tracking analysis or just getting started with **SR Research’s Data Viewer**, this guide is for you.

In this post, you’ll learn:
- What Data Viewer is  
- What kinds of eye-tracking data it can analyze  
- How it helps researchers visualize and extract insights  
- Why it's one of the most widely used tools for processing EyeLink data

Let’s take a first look at what makes Data Viewer so powerful and beginner-friendly.

### Tutorial 00: Data Viewer Overview

#### What Is Data Viewer?

**Data Viewer** is a powerful and flexible tool developed by SR Research for analyzing **eye-tracking data**. If you're working with an **EyeLink system**, this is your go-to application for:

- Viewing gaze behavior over time and across conditions  
- Creating visualizations like heat maps  
- Extracting data for statistical analysis  

This tutorial introduces the major functions and benefits of Data Viewer and prepares you to dive deeper in later modules.



#### What Can You Do with Data Viewer?

#### 1. **Inspect Spatial and Temporal Data**

Data Viewer lets you analyze **where** and **when** participants look during a task. You can:

- Compare gaze durations on different parts of an image  
- Track regressions while reading text  
- Analyze saccade amplitude and latency  
- Explore pupillometry over time  

> 📌 Example: See if participants looked longer at **angry faces** than **happy faces**, or how many **regressions** they made during reading.


#### 2. **Batch Processing for All Participants**

Data Viewer supports **batch processing**, meaning you can analyze data from **all participants at once**.

Just:
- **Import all .edf files** into a single session
- Process them collectively
- Export your reports in seconds  

This saves time and ensures consistent output across your dataset.

#### 3. **Define Interest Periods (IPs)**

An **Interest Period (IP)** is a time window during a trial where you want to focus your analysis.

You can:
- Sync IPs to specific experimental events (e.g., stimulus onset)
- Define IPs to last a fixed duration or until another event
- Apply the same IP definition across all trials and participants  

> 📌 Example: Analyze **only the image-viewing part** of a trial and ignore the following question.

#### 4. **Define Interest Areas (IAs)**

An **Interest Area (IA)** defines a region of a visual display where you expect relevant gaze behavior.

- Can be **static** (e.g., text or image studies) or **dynamic** (e.g., video or smooth pursuit)
- Come in various shapes:
  - Rectangle  
  - Ellipse  
  - Freehand  
- Dynamic IAs can **change over time** for more complex studies  

> 🎯 Knowing *where* participants are looking is just as important as knowing *when*.


#### Visualization Tools in Data Viewer

Data Viewer offers a suite of tools to help you visually explore gaze data:

#### Temporal Graph View  
- Displays **eye data over time** (e.g., fixation durations, pupil size trends).

#### Spatial Overlay View  
- Overlays **scan paths** (saccades + fixations) on your stimuli.

#### Animation Playback View  
- Plays back each trial with gaze data overlay  
- Includes **bee swarm mode** and **dynamic heat map mode**

#### Heat Maps and Difference Maps  
- Generate **static or dynamic heat maps**  
- Create **difference maps** to compare conditions or participant groups  


#### Filters and Data Export

#### Filtering Tools
- Apply **temporal** and **spatial** filters  
- Replicate standard preprocessing steps used in eye-tracking research  

#### Data Reports
Data Viewer offers **report generation** for different levels of granularity:

- **Fixations**
- **Saccades**
- **Interest Areas**
- **Time bins**
- **Sample-level data**

Each report:
- Includes **dozens of variables**
- Can be tailored to your specific research questions
- Is exportable to tools like SPSS, R, or Excel


#### Compatibility and Flexibility

Data Viewer works seamlessly with:

- **EyeLink data files** collected via **Experiment Builder**
- Data from **other software**, using SR Research’s communication protocol  

This ensures flexibility no matter what platform you used to run your experiment.


#### Summary: Why Use Data Viewer?

| Feature | Benefit |
|--------|---------|
| 🎞️ Visual Playback | Understand gaze behavior in real time |
| 🔁 Batch Analysis | Process data from all participants at once |
| 🎯 Interest Areas | Define "where" the participant was looking |
| ⏱️ Interest Periods | Define "when" the data matters most |
| 🔥 Heat Maps | Visualize attention distribution |
| 📤 Flexible Reports | Export customizable data summaries for analysis |

> 💡 **Bottom line**: Data Viewer simplifies and enhances your analysis workflow so you can spend more time interpreting results and less time managing files.


####  What's Next?

In the next tutorial, we’ll walk through the **Data Viewer interface** and guide you through setting up your first session.

---


### Tutorial 01: Intro to GUI and Workflow

Welcome to **Tutorial 2** in our beginner’s series on **SR Research’s Data Viewer**.

In this guide, you’ll learn how to:

- Create a new **Viewing Session**
- Import **EDF files** (eye-tracking data)
- Understand the relationship between **EDF files** and **EVS files**
- Set up **Interest Periods**
- Navigate the **Graphical User Interface (GUI)** of Data Viewer

Let’s get started with the Data Viewer workflow.


#### What Is a Viewing Session?

A **Viewing Session** is the central project file in Data Viewer. It contains:

- All your imported **EDF files**
- Associated settings (e.g. Interest Areas, Interest Periods)
- Your visualization and analysis preferences

> 📁 The Viewing Session file uses the `.evs` file extension.

To begin a new project:

- Go to **File → New**
- Or simply launch Data Viewer — it creates a new session by default


#### Importing EDF Files

Once you’ve started a Viewing Session, the next step is to **import the eye-tracking data**.

#### Step-by-step:
1. Click **File → Import Data → Multiple EyeLink Data Files**
2. Navigate to your **experiment folder** (containing participant EDF files)
3. Data Viewer will **automatically detect all EDF files**, even in subfolders
4. Click **Import**

> ✅ If you used **Experiment Builder**, you can point to the **deployed project folder**.


#### EDF vs. EVS: What’s the Difference?

#### EDF Files:
- Contain **raw, binary eye-tracking data**
- **Cannot be edited**
- Include fixations, saccades, timestamps, and messages
- Do **not** include images, videos, or interest areas

#### EVS Files:
- Created when you import EDFs into Data Viewer
- Store your **session-specific settings** and **visual references**
- Can be saved and reopened later

> ⚠️ Always move the **entire experiment folder** (not just EDF files) when transferring projects. Missing files will result in **blank screen views** during analysis.


#### Saving and Moving Viewing Sessions

After importing your data:

- Save your session via **File → Save**
- Data Viewer saves:
  - An `.evs` file
  - Associated folders and files (e.g. stimuli, visualizations)

#### Need to move the session to another computer?
Use **File → Package** to create a `.dvz` file:

- Combines everything into one portable file
- On the new machine, double-click the `.dvz` file or use **File → Unpack** to extract it


#### Setting Interest Periods

Interest Periods allow you to **analyze specific time windows** of each trial.

> 📌 Example: If a picture is followed by a question, you may want to focus analysis only on the **picture period**.

#### Why use them?
- Exclude samples **before and after** stimulus presentation
- Focus on precise trial segments for accurate metrics

#### How to set Interest Periods:
1. Locate the **Interest Period dropdown** (e.g., “Full Trial Period”)
2. Click the arrow and select **Edit**
3. Use the **Interest Period Manager** to define your time windows

Once defined:
- You’ll see visual stimulus content (if linked properly)
- You can switch views like **Spatial Overlay** or **Trial Animation Playback** to see the participant’s gaze during that interval


#### Data Viewer Interface Overview

Let’s walk through the GUI layout.

#### 1. **Inspector Panel (Left Side)**
- **Preferences tab**: Adjust session-wide settings and filters
- **Data tab**: Navigate between trials

#### 2. **Trial View Window**
- Displays visual data per trial
- Change visibility of elements (e.g. fixations, saccades) with buttons at the top
- Switch between view modes (top-left corner buttons):
  - **Temporal Graph View**
  - **Spatial Overlay View**
  - **Trial Animation Playback View**

#### 3. **Middle Panel (Event List)**
- Lists detected events (e.g. fixations, saccades) for the selected trial

#### 4. **Bottom Panel (Event Details)**
- Shows detailed info for the currently selected event

> 📸 You can export visualizations as **images or videos** for presentations or publications.


#### Editing and Exporting Data

#### Add or Edit Interest Areas
- Define new Interest Areas (IA) within Data Viewer
- Adjust existing ones to match your research goals

#### Export Reports
Data Viewer allows you to generate **summary reports** for:

- Fixations  
- Saccades  
- Interest Areas  
- Time bins  
- Sample-level data  

These reports are easily opened in:

- **Excel**  
- **SPSS**  
- **R**  
- **MATLAB**  

> 📊 These reports are key for downstream statistical analysis — we’ll explore them in detail in upcoming tutorials.

#### Summary: What You Learned

| Step | Purpose |
|------|---------|
| 📁 Create Viewing Session | Start a new analysis project |
| 📥 Import EDF Files | Load eye-tracking data |
| 💡 Understand EDF vs. EVS | Know what’s editable and what isn’t |
| ⏱️ Set Interest Periods | Define trial time windows for analysis |
| 🧭 Use the GUI | Navigate trials, adjust settings, and visualize data |
| 📤 Export Reports | Get your data into your preferred stats software |


#### Coming Up Next

In the next tutorial, we’ll show you how to **define Interest Areas** and begin generating **heat maps** and **scan paths**. These visual tools will help you uncover where attention was focused during your experiment.


---


### Tutorial 02: Basic Data Visualization

####  What You’ll Learn

This tutorial introduces the **three main visualization views** in the **Trial View window** of SR Research's **Data Viewer**:

1. Temporal Graph View  
2. Spatial Overlay View  
3. Animation Playback View  

These views allow you to inspect how participants' eyes moved, where they looked, how long they looked, and how their gaze patterns changed over time.

#### Overview of Trial View Window

In Data Viewer, the **Trial View window** is the central panel where you visualize eye movement data for a selected trial.  
It has **three main views**, switchable via **buttons in the top-left corner** of the Trial View window:

- 🔵 First Button: **Temporal Graph View**  
- 🟢 Second Button: **Spatial Overlay View**  
- 🟣 Third Button: **Animation Playback View**

Each view offers different ways to analyze the eye-tracking data collected in your experiment.


#### Temporal Graph View

#### How to Open It

Click the **first button (on the left)** in the top-left corner of the Trial View window.

#### What It Shows

This view presents data as **graphs over time**:

- **X-axis** = Time
- **Y-axis** = One of the following:
  - X/Y Gaze Position (in screen pixels)
  - **Pupil Size** (arbitrary units)
  - **Velocity** (°/sec)
  - **Acceleration** (°/sec²)

#### Viewing Different Data Types

At the **top of the interface**, use the **Data Visibility Buttons** to toggle different elements:
- ✅ Fixations  
- ✅ Saccades  
- ✅ Blinks  
- ✅ Samples  
- ✅ Messages  
- ✅ Button Events  
- ✅ Input Sync Signals  
- ✅ Interest Areas  

These data types will be **displayed in the graph** and **listed in the Inspector** (left panel).

#### Exploring Specific Events

Click on any item (e.g., fixation or saccade) in the **Inspector’s middle panel** to see details in the **bottom panel**.

#### Sample Data Options

At the **bottom of the Trial View window**, toggle visibility for:
- Velocity
- Acceleration
- X/Y Gaze Position
- Pupil Size

#### Visualizing Target Positions

If your experiment used **moving targets** and sent **target position messages** to the EDF file (e.g., via Experiment Builder), Data Viewer can show:
- Eye vs. Target Position traces over time
- These can be exported later as a **Sample Report**


#### Interest Period Boundaries

- Only data within the **Interest Period** is shown
- Marked by **two vertical pink lines**
- Data **outside this window** is **grayed out** by default

#### Zooming and Scrolling

Use **magnifier icons** (top of view) to:
- Zoom in to a selected region
- Zoom out to full view

If the data is longer than the screen can display:
- A **time slider** will appear for scrolling left/right

#### Spatial Overlay View

#### How to Open It

Click the **second button from the left** (top-left corner of the Trial View window).

#### What It Shows

This view **superimposes gaze events** (fixations, saccades, etc.) **on the stimulus** (e.g., image or text) that was shown to the participant during the **Interest Period**.

#### Fixation and Saccade Representation

- **Fixations**:  
  - Shown as **circles**
  - **Center** = X/Y gaze coordinate  
  - **Size** = Duration of fixation (larger = longer)

- **Saccades**:  
  - Shown as **arrows**
  - Start to end positions of eye movement

#### Additional Visibility Options

Toggle:
- Blinks
- Sample traces
- Button presses
- Input sync signals
- Interest Areas

#### Stimulus Display Requirements

- If experiment was created with **Experiment Builder**, stimuli are automatically saved and will be shown as the background.
- If not, ensure your experiment **sent the stimulus paths/messages** correctly to the EDF file.

#### Drawing Interest Areas

Use the **drawing tools** (top of Trial View) to:
- Create new Interest Areas
- Edit existing ones

You can use:
- Rectangles
- Ellipses
- Freehand shapes


#### Animation Playback View

#### How to Open It

Click the **third button from the left** (top-left of the Trial View window).

#### What It Shows

- Plays back the eye movements in **real time** as they occurred during the trial
- Ideal for analyzing trials with **dynamic stimuli** (e.g., videos, animations)

#### Playback Controls

At the bottom of the Trial View window:
- Play/Pause
- Skip to time point
- Adjust **playback speed**

#### Editing During Playback

You can:
- Add/edit **dynamic Interest Areas** that change over time

#### Saving Output

- Save a **still image** of the current view
- Export a **video** of the trial playback for presentations or publications


#### Aggregate Mode (Bonus)

Both **Spatial Overlay** and **Animation Playback** support **Aggregate Mode**, which allows you to:
- Visualize multiple trials together
- Compare data across **conditions** or **participants**

You’ll learn more about Aggregate Mode and grouping in a later tutorial.


#### Summary Table

| View                 | Description                                                            | Best For                              |
|----------------------|------------------------------------------------------------------------|----------------------------------------|
| **Temporal Graph**   | Graphs gaze, pupil, velocity, acceleration over time                   | Time-series analysis                   |
| **Spatial Overlay**  | Superimposes fixations/saccades on visual stimuli                      | Visual inspection of gaze patterns     |
| **Animation Playback** | Plays trial like a video, showing how gaze changed dynamically       | Dynamic stimuli, live-style analysis   |


#### What’s Next?

Now that you’ve learned how to visualize data using the three Trial View modes, the next tutorial will guide you through:

- **Setting Interest Periods**
- **Drawing and editing Interest Areas**
- **Exporting meaningful data reports**


---





### Tutorial 03: Interest Periods


#### What You’ll Learn

In this tutorial, you'll learn how to:
- Understand what an **Interest Period (IP)** is and why it's important
- Define an Interest Period using messages or events
- Apply Interest Periods across all trials and participants
- Create **multiple consecutive Interest Periods**
- Configure output reports to include IP-specific data


#### What Is an Interest Period?

In an eye-tracking experiment, the eye tracker records data continuously throughout each trial — including during **stimulus presentation**, **response collection**, **feedback**, and other events.  
But in many studies, you only want to analyze eye movements during a specific part of the trial (e.g., when a picture is shown).

This is where **Interest Periods (IPs)** come in.

> 🔹 **An Interest Period** defines a start and end time window during each trial.  
> Only data within this time window is included in:
> - Visualizations
> - Analyses
> - Output reports

By setting an IP, you focus your analysis on the time when the participant was engaged with your stimulus of interest.

#### Where to Find the Interest Period Selector

- At the **top of the Data Viewer interface**, locate the **Interest Period Selector**.
- By **default**, the Interest Period is set to `Full Trial Period` (i.e., from start to end of recording for each trial).


#### How to Define a New Interest Period

#### Step-by-Step Instructions

1. Click the **dropdown arrow** in the Interest Period Selector.
2. Choose **`Edit...`** to open the **Interest Period Manager**.
3. Click **`New Interest Period`** to open the **Interest Period Editor**.

#### Set Start and End Events

- You define:
  - The **Start Event** (top section)
  - The **End Event** (bottom section)

These events are typically **EDF messages** sent from your experimental program (e.g., Experiment Builder).

#### ✅ Start Event

- Example: If the message marking the image display was `"DISPLAY_IMAGE"`:
  - Check **EDF Message**
  - Enter `"DISPLAY_IMAGE"` in **Message Text**
  - (Be careful — **case sensitive**!)

- You can apply **offsets** (in milliseconds):
  - Positive offset = start later
  - Negative offset = start earlier

#### ✅ End Event

Options include:
- Another EDF Message (e.g., `"DISPLAY_QUESTION"`)
- A **button press**
- An **input signal**
- A **fixed duration** (e.g., 5000 ms)

#### ✅ Finalize the IP

1. Give your IP a **Label** (e.g., `ViewImage`)
2. Click **OK** to save the IP
3. Make sure your new IP is **selected**
4. Click **OK** again to apply it

Now, **all reports and views** in Data Viewer will only include data **within this Interest Period**.


#### Example Walkthrough

#### Sample Trial Structure

1. Eye-tracker starts recording  
2. Short delay  
3. Image displayed for **5 seconds** → EDF Message: `DISPLAY_IMAGE`  
4. Image replaced by question → EDF Message: `DISPLAY_QUESTION`  
5. Participant presses a key  
6. Feedback displayed for **2 seconds**  
7. Blank screen → Eye-tracker stops

#### Goal

You want to analyze **only the eye movements during image viewing**.

#### IP Setup

- **Label**: `ViewImage`
- **Start**: `DISPLAY_IMAGE`  
- **End**: `DISPLAY_QUESTION`
- Leave offsets as `0` if exact match is desired
- Click OK to confirm


#### Creating Multiple Consecutive Interest Periods (Optional)

If you want to analyze **consecutive time windows** (e.g., 1st, 2nd, 3rd second of gaze):

1. In the Interest Period Manager, choose:
   - `Create Multiple Consecutive IPs`
2. Specify the duration (e.g., 1000 ms)
3. Data Viewer will generate IPs like:
   - `IP_1` → 0–1 sec
   - `IP_2` → 1–2 sec
   - `IP_3` → 2–3 sec

This is helpful for **time-course analyses** (e.g., how gaze behavior changes over time).


#### Output Options for Interest Periods

#### Default Behavior

- Data Viewer only includes data from the **currently selected IP** in reports

#### Include All IPs in Output

1. When generating a report, check:
   - `Create Output Report for All Custom Interest Periods`
2. Data Viewer will add:
   - `IP_INDEX`: numeric ID of IP
   - `IP_LABEL`: the label you provided

#### Choose Output Style

- **One File**:  
  All IPs appear as **rows** in a single output file  
- **Multiple Files**:  
  One separate file per IP

#### Summary

| Feature                      | Description                                                                            |
|-----------------------------|----------------------------------------------------------------------------------------|
| Interest Period (IP)        | A time window that focuses analysis on a specific event or stimulus                   |
| Start/End Events            | Typically EDF messages sent from Experiment Builder (e.g., DISPLAY_IMAGE)            |
| Offsets                     | Adjust IP start/end by ± milliseconds                                                 |
| Multiple Consecutive IPs    | Break a trial into equal-duration chunks (e.g., 1s each)                              |
| Report Options              | Output for current IP only or for all IPs at once                                    |
| Output Formats              | One file (rows = IPs) or multiple files (one per IP)                                  |


#### What’s Next?

You’ve now learned how to:
- Define Interest Periods
- Focus your analysis on key parts of the trial
- Structure outputs for time-based or condition-based reporting

Next up: **Interest Areas (IAs)** — defining where participants looked during your stimulus!


---






### Tutorial 04: Trial Variables and Trial Grouping


####  Overview

**Trial Variables** are the backbone of how Data Viewer organizes your eye-tracking data.  
In this tutorial, you’ll learn how Trial Variables help you:
- Record condition and behavioral data
- Customize and edit your dataset
- Group and regroup trials for efficient analysis and visualization


#### What Are Trial Variables?

**Trial Variables** in Data Viewer are labels or values associated with each trial.  
They help you keep track of things like:

- Experimental **conditions** (e.g., color vs. black-and-white)
- **Participant responses** (e.g., accuracy, reaction time)
- **Stimulus information**, if multiple types were used

These variables are usually defined in your **experimental script** and saved to the **EDF file**.

#### Example:

Imagine this setup:
- Trials involve showing participants either a **black-and-white** or **color** image.
- Participants press:
  - One key for black-and-white
  - Another key for color
- You want to record:
  - The **image type**
  - The **accuracy** of the response
  - The **reaction time**

All this trial-specific information can be saved and handled using **Trial Variables** in Data Viewer.


#### Why Are Trial Variables Important?

Trial Variables are essential because they:

1. **Enrich Output Reports**  
   - Added to **any report** you generate  
   - Keep your condition/response info **alongside eye-tracking data**

2. **Enable Grouping for Analysis**  
   - Group trials by condition or accuracy  
   - Used for **Interest Area (IA)** creation, **visualizations**, and **aggregate reports**

---

#### Where Do Trial Variables Come From?

#### 1. **If You Use Experiment Builder**
- Trial Variables are derived from:
  - **Data Source columns**
  - **Variable Nodes**
- These values are written to the EDF file **automatically at the end of each trial**

#### 2. **If You Use Another Platform**
- Trial Variables must be sent manually via **Trial Variable Messages**
- See the **User Manual** section:  
  *Protocol for EyeLink Data to Viewer Integration → Trial Message Commands*


#### View and Edit Trial Variables

#### Trial Variable Value Editor

Access via:  
**Analysis > Trial Variable Value Editor**

- **Rows** = trials  
- **Columns** = trial variables  
- Edit values manually or:
  - Copy-paste from **Excel**
  - Use keyboard to edit within interface

#### Add New Trial Variables

Use the **Trial Variable Manager**:
- Access via: **Analysis > Trial Variable Manager**
- Click `New Variable`
- Assign a **Label**
- Optionally: set a **default value** for all trials
  

#### Trial Grouping – Organizing Your Data for Analysis

#### Default Grouping

- Data is grouped by **EDF file** (i.e., by participant)
- Shown in the **Inspector** under the **Data tab**
- Expand an EDF file to view its trials

#### Regroup by Trial Variables

You can regroup trials **across files** by one or more Trial Variables.

#### Why Reorganize?

- **Define Interest Areas (IA)** once per condition → apply across similar trials
- **Visualize gaze data** for specific conditions
- Create **aggregate reports** by condition (e.g., across participants)


#### How to Regroup Trials

1. Go to **Edit > Trial Grouping…**
2. Select Trial Variables to use as grouping keys
3. Use the ➡️ arrow to move them to `Selected Variables`
4. Click OK

Now, in the **Inspector**, your data will appear grouped by selected variable values (e.g., `Condition = color` and `Accuracy = correct`).


#### Summary of Key Features

| Feature                          | Description                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
| Trial Variables                  | Store info like condition, response accuracy, RT, etc.                      |
| Source (EB)                     | Data Source columns and Variable nodes                                      |
| Source (Other)                 | Trial messages manually sent to EDF file                                    |
| Trial Variable Editor            | View/edit values directly; supports Excel-like interaction                  |
| Trial Variable Manager           | Add new variables with default values                                       |
| Trial Grouping                   | Organize trials by Trial Variables instead of participant                   |
| Use Cases                        | Needed for IA creation, visualizations, and condition-based reports         |


#### What’s Next?

Now that you understand Trial Variables and Grouping:

- You can **define Interest Areas** that apply across trials
- You can **visualize patterns** across conditions
- You can **generate focused reports** for specific variables


---


### Tutorial 05: Interest Areas Static

**Interest Areas** (IAs) are fundamental to analyzing most eye-tracking experiments. They define specific regions on the screen that are relevant for your analysis, such as words in a sentence, facial features, or saccadic targets.

This tutorial provides a detailed walkthrough for working with **static Interest Areas** in Data Viewer, including creation, editing, grouping, and template application.



#### What Are Interest Areas?

- Interest Areas define parts of the stimulus screen that you want to analyze.
- Examples:
  - **Reading**: Individual words in a sentence
  - **Face Perception**: Eyes, nose, mouth
  - **Saccadic Movement**: Initial and target fixation zones

By using IAs, you can extract data such as:
- Total fixation time (dwell time)
- Fixation counts
- Entry times
- Sequence of fixations


#### Static vs. Dynamic Interest Areas

- **Static IAs**: Do not move within a trial.
- **Dynamic IAs**: Change position (used in video/smooth pursuit studies).
- This tutorial focuses only on **static** IAs.



#### Before Creating Interest Areas

1. **Turn on Interest Area Visibility**  
   - Click the toggle at the top of Data Viewer.
   - Allows you to view IAs in the **Trial View** window.

2. **Set the Interest Period**  
   - IAs apply to specific time windows (e.g., image display).
   - See [Tutorial 03](../tutorial-03-interest-periods) for details on setting Interest Periods.

3. **Auto-imported Interest Areas**  
   - If using **Experiment Builder**, IA info is written into the EDF file.
   - Default reading IA segmentation = space-separated words.
   - Can be customized to segment by phrase/character.

4. **Manual EDF coding**  
   - If using other software, Interest Area messages must follow SR Research syntax.
   - See **Help > Contents > Protocol for EyeLink Data to Viewer Integration > Interest Areas**.


#### Creating Static Interest Areas

#### Step-by-Step

1. Switch to **Spatial Overlay View**.
2. Select a trial.
3. Use the **Rectangle**, **Ellipse**, or **Freehand** tools to draw IAs.
4. Label each IA and press Enter.


#### Grouping Trials for Shared IAs

Creating IAs per trial is tedious. Instead, group trials that use the same stimuli and apply IAs to the entire group.

#### How to Group:

1. Group by Trial Variable (e.g., `imagefile`) via:

Edit → Trial Grouping...


2. Draw IAs on one representative trial in that group.
3. Save the IA set:
- Click save button at top of Trial View.
- Choose **Yes** to add as a template.
4. Apply template:
- In **Inspector**, select the trial group.
- Assign the saved IA set as the default.


#### Editing Interest Areas

- **Resize**: Use the Select Tool + `Alt` key to drag edges.
- **Exact edits**: Use Inspector to edit coordinates.
- **Right-click options**:
- `IA Shape Actions`: Includes duplication, alignment, and distribution.
- **Copy & Paste**: Between trials for efficiency.

#### Interest Area Files (.ias)

- Plain text format.
- Rectangle/Ellipse:
- ID, left, top, right, bottom (pixels), Label
- Freehand:
- ID, list of points, Label

You can create/edit these manually or reuse from other sessions.

#### Importing IA Templates

Go to:
File → Import Data → Interest Area Template


#### Learn More

- See [Tutorial 06](../tutorial-06-interest-areas-dynamic) for **dynamic** IAs.
- Refer to:
  - **User Manual → Working with Events, Samples, and Interest Areas**
  - **SR Research Website**

#### Summary Table

| Task                              | Tool/Command                         |
|-----------------------------------|--------------------------------------|
| View IAs                          | Toggle IA Visibility                 |
| Group Trials                      | `Edit → Trial Grouping...`           |
| Draw Static IAs                   | Rectangle / Ellipse / Freehand Tools |
| Save & Apply IA Template          | Save button + Inspector assignment   |
| Edit IA shape/position            | Select + Alt drag / Inspector edits  |
| Import External IA Set            | `File → Import Data → IA Template`   |


> **Tip**: Always double-check that your Interest Period is correctly set before working with IAs. It ensures you’re tagging fixations in the relevant time window.


---




### Tutorial 06: Dynamic Interest Areas in Data Viewer

In this tutorial, we cover **dynamic Interest Areas** (IA) in Data Viewer. This builds on **Tutorial 05**, which introduced static Interest Areas. If you’re new to Interest Areas in general, we recommend reviewing that tutorial first.

Dynamic Interest Areas allow you to track and analyze how a region of interest **changes over time** in terms of position, shape, or size—crucial for analyzing dynamic stimuli like videos.



#### What Are Dynamic Interest Areas?

Dynamic Interest Areas are similar to static ones, but with two key differences:

- **Static IA**: Defined by a single set of boundaries (rectangle, ellipse, or freehand), and an optional **start time**.
- **Dynamic IA**: Comprised of **multiple instances**, each with its own:
  - Boundary shape
  - **Start time**
  - **End time**

####  Why Use Dynamic IAs?

Dynamic IAs are essential when the visual target moves or changes across time in a trial. For example:
- Tracking a moving object in a video
- Annotating different time-locked events

They allow for:
- Flexible boundary changes
- Time-locked alignment to experimental events
- Easy reusability across similar trials


#### Structure of a Dynamic Interest Area

Each **Dynamic IA** includes:

- **One ID and Label** (like “TargetObject”)
- **Multiple Instances**, each defined by:
  - Shape (rectangle, ellipse, or freehand)
  - Start time (ms from the start of the Interest Period)
  - End time

⏱️ *All time values are relative to the **Interest Period**, not the entire trial.*


#### Step 1: Set the Interest Period

Before creating any Dynamic IAs, **set the Interest Period** properly. This defines the timeline from which all dynamic instance timings will be measured.

#### Example

If your video starts at a certain message (e.g., `VIDEO_ONSET`) and ends with another (e.g., `VIDEO_END`), use these as the **Interest Period Start** and **End Messages**.

Setting this ensures:
- Timing is accurate and relative
- Instances align correctly across trials


#### Step 2: Group Similar Trials

Group the trials based on a variable (e.g., `VideoID`) that identifies which video or condition was shown. This step:

- Helps apply one set of dynamic IAs to all trials with the same stimulus
- Improves organization in the Viewing Session


#### Step 3: Create the First Instance

You can now begin defining the first instance of a Dynamic IA.

#### Method 1: Manual Creation

1. Navigate to the **Animation Playback View**.
2. Use the **slider** or **arrow buttons** to scrub to the desired time.
3. Use **drawing tools** (rectangle, ellipse, or freehand) to define the region.
4. Check the **"Dynamic IA"** box and give it a label (e.g., “Ball”).
5. Fine-tune:
   - Start Time
   - End Time

📌 *Remember: time is relative to the start of the Interest Period.*


#### Step 4: Add More Instances

#### Option 1: Manual Drawing

Repeat the process for each time segment you need a new boundary:
- Navigate to the new time
- Draw the new shape
- Confirm start and end times

Use this for small numbers of instances.

#### Option 2: Copy and Paste

Speed up creation using these right-click options:

| Action         | Result |
|----------------|--------|
| `Copy` + `Paste` | Pastes instance at same time as original |
| `Paste Current` | Pastes with same duration but start time is current time |
| `Paste After` | Pastes after previous instance ends |

🎯 Use [ALT] + drag to move/resize instances.

#### Option 3: Mouse Record Method (Best for many changes)

1. Right-click the first instance > **Mouse Record**
2. Playback the trial (slow it down if needed)
3. Click at each timepoint where the IA should shift
4. Fine-tune later in **Inspector** or directly on screen

🔄 Interpolation is auto-applied to make transitions smooth.


#### Step 5: Clean Up Overlaps

Sometimes instances overlap in time.

Use:  
**`Cleanup Dynamic Interest Area`** → Removes overlap  
🔸 Later instance takes priority, earlier ones are trimmed.


#### Step 6: Save and Apply to Other Trials

1. After all instances are defined:
   - Save the IA Set to disk
   - Say “Yes” to import as **template**
2. Set as **Default IA Set** for the grouped trials

This applies the dynamic IA to **all similar trials** in your session.


#### Want to Learn More?

Check out the [Data Viewer User Manual](https://www.sr-research.com/support_data_viewer_manual/) section:

**Working with Events, Samples, and Interest Areas → Interest Areas**


#### Summary Table

| Feature | Static IA | Dynamic IA |
|--------|------------|------------|
| Shape Types | Rectangle, Ellipse, Freehand | Same |
| Time Info | Optional Start Time | Start + End Time for each instance |
| Movement | Fixed | Can change over time |
| Usage | Images or single-state stimuli | Videos, animations, dynamic trials |


---





### Tutorial: 07 - Filtering Cleaning and Adjusting Data

####  Introduction

Data Viewer is designed to maximize the quality of eye-tracking data with its default settings. However, in some cases, researchers need to filter or edit the data further. This tutorial introduces several tools available in Data Viewer to:

- Filter eye movement data (e.g. fixations, blinks)
- Clean fixation data (especially useful for reading studies)
- Manually adjust or drift-correct fixation positions

> ⚠️ **Important:** Before applying any filtering or editing, always save a **backup copy** of your Viewing Session using `File -> Save As...`. These changes cannot be undone and may impact your final analyses.


####  Fixation, Blink, and Interest Period Filtering

You can access basic filtering options from:

**📍 Preferences Tab → Inspector → Data Filters Section**

#### Key Options:

1. **Minimum Fixation Duration**
   - Exclude fixations below a certain duration threshold (e.g. less than 80 ms).
   
2. **Merging Close Fixations**
   - Merge consecutive fixations that are:
     - Spatially close
     - Individually too short to be considered valid
     - Combined duration meets the minimum threshold

3. **Blinks and Pupil Data**
   - Define how data around **blinks** is treated (e.g. exclude, interpolate).
   - Useful for studies involving **pupil size analysis**.

4. **Static IA Outside Interest Period**
   - Exclude static Interest Areas outside the active **Interest Period**.
   - Prevents irrelevant IAs from interfering with analysis.

5. **Fixations Across Interest Period Boundaries**
   - Control how fixations that **start before** or **end after** the Interest Period are handled:
     - Trim
     - Include partial
     - Exclude

> These choices affect both on-screen displays and exported reports.

📘 Learn more:  
**Help → Contents → Preference Settings → Data Filtering**


####  4-Stage Fixation Cleaning Function (For Reading Studies)

Eye-tracking studies on reading often apply specific cleaning methods. Data Viewer supports this through the **4-Stage Fixation Cleaning** tool.

#####  How to Use:

1. Select:
   - A trial
   - A group of trials
   - Or the whole Viewing Session in the **Inspector**
2. Right-click → **Perform 4-stage Fixation Cleaning**

#### The Four Stages:

Each stage is applied **sequentially**. You can uncheck any to skip them.

To see a breakdown of each stage, click the **Fixation Cleaning Help** button in the dialog.

> This tool is commonly used in published reading research and can help standardize data across studies.


####  Manually Adjust or Drift-Correct Fixation Positions

Sometimes fixations may appear slightly off due to **drift** or **tracking noise**. These can be manually adjusted:

#### Steps to Adjust Fixation Positions:

1. Open the **Trial View → Spatial Overlay** tab.
2. **Turn off visibility** for all data **except fixations**.
3. **Click and drag** to select the fixations you want to adjust.
4. Hold **[ALT]** and use **arrow keys** to nudge them.
5. To drift-correct:
   - Use `Edit → Drift Correct` or press **[CTRL + D]**
   - This aligns fixations **vertically**, preserving horizontal position

#### Fixation Circle Tips:

- **Center** = Actual X, Y coordinate
- **Size** = Fixation duration (larger = longer)
- Only the **center** is checked for IA inclusion, not the full circle


####  Summary: When and Why to Use Filtering

| Situation | Use This Tool |
|----------|----------------|
| Your data has very short fixations | Apply minimum fixation duration filter |
| You want to merge nearby short fixations | Enable merging filter |
| Pupil size analysis | Configure blink handling |
| Reading studies | Use 4-Stage Cleaning Function |
| Slight tracking drift | Manually adjust fixations or apply drift correction |


#### Learn More

For further details, consult the official documentation:

📘 **Help → Contents → Preference Settings → Data Filtering**


Filtering and adjusting data isn't always necessary, but it's valuable when working with:
- Sub-optimal data quality
- Pupil data analysis
- Published paradigms that require precise control

Always make a backup before applying changes!

---



### Tutorial 08: Fixation Maps and Aggregate Viewing 
#### 🎯 Overview

This tutorial walks you through how to visualize gaze data using **Fixation Maps**, **Dynamic Fixation Maps**, **Difference Maps**, and the **Aggregate Mode** in **Data Viewer**. These visualization tools allow researchers to explore viewing patterns across participants or experimental conditions—perfect for generating images and animations for presentations, posters, or publications.


####  What is a Fixation Map?

A **Fixation Map** (also called a **heat map**) displays where and how long participants looked at different regions on the screen.

- **Hotter colors** = longer gaze durations.
- Each fixation is rendered as a **2D Gaussian blob**.
- Fixation **duration** determines the **height (intensity)** of the Gaussian.
- The **inner 90%** of each Gaussian is colored.
- If multiple Gaussians overlap, their durations are **summed** visually.

#### How to Create a Fixation Map

1. **Select a trial** (or group of trials) in the Inspector.
2. **Right-click** → `Create Fixation Map`.
3. Choose where to save the output image file (default is the Viewing Session's output folder).

> ✅ Tip: Fixation maps are always saved as image files.


#### Creating Group-Based Fixation Maps

To create a heat map for **a whole group of trials** (e.g., all trials where a "happy" face was shown):

1. Go to `Edit → Trial Grouping…`
2. Select a grouping variable (e.g., Emotion condition).
3. In the Inspector, select the group (e.g., "Happy").
4. Right-click → `Create Fixation Map`.

This will generate a **group-averaged fixation map**.


#### Creating a Difference Fixation Map

A **Difference Fixation Map** compares viewing patterns **across two conditions**.

#### Steps:

1. Hold **CTRL** and select two groups in the Inspector.
2. Right-click → `Create Difference Fixation Map`.

- The resulting image highlights **differences** in gaze activity.
- **Color legend** shows which group had increased activity.
- The **order of selection** determines the subtraction direction.


#### Trial View Integration: “Create and Use Fixation Map”

You can also view fixation maps **within** the Trial View:

1. Open the **Spatial Overlay** view in the Trial View window.
2. Click `Create and Use Fixation Map`.

> This generates a **temporary visualization** based on the data visible in the current trial.

#### Aggregate Mode: Visualizing Multiple Trials

Aggregate Mode enables viewing **multiple trials at once** in both:

- **Spatial Overlay** view
- **Animation Playback** view

#### How to Use Aggregate Mode:

1. Activate **Aggregate Mode**.
2. Select a trial or trial group.
3. Data for all relevant trials will be displayed together.


#### Dynamic Heat Maps in Animation Playback

Within **Aggregate Mode**, you can visualize changes in fixation over time using **Dynamic Heat Maps**.

#### Steps:

1. Go to **Animation Playback** view.
2. Enable the `Enable Dynamic Heat Map` button.
3. A heat map window will animate over time, centered on the current playback position.


#### Configuring Fixation Map Preferences

Under the **Preferences tab**:

1. Navigate to `Output Analysis → Fixation Map`.

You can change:

- **Type of Fixation Map**:
  - Fixation Duration (default)
  - Fixation Count
  - Duration Density
  - Count Density
- **Gaussian Settings**
- **Presentation Settings**
- **Dynamic Map Settings**

####  Further Reading

To dive deeper, consult the following sections in the **Data Viewer User Manual**:

- `Data, Analysis, and Output → Fixation Map`
- `Preference Settings → Fixation Map`

Access via: `Help → Contents`


#### Summary

| Feature                    | Description                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| Fixation Map              | Visualizes gaze using heat intensity based on duration.                     |
| Difference Fixation Map   | Compares gaze between two groups.                                           |
| Aggregate Mode            | Combines data from multiple trials for visualization.                       |
| Dynamic Heat Map          | Animates fixation changes over time.                                        |
| Preferences               | Customizes type, smoothing, density, and other display parameters.          |

--- 


### Tutorial 09: Generating Output Reports

#### Introduction

The final step of most research studies using **Data Viewer** involves exporting the actual **data files** for statistical analysis. This tutorial introduces:

- Different types of **output reports**
- How to **select and organize variables**
- When to use each **report type** (Fixation, Interest Area, Sample)
- Options for **filtering and excluding** trials


#### Types of Reports

You can generate reports by navigating to:

Analysis → Reports


Each report type determines what **each row** in the output file represents:

| Report Type       | Row Represents                        |
|-------------------|----------------------------------------|
| Fixation Report   | One fixation                          |
| Saccade Report    | One saccade                           |
| Interest Area     | One interest area                     |
| Sample Report     | One sample (e.g., 1000 Hz = 1000 rows/sec) |


#### Variable Selection

When creating a report:

1. A **dialog window** appears.
2. Select variables from the **Available Variables** list.
3. Move them to the **Selected Variables** section using the arrow button.

> ℹ️ Definitions for each variable are shown below when clicked.

By default, these two variables are always included:

- `RECORDING_SESSION_LABEL` – EDF file name
- `TRIAL_INDEX` – Trial number per participant


#### Example: Fixation Report

To analyze fixation-level data, you might select:

- `CURRENT_FIX_INDEX` – Fixation order within trial
- `CURRENT_FIX_DURATION` – Duration of each fixation
- `CURRENT_FIX_X` and `CURRENT_FIX_Y` – Gaze coordinates
- `CURRENT_FIX_PUPIL` – Pupil size
- Interest Area variables (will be NA if fixation not in IA)

#### Including Trial Variables

- Scroll to the **bottom** of Available Variables list (they are in **blue**).
- These often encode **condition information** or **behavioral data** (e.g., accuracy, RT).

#### Reordering Variables

Use the **up/down arrows** in the Selected Variables panel to customize the column order.


#### Participants & Interest Periods Options

You can customize output scope:

- Create **one report per participant**
- Include **all Interest Periods**, either:
  - Combined into one file
  - Split into separate files

Use settings at the **bottom** of the report creation dialog.


#### Opening the Output

Once the report is created, open it in:

- **Excel** for preview
- **R/SPSS/JASP** or any other statistical tool for analysis

Each row = one event (e.g., fixation), and each column = one variable.


#### Interest Area Reports

Each **row** = one **Interest Area** (IA) per trial.

Recommended variables:

- `IA_ID` – Interest Area identifier
- `IA_LABEL` – Text label for the IA
- `IA_DWELL_TIME` – Total fixation duration in IA
- `IA_DWELL_TIME_%` – % of time spent in IA

Additional metrics:

- **Run count** (consecutive fixations)
- **First fixation time**
- **FSA (Fixation Sequence Analysis)** variables: Transitions between IAs

Include Trial Variables (conditions, RTs, etc.) as needed.


#### Sample Reports

For **fine-grained** time-series data:

- Each row = 1 **sample**
- Useful for studies on **smooth pursuit**, **microsaccades**, etc.

Each row may include:

- Eye position (X/Y)
- **Velocity**, **acceleration**
- **Pupil size**
- If available: **target motion** data (position, velocity)
- **Resolution info**: Pixels per degree (X/Y)

#### Binocular Recordings

- Variables with `LEFT_` or `RIGHT_` show per-eye data.
- Some variables provide **average values** across both eyes.


#### Excluding Trials

To exclude data:

1. Select a trial or group in the **Inspector**
2. Enable the checkbox: `Exclude from Reports`

> This prevents that data from being included in any output file.


#### Report Preferences

Under the **Preferences tab** → `Output Analysis`, you can configure:

- Report formatting
- Default variables
- Trial selection behavior


#### Learn More

The full list of variables and report settings is available in the **Data Viewer User Manual**:

- `Help → Contents`
  - `Data Analysis and Output`
  - `Output Reports`


#### Summary Table

| Feature                   | Description                                                           |
|---------------------------|-----------------------------------------------------------------------|
| Fixation Report           | One row per fixation; includes spatial/temporal metrics               |
| Interest Area Report      | One row per IA; includes dwell time, sequence data, IA-level info     |
| Sample Report             | One row per recorded sample (e.g., 1000/s); ideal for time series     |
| Trial Variable Inclusion  | Add condition info, behavioral data like accuracy or RT               |
| Exclude Trials            | Use Inspector to prevent specific trials from report output           |
| Customize Columns         | Use arrows to choose and reorder variables                            |

---



### Tutorial 10: Time Course (Binning) Analysis Reports
#### Introduction

In the previous tutorial, we discussed various Report types like Fixation, Saccade, Sample, and Interest Area Reports. In this tutorial, we’ll explore the **Time Course (Binning) Analysis Report**, which is especially useful for **Visual World** studies, but applicable to other paradigms as well.

- This report divides trial time into **equal-sized bins** (e.g., 20 ms).
- It calculates the **percent of gaze samples** that fall into different **Interest Areas** during each bin.
- It's ideal for tracking **attention over time** and comparing across **conditions or groups**.

You can access this feature via:

Analysis → Reports → Time Course (Binning) Analysis


#### Time Course Report Setup

####  Bin Duration

- **Default**: 20 milliseconds per bin
- Each **row** in the report = one time bin

You can customize this duration to best match the temporal resolution required by your study.

#### Selecting Variables

1. Choose the variables to include as columns.
2. Use the **arrow** to move selected items into the output.
3. Click each variable to view its **definition** at the bottom.
4. Reorder columns using **up/down arrows**.

#### Variables with Asterisks (`*`)

Some variable names include an asterisk (e.g., `AVERAGE_IA*_SAMPLE_COUNT_%`):

- These will create **one column per Interest Area**
- Plus **one extra column** for samples **outside any Interest Area**
- For example, if you have 4 Interest Areas, this produces **5 columns**:
  - `IA1`, `IA2`, `IA3`, `IA4`, `IA0` (non-IA)

#### Eye Data Sources

- Some variables are based on **averaged data from both eyes**
- Others are **left- or right-eye specific**
- Choose based on your **recording setup**

#### Report Filtering Options

You can refine which data contribute to the report:

#### Max Bins

- Prevents excessive data for **long or outlier trials**

#### Number of Interest Areas

- Defaults to **4 IAs**
- You can specify a different number and assign **labels/indexes**

#### Sample Filtering

- Based on:
  - **Gaze position**
  - **Fixation/Saccade status**

Useful to remove noisy or off-screen data.


#### Averaging Across Groups or Conditions

You can optionally generate a **collapsed report** with data **averaged by condition**:

#### Steps:

1. Go to:
Edit → Trial Grouping...

2. Group by a trial variable (e.g., `condition`)
3. Enable the **“Separate Collapsed Report”** option
4. Data will be:
- Collapsed across all trials per group
- Output in a **second file**

✅ This is particularly useful when comparing **conditions** in group-level analyses.


#### Output Example

When you open the report (e.g., in Excel), you will see:

- Each **row = one time bin**
- Each **column = one variable or Interest Area**

#### Example:

| BIN_INDEX | IA1_% | IA2_% | IA3_% | IA0_% |
|-----------|-------|-------|-------|-------|
| 1         | 15.0  | 25.0  | 50.0  | 10.0  |
| 2         | 20.0  | 30.0  | 40.0  | 10.0  |
| ...       | ...   | ...   | ...   | ...   |

📁 If you generated a **collapsed report**, it will contain:

- **Averaged values** across all trials for each group
- One row per **bin** per **group**


#### Learn More

To explore further:

Help → Contents → Data Analysis and Output → Time Course (Binning) Analysis


This section includes:

- Variable definitions
- Sample reports
- Detailed setup instructions


#### Summary Table

| Feature                     | Description                                                   |
|-----------------------------|---------------------------------------------------------------|
| Bin Size                    | Duration of each time slice (e.g., 20 ms)                     |
| Interest Area Breakdown     | One column per IA + one for non-IA samples                   |
| Eye Source Options          | Left, Right, or Averaged data                                 |
| Grouping/Collapsing         | Average data across trials grouped by conditions              |
| Output                      | One row per bin, multiple columns for chosen variables        |
| Sample Filtering            | Filter by position or eye movement status                     |


---

## Notes to Webinar: Data Viewer Overview & EDF File Structure

[**link to video**](https://www.youtube.com/watch?v=3S1M2imgT5U&list=PLOdF-B36TwsqU0e7sVrcXHIBPdxfh7CNJ&index=1)

[**sample data**](https://drive.google.com/drive/folders/1b1luwbm1J0wyK4ugiRN9yWAYeFqc1mgE)

#### Introduction & Overview  
**0:10 – 2:49**  
- **Welcome & Purpose**  
  - “Quick webinar” highlighting recent features in the latest Data Viewer.  
  - Brief refresher on basic functionality for new users.  
  - Q&A time anticipated at the end.  

- **Agenda**  
  1. **Basics & File Contents** (EDF structure)  
  2. **Aggregate Mode** & Aggregate Reports  
  3. **Fixation Maps** (incl. Difference/Heat Maps)  
  4. **Interest Area Manipulation** tools  
  5. **Time Series (Binning) Reports**  
  6. **Interest Period** creation & multi-period reporting  
  7. **Event Editing**  

- **History & Evolution**  
  - Data Viewer has been around ~15 years.  
  - Early analyses were manual (e.g. ruler measurements → digital pad).  
  - Today’s webinar focuses on the most recent additions since version 3.1.

- **Key New Features in DV 3.1**  
  - Aggregate mode & aggregate reports  
  - Static, dynamic & difference fixation (heat) maps  
  - Enhanced interest‑area shape tools (resize, flip, rotate)  
  - Binning/time‑series reports  
  - Support for multiple interest periods  
  - Event‑editing interface  


#### EyeLink EDF File Overview  
**3:38 – 10:25**  

Data Viewer is designed to load **EDF** (EyeLink Data Files), which are **binary** files containing three primary data types:

#### 1. Samples  
- **One per eye‑tracker frame**  
  - 1000 Hz → 1 ms/sample; 500 Hz → 2 ms/sample.  
- **Columns**:  
  1. Timestamp (ms)  
  2. X gaze pixel coordinate  
  3. Y gaze pixel coordinate  
  4. Pupil area (arbitrary units)  
- **Missing samples** shown as `.` (dots).  
  - Can replace dots in Sample Reports for compatibility with R, MATLAB, SPSS, etc.  
- **Optional extra columns** (via EDF→ASCII conversion):  
  - Screen resolution (pixels/deg.)  
  - Eye velocity  
  - Parallel‑port status (for EEG or other device sync)  

#### 2. Events  
- **Pairs** of start/end records define saccades & fixations:  
  - `ENDSACC → STARTFIX`; `ENDFIX → STARTSACC`.  
- **Saccade detection** uses velocity/acceleration thresholds (e.g. >30 °/s).  
  - Fixations are simply the intervals between detected saccades.  
- **Event metadata** includes:  
  - Onset/end timestamps  
  - Duration (ms)  
  - Average X/Y gaze & pupil size (for fixations)  
  - Amplitude & peak velocity (for saccades)  

#### 3. Messages  
- Timestamped labels inserted by your experiment script or Data Viewer itself.  
  - **Stimulus events** (e.g. trial start, response, custom markers).  
  - **Data Viewer messages** (`!V …`) link to stimulus files (images, text, videos).  
- **Best practice**: always copy the entire experiment folder (EDF + stimuli).  
  - Without matching stimuli files and `!V` messages, Data Viewer cannot display your trials correctly.


#### Trial Grouping & Aggregate Mode  
**14:19 – 15:02**  

- **Trial Grouping**  
  - Organize trials by any trial variable (e.g., participant, condition, duration).  
  - Essential to encode all variables you may later want to group by during experiment design.

- **Aggregate Mode**  
  - When enabled, displays data from all trials under a grouping node simultaneously.  
  - Available in Spatial Overlay, Animation Playback, and Fixation Map generation.  
  - Combine with **aggregate reports** to rapidly compute summary statistics across your chosen groups.

---



## Webinar - Data Analysis for the Visual World Paradigm Using Data Viewer
[Link to video](https://www.youtube.com/watch?v=WOmBxgdq6bA&list=PLOdF-B36TwsqU0e7sVrcXHIBPdxfh7CNJ&index=3)

[Sample Data](https://drive.google.com/drive/folders/1b1luwbm1J0wyK4ugiRN9yWAYeFqc1mgE)

#### Introduction

In this tutorial we’ll walk through how to use **Data Viewer** to analyze eye‑tracking data collected in a **Visual World Paradigm** experiment. You’ll learn how to:

- Load and inspect EyeLink EDF files  
- Define **Interest Areas (IAs)** for target, competitor, distractor, etc.  
- Create **Interest Periods** tied to auditory events (e.g., word onsets)  
- Group trials by experimental condition (e.g., NP1 vs. NP2 bias)  
- Generate **Time Course (Binning) Analysis Reports** to quantify gaze over time  
- Collapse reports across trials/participants for statistical analysis  
- Export and visualize your results  

> **Prerequisites:**  
> - EyeLink EDF files with messages marking stimulus onset, word onsets, etc.  
> - Data Viewer 3.1 or later  


#### 1. Load Your Data

1). **Open Data Viewer** and go to **File → Open Viewing Session…**  
2). Select your EDF files (or an existing `.vdx` session) and click **Open**.  
3). In the **Inspector**, confirm you see your participants and trials listed.


#### 2. Define Interest Areas

You’ll need IA‘s corresponding to each on‑screen object (e.g., NP1, NP2, distractor, filler).

1). In the **Trial View** window, switch to the **Spatial Overlay** tab.  
2). Use the **Interest Area** tools to draw regions over each object:
   - **Elliptical** for character images  
   - **Rectangular** for text or other regions  
3). **Name** each IA in the **Properties** panel (e.g., “NP1”, “NP2”, “Distractor”).  
4). Once your first trial is annotated, click **Save Interest Area Set…** and give it a descriptive name (e.g., `VW_IAs`).  
5). To apply this template to all trials, create a grouping that clusters **all trials** under one node (see next section), then in the **Inspector** set **Default Interest Area Set = VW_IAs**.

#### 3. Create Interest Periods

Interest Periods define the time window over which gaze is measured (e.g., from sentence onset to question screen).

1). Switch to the **Temporal View** and open the **Interest Periods** panel.  
2). Click **New…** and configure:
   - **Name:** `SentenceWindow`  
   - **Start event:** message `PlaySound`  
   - **End event:** message `DisplayQuestion`  
3). Click **OK**. You should see the grey‑shaded window in the timeline.  

> **Tip:** You can also create a **scrolling series** of Interest Periods (e.g., 500 ms bins) by checking **“Create multiple consecutive IPs”** and specifying duration and count.

#### 4. Group Trials by Condition

To compare NP1‑ vs. NP2‑bias trials:

1). Go to **Edit → Trial Grouping…**  
2). Select the variable that codes your bias condition (e.g., `BiasType`) and click **Group**.  
3). In the **Inspector**, confirm you now have two grouping nodes: **NP1_Bias** and **NP2_Bias**.  

#### 5. Configure Cyclopean Mode (Monocular Data)

If your experiment recorded **monocular** data inconsistently (right vs. left eye):

1). In the **Inspector** Preferences tab, under **Output Analysis**, check **“Cyclopean mode”**.  
2). This lets you use **average‑eye** variables (e.g., `AVERAGE_IA*_SAMPLE_COUNT_%`) without worrying about empty left/right columns.


#### 6. Generate a Time Course (Binning) Report

  1). With your **SentenceWindow** IP selected, go to **Analysis → Reports → Time Course (Binning) Analysis**.  
  2). In the dialog:
   - **Bin size:** `20` ms (default)  
   - **Variables:**  
     - `Condition` (your grouping variable)  
     - `AVERAGE_IA*_SAMPLE_COUNT_%`  
   - **Separate Collapsed Report:** check to average across all trials in each group  
  3). Click **Run**.  
  4). When prompted, save your session. Data Viewer will write two CSVs:
   - **raw** time‑course per trial/bin  
   - **collapsed** time‑course averaged by group  


#### 7. Inspect & Visualize

1). Open the **collapsed** CSV in Excel, R, or Python.  
2). You’ll see columns:
   - `GroupingIndex` (e.g., 1 = NP1_Bias, 2 = NP2_Bias)  
   - `InterestArea_1`, `InterestArea_2`, …, `InterestArea_0` (null region)  
3). Plot each IA’s `% samples` over time (e.g., line chart) to reveal gaze biases unfolding around key words.


#### 8. (Optional) Aggregate Reports & Heat Maps

- **Aggregate Event Statistics:**  
  - **Analysis → Reports → Aggregate → Event Statistics**  
  - Provides summary (fixation count, duration, saccade amplitude) per group.  

- **Dynamic Fixation Maps:**  
  - Turn on **Aggregate Mode** in the toolbar.  
  - In **Animation Playback**, click **Enable Dynamic Heat Map**.  
  - Color‑code by group to inspect how gaze patterns diverge over time.


#### 9. Troubleshooting & Tips

- **Missing stimuli in Trial View?**  
  – Ensure you copied your experimental folder (images/videos) alongside EDFs so Data Viewer can follow `!V IMGLOAD <path>` messages.  
- **Dots (`.`) in sample report?**  
  – Use the **Replace Missing Samples** option in the Sample Report dialog to convert dots to `NaN` or `0` for easier downstream analyses.  
- **Custom IP series**  
  – Use **“Create multiple consecutive IPs”** to generate coarse-grained time blocks (e.g., 8×500 ms bins) for higher‑level temporal comparisons.


#### Further Reading

- **Data Viewer User Manual →**  
  - *Data, Analysis, and Output → Time Course (Binning) Analysis*  
  - *Preference Settings → Output Analysis → Fixation Map*  

---


##  Recommended Data Viewer Workflow (From Data Viewer User Manual)
*Chapters in the workflow refer to the ones in the Manual*

1. **📁 Create a New Viewing Session**  
   - Start by creating and saving a new **viewing session**.  
   - See **Chapter 4** for detailed guidance on managing data viewing sessions.

2. **📥 Import EDF Files**  
   - Load **one or more EDF files** into your viewing session.  
   - Refer to **Section 4.5** for step-by-step instructions.

3. **⏱ Set Interest Period(s)**  
   - Focus your analysis on specific time windows within a trial by creating **interest periods**.  
   - See **Section 7.4** for creating and managing these periods.

4. **🎯 Check Interest Areas (IAs)**  
   - Verify that all **Interest Areas** are correctly set.  
   - See **Sections 6.10** and **8.3.6** for creating, loading, and editing IAs.

5. **👁 Create Visualizations (Optional)**  
   - Use Data Viewer’s visualization tools to inspect **temporal** and **spatial** aspects of your data:
     - Spatial Overlay
     - Animation Playback
     - Temporal Graphs
     - Fixation Maps  
   - See **Chapter 5** and **Section 7.2** for details.  
   - Also check **Sections 8.3.4** and **8.3.5** to confirm integration messages from your display software.

6. **⚙ Set Preferences**  
   - Ensure all relevant **preferences** are configured correctly.  
   - See **Chapter 9** for available settings.

7. **📊 Set Trial Condition Variables**  
   - Make sure all necessary trial condition variables are defined.  
   - See **Section 7.1** for manual setup, and **Section 8.3.2** if sending variables from your display software.

8. **📝 Create Reports**  
   - Generate **summary reports** based on:
     - Trials
     - Interest Areas
     - Fixations
     - Saccades
     - Time Bins
     - Samples  
   - See **Sections 7.5–7.13** for report options and configurations.

---

## 💡 Tip for Beginners
Following this structured workflow helps ensure:
- All necessary variables and regions of interest are in place before analysis
- Visual checks confirm your data integrity
- Reports are generated with correct parameters, avoiding rework later



--- 




## Time Course (Binning) Analysis Report

### Time Course (Binning) Analysis Report manual


#### 🌐 What Is Time Course (Binning) Analysis?

**Time Course (Binning) Analysis** in Data Viewer lets you examine how gaze behavior changes *over time* during a trial. This analysis is especially useful when your study focuses on the **time course of cognitive processes** as revealed by eye movements.

#### ❓ Why Use It?

Researchers use this method to:

* Analyze **when** participants begin fixating on specific Interest Areas (IAs)
* Track gaze **transitions over time**
* Compare fixation patterns across conditions or trial types

It is commonly used in:

* **Visual World Paradigms**
* Studies with **dynamic stimuli** (e.g., videos)

The Time Course Analysis replaces the older Visual World Python scripts and runs much faster, with more flexibility and integrated settings.


#### Key Features

* Breaks each trial into equal-sized **time bins** (e.g., every 20ms)
* Tallies fixations per Interest Area in each bin
* Generates:

  * **Trial-based report** (per trial per bin) (which provides data output for each consecutive time window for each trial in the viewing session)
  * **(optional) Collapsed report** (which provides average data in the same time window across all trials and participants within each trial group). The collapsed report allows users to examine how likely the participants are, on average, at a given moment in time, to look at each of the interest areas. 
* Includes data for **blink**, **off-screen**, and **excluded samples**


####  Before You Start: Load Samples

The Time Course Analysis will only be available if samples are loaded.

1. Open Data Viewer
2. Go to `Preferences → Data Loading`
3. Ensure **"Load Samples"** is checked
4. Optional: Right-click top-level node and choose **"Save Properties as Defaults"**
5. Load your `.edf` file(s)  
`Go to File → Open Viewing Session…`  
`Select the .edf file(s) you wish to open`   
`Click Open`


#### Steps to Create a Time Course Analysis Report

#### ① Open the Report Menu

From the menu:

```
Analysis → Reports → Time Course (Binning) Analysis...
```

#### ② Select Output Variables

1. Choose variables from the left (Available Variables)
2. Press `>>` or drag into the right (Selected Variables)
3. Use arrows to reorder or drag & drop
4. Optional: Export/Import variable lists

   * Export: `Analysis → Reports → Export Report Variable Selection...`
   * Import: `Analysis → Reports → Import Report Variable Selection...`


> 📌 **Note on `AVERAGE_*` Variables and Cyclopean Mode**
>
> - Variables that begin with `AVERAGE_` are affected by the **Cyclopean Mode** setting (found in **Output/Analysis Preferences**).
>
> - In **monocular recordings**, or when one eye is missing in binocular recordings:
>   - If Cyclopean Mode is **disabled**, `AVERAGE_*` variables will return **missing values**.
>   - If Cyclopean Mode is **enabled**, the output will use data from the **available eye**.
>
> - Cyclopean Mode has **no effect** if **both eyes** have valid (or both missing) data.
>
> - When creating a Time Course (Binning) Report that includes `AVERAGE_*` variables, **Data Viewer will prompt** you to enable Cyclopean Mode if needed.
>
> - ✅ Enabling Cyclopean Mode is helpful for comparing data across participants with recordings from different eyes.



####  Configuration Settings (Detailed)

**Bin Interval**

* Duration of each bin in milliseconds (default: 20ms)

**Max Number of Bins**

* Maximum bins per trial (default: 2000)
* Set to `-1` to auto-adjust based on longest trial

**Interest Areas Used**

* Leave blank: uses IAs 1-4
* Input comma-separated list (e.g., `Target, Competitor`)
* Must match actual IA IDs or labels
* Supports up to 10 interest areas

> ⚠️ For collapsed reports, ensure **IA consistency across trials** (e.g., IA 1 always = Target)

#### Proportion Calculation Type

#### i. Across All Samples

* % = IA sample count / total bin samples

#### ii. Across All On-Screen Samples

* % = IA sample count / (IA 0 + IA 1-4)

#### iii. Across Predefined IAs Only (excludes IA 0)

* % = IA sample count / (IA 1 + IA 2 + ...)

> Blink, off-screen, and excluded sample proportions are always calculated over the total bin samples.

#### Example Table (Based on 200 Samples)

| Types of Samples         | Sample Count | Across All Samples | Across All On-Screen Samples| Across All IAs Samples |
| ---------- | ----- | ----------- | --------- | -------------- |
| IA 1       | 10    | 5%          | 6.7%      | 10%            |
| IA 2       | 20    | 10%         | 13.4%     | 20%            |
| IA 3       | 30    | 15%         | 20%       | 30%            |
| IA 4       | 40    | 20%         | 26.7%     | 40%            |
| IA 0       | 50    | 25%         | 33.3%     | 25% (excluded) |
| Off-screen | 30    | 15%         | 15%       | 15%            |
| Blink      | 15    | 7.5%        | 7.5%      | 7.5%           |
| Excluded   | 5     | 2.5%        | 2.5%      | 2.5%           |

#### Data Selection Options

Choose what types of samples to include:

1. **All Samples**: Includes fixations, saccades, and blinks
2. **Fixation Only**: Excludes saccades and blinks
3. **Strict Fixation Bins**: Excludes entire bin if *any* sample is a saccade or blink

#### Collapsed Report Option

* Check to average across **all trials within each trial group**
* Grouping must be done beforehand


#### Saving the Report

1. Click **Next**
2. Choose output folder
3. Enter file name (append `.txt` if needed)
4. Click **Save**

> ⏳ May take time depending on `.edf` size


#### Report Output Types

####  Trial-Based Report

* Data for each time bin per trial

#### Collapsed Report

* Averages for each bin per trial group (e.g., per participant)

> Collapsed % values are computed from **summed raw counts**, not averages of trial percentages


####  Special Notes

* **Interest Period**: Bins start from the beginning of the currently selected period
* **Cyclopean Mode**:

  * Needed for `AVERAGE_*` variables with monocular or missing eye data
  * Prompted when report is created if applicable
* **Blink Handling**:

  * Samples in a blink saccade are excluded from `AVG_X`, `AVG_Y`, and pupil size


####  Summary Table

| Setting          | Description                            |
| ---------------- | -------------------------------------- |
| Bin Interval     | Length of each time bin (e.g., 20ms)   |
| Max Bins         | Max number of bins per trial           |
| IAs for Analysis | Specify which areas to analyze         |
| Proportion Type  | Choose how IA percentages are computed |
| Data Selection   | Include/exclude saccades and blinks    |
| Collapsed Report | Average across trials in group         |


####  Additional Tips

* Use collapsed report for smoother time-course curves
* Visualize results in R, Python, or Excel
* Make sure to match IA labels/IDs **exactly** (case-sensitive)
* Always define **Interest Periods** clearly to align binning

---


### Create a Time Course Line Graph from Data Viewer Output"

#### 🎯 Goal

Create a **publication-style line graph** showing how gaze fixations to different interest areas (IAs) change over time, using output from Data Viewer's **Time Course (Binning) Analysis**.

This guide includes:

* Conceptual overview
* Step-by-step instructions
* Matching R code
* Explanation of design choices


#### What You Need

A `.csv` file exported from the Time Course (Binning) Analysis Report in SR Research Data Viewer, which includes per-bin **fixation proportions** (e.g., `*_PROP` columns).


#### Step 1: Understand the Structure of the CSV File

Each row represents one **time bin** in one trial. Important columns:

* `BIN_INDEX`: the bin number (e.g., 0 to 100)
* `AVERAGE_IA_X_SAMPLE_COUNT_PROP`: proportion of samples in IA X during that bin (0 to 1 scale)
* IA labels: Target, Competitor(s), Distractor

Make sure the `PROP` values are proportions (0 to 1), not raw counts.


#### Step 2: Prepare the Data

In R:

```r
library(tidyverse)

# Load the data
raw_data <- read_csv("TimeCourseReport.csv")

# Select and rename relevant columns
plot_data <- raw_data %>%
  select(BIN_INDEX,
         Target = AVERAGE_IA_1_SAMPLE_COUNT_PROP,
         Phonological = AVERAGE_IA_2_SAMPLE_COUNT_PROP,
         Semantic = AVERAGE_IA_3_SAMPLE_COUNT_PROP,
         Distractor = AVERAGE_IA_4_SAMPLE_COUNT_PROP)

# Average across all trials per bin
timecourse <- plot_data %>%
  group_by(BIN_INDEX) %>%
  summarise(across(everything(), mean, na.rm = TRUE))
```

**Why average?**
Psycholinguistics line graphs typically present **mean fixation proportions per bin** across participants/trials to visualize trends over time.


#### Step 3: Plot the Line Graph

In R:

```r
ggplot(timecourse, aes(x = BIN_INDEX)) +
  geom_line(aes(y = Target * 100, color = "Target"), size = 1) +
  geom_line(aes(y = Phonological * 100, color = "Phonological"), size = 1) +
  geom_line(aes(y = Semantic * 100, color = "Semantic"), size = 1) +
  geom_line(aes(y = Distractor * 100, color = "Distractor"), size = 1) +
  scale_color_manual(values = c("Target" = "#1b9e77",
                                "Phonological" = "#d95f02",
                                "Semantic" = "#7570b3",
                                "Distractor" = "#666666")) +
  labs(title = "Time Course of Fixations by Interest Area",
       x = "Time Bin (e.g., 20ms per bin)",
       y = "Fixation Proportion (%)",
       color = "Interest Area") +
  theme_minimal(base_size = 14) +
  theme(legend.position = "top",
        panel.grid.major = element_line(color = "gray90"))
```

The line graph looks like this:  
![Time Course Plot](/images/time_course_fixation_plot.png)



Optional extensions:

* Add **error ribbons** using `geom_ribbon()` or bootstrapped CIs
* Re-align time bins to **critical word onset**
* Facet by condition if using multiple experimental groups


####  Summary

This line graph visualizes **how participants' attention shifts over time** in a spoken language or visual world task. It’s a staple analysis in psycholinguistics and is often used to support claims about processing dynamics, cue competition, and real-time comprehension.

Let me know if you'd like to add:

* Error bars (CI or SE)
* Multiple conditions
* Publication export (PDF, EPS)

---


💡 **Understanding `SAMPLE_COUNT` and `SAMPLE_COUNT_PROP` (`SAMPLE_COUNT_%`) in Time Course (Binning) Reports**
>
> **1. What `SAMPLE_COUNT` Means**  
> - `AVERAGE_IA_2_SAMPLE_COUNT` = the **average number of gaze samples** in each bin that fell into **Interest Area 2** (*Phonological Competitor*).  
> - Values are averaged across all trials contributing to that bin (collapsed report).  
> - The count depends on:
>   - **Sampling rate** (e.g., 1000 Hz = 1 sample per ms)
>   - **Bin size** (e.g., 20 ms/bin → ~20 samples possible)
>   - How long the participant looked at IA 2 during that bin.
>
> **2. What `SAMPLE_COUNT_PROP` Means**  
> - `AVERAGE_IA_2_SAMPLE_COUNT_PROP` = **proportion** of samples in the bin that were in IA 2:  
>  
>   $$ 
\text{PROP} = \frac{\text{AVERAGE\_IA\_2\_SAMPLE\_COUNT}}{\text{Total samples in bin (all IAs + off-screen + blinks)}}
>   $$
>
> **3. Example — BIN_INDEX = 20**  
> | IA | Count |  
> |----|-------|  
> | Target | 0 |  
> | Phon Competitor | 6 |  
> | Semantic Competitor | 0 |  
> | Distractor | 0 |  
> | Off Target | 4 |  
> **Total samples** = 10 → **PROP for IA 2** = 6/10 = 0.6 ✔
>
> **4. Example — BIN_INDEX = 21**  
> | IA | Count |  
> |----|-------|  
> | Target | 0 |  
> | Phon Competitor | 10 |  
> | Semantic Competitor | 0 |  
> | Distractor | 0 |  
> | Off Target | 0 |  
> **Total samples** = 10 → **PROP for IA 2** = 10/10 = 1.0 ✔
>
> **5. Why It Matters**  
> - **Counts** = raw absolute gaze allocation.  
> - **Proportions** = normalized values that allow comparison across trials/participants even when total sample counts differ (e.g., due to blinks).  
> - In psycholinguistics time-course plots, **proportions** are typically plotted for clearer interpretation.



---



💡 **How a Gaze Is Determined to Be on an Interest Area (IA)**
>
> **1. Defining Interest Areas**  
> - IAs are **rectangles**, **ellipses**, or **polygons** drawn in Data Viewer to mark regions of interest on the screen (e.g., Target, Competitor, Distractor).  
> - Each IA has an **ID** (number) and a **Label** (name).  
> - IAs can be **static** (fixed position) or **dynamic** (change position over time).
>
> **2. Sampling Eye Position**  
> - The eye tracker records gaze at a fixed **sampling rate** (e.g., 500 Hz, 1000 Hz).  
> - Each **sample** contains:
>   - Timestamp
>   - X, Y gaze coordinates
>   - Pupil size
>   - Eye event flags (fixation, saccade, blink)
>
> **3. Matching Gaze to IA Boundaries**  
> - For each sample:
>   1. **Check validity** (not a blink, not missing data).
>   2. Compare gaze coordinates to IA boundaries for that moment.
>   3. Assign the sample to:
>      - `IA_1`, `IA_2`, etc. if inside a defined IA.
>      - `IA_0` (NULL) if outside all IAs.
> - If **Cyclopean Mode** is enabled, binocular eye positions are averaged before checking boundaries.
>
> **4. Special Cases**  
> - **Blinks** → excluded (not assigned to any IA).  
> - **Off-screen gaze** → labeled as off-screen.  
> - **Dynamic IAs** → boundaries depend on the display time point.
>
> **5. Link to `SAMPLE_COUNT`**  
> - After classification, Data Viewer counts how many samples in each **bin** fall into each IA.  
> - These counts appear in columns such as `AVERAGE_IA_1_SAMPLE_COUNT`, `AVERAGE_IA_2_SAMPLE_COUNT`, etc.

---


💡 **Why “AVERAGE” Appears in Non-Collapsed Reports**
>
> In Data Viewer’s Time Course (Binning) reports, variables such as  
> `AVERAGE_IA_1_SAMPLE_COUNT`, `AVERAGE_IA_2_SAMPLE_COUNT`, etc.  
> always include the “AVERAGE” prefix — even if the report is **not** collapsed.
>
> - **In collapsed reports** (e.g., aggregated by participant or condition),  
>   “AVERAGE” means the value is the *mean number of samples per bin* for that IA  
>   averaged across all trials contributing to that bin.
> - **In non-collapsed reports** (like the one in this dataset), each row represents  
>   one specific trial and bin. The “AVERAGE” value is therefore based on a  
>   single trial’s data — which means it is numerically the same as the **raw sample count** for that IA and bin.
>
> Data Viewer uses the “AVERAGE” prefix in both cases for **naming consistency**  
> across collapsed and non-collapsed outputs.
>
> **Example:**
>
> | Report Type | Trial(s) Included in Bin | IA 2 Sample Counts | `AVERAGE_IA_2_SAMPLE_COUNT` |
> |-------------|--------------------------|--------------------|-----------------------------|
> | Non-collapsed | Trial 5 only            | 6                  | 6.0                         |
> | Collapsed (by participant) | Trial 5, Trial 7, Trial 9 | 6, 8, 4            | (6 + 8 + 4) / 3 = 6.0       |


