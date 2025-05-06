---
title: "Eyetracking"
date: 2023-06-17
draft: false

---

### Learning About Eye-Tracking Technique: creation, design, data analysis
---
Learning about the **eye-tracking technique** is motivated by my interest in discovering cognitive processes involved in interpreting scalar quantifiers in social contexts.

My first experiments (hopefully) are about **perspective-taking** and **interpreting scalars in social contexts**, a project emerging from my discussions with Prof. Gerry Altmann.

In this post, I share my experience in learning about this technique in five areas:
- Reviews
- Classical studies
- tools to create VWP experiments
- Experimental design
- Data analysis

---

#### Part I: Reviews   

video tutorials:

Zhan L. Using Eye Movements Recorded in the Visual World Paradigm to Explore the Online Processing of Spoken Language. J Vis Exp. 2018 Oct 13;(140):58086. doi: 10.3791/58086. PMID: 30371678; PMCID: PMC6235534.
[link to video](https://app.jove.com/v/58086/using-eye-movements-recorded-visual-world-paradigm-to-explore-online)



Tutorials

1. Introduction to Eye Tracking: A Hands-On Tutorial for Students and Practitioners [Link](https://arxiv.org/html/2404.15435v1#S1)


#### Part II: Classical Studies

The following is a list of classical VWP studies:  






#### Part III: tools to create VWP experiments

  ##### Lab-Based Eye-Tracking 
   SR EyeLink   
   [Experiment Builder Tutorial videos](https://www.youtube.com/watch?v=qCMgHiGbWN4)


 
  ##### Opensource tools
  jsPsych, pychoPy, OpenSesame  
  
   4. **jsPsych Tutorial**  
   - [jsPsych Official Tutorial](https://www.jspsych.org/7.0/tutorials/hello-world/)  
   - Online Book by Winson Yang: [jsPsychTutorial](https://winsonfzyang.github.io/jsPsychTutorial/)  
   - [YouTube Tutorial Playlist](https://www.youtube.com/playlist?list=PLtdKTIOUlb42qG962wz30fzlUMibJCGQW)  

   5. **PyGaze (Eye Tracking) on OpenSesame**  
   - [PyGaze in OpenSesame Documentation](https://osdoc.cogsci.nl/3.3/manual/eyetracking/pygaze/)  
   - [PyGaze Documentation](http://www.pygaze.org/docs/)  

  6. **Eyetracking Data Analyses in R**  
   - [eyetrackingR Package](http://www.eyetracking-r.com/)  
   - Tutorial by Marissa Barlaz: [Portfolio Example](https://marissabarlaz.github.io/portfolio/eyetracking/)  
   - [YouTube Tutorial](https://www.youtube.com/watch?v=CkoJvnWEOxw)  


 ##### Online Webcam-Based Eye-Tracking  
  Here are some of the resources I use to learn about designing online eye-tracking experiments:

   1. **WebGazer**  
   - [WebGazer Official Site](https://webgazer.cs.brown.edu)  
   - [WebGazer on GitHub](https://github.com/brownhci/WebGazer)  
   - Tutorial by BROWNHCI: [WebGazer Tutorial](https://github.com/brownhci/WebGazer/wiki/Tutorial)  

   2. **WebGazer Tutorial on jsPsych**  
   - Tutorial by Xiaozhi Zhao: [GitHub Repository](https://github.com/xiaozhi2/webgazertutorial)  

   3. **WebGazer on OpenSesame**  
   - [WebGazer in OpenSesame Documentation](https://osdoc.cogsci.nl/3.3/manual/eyetracking/webgazer/)  


#### Part IV Experimental Design

There are several ways to build an eye-tracking experiment.  
1. **Experiment Builder**: Provided with the EyeLink machine.  
2. **Open-source tools**: Tools like **OpenSesame** and **PsychoPy**.

##### OpenSesame  
OpenSesame (Mathôt et al., 2012), used together with the [PyGaze](http://www.pygaze.org) plugin (Dalmaijer et al., 2014).  

##### Resources for using PyGaze on OpenSesame:
1. [OpenSesame and PyGaze Workshop in Potsdam](https://www.pygaze.org/2018/07/opensesame-and-pygaze-workshop-potsdam/)  
2. [PyGaze (Eye Tracking) - OpenSesame Documentation](https://osdoc.cogsci.nl/3.2/manual/eyetracking/pygaze/)  
3. [Visual World Experiment with PyGaze and OpenSesame](https://osdoc.cogsci.nl/3.3/tutorials/visual-world/)

##### PsychoPy  
[PsychoPy](https://psychopy.org/index.html) is another open-source tool that supports creating eye-tracking experiments. These experiments are compatible with EyeLink systems.

##### Resources for PsychoPy:
1. [Communicating with an Eye Tracker](https://psychopy.org/hardware/eyeTracking.html)  
2. [YouTube Tutorial: PsychoPy Integration for EyeLink Eye Trackers](https://www.youtube.com/watch?v=1tLJHVktrEk)

##### Gorilla  
[Gorilla](https://app.gorilla.sc/login) is also an option for creating eye-tracking experiments.

##### Resources for Gorilla:
1. [Eye Tracking in Task Builder 1](https://support.gorilla.sc/support/tools/legacy-tools/task-builder-1/eye-tracking#overview)  
2. [Eye Tracking in Task Builder 2](https://support.gorilla.sc/support/tools/task-builder-2/eye-tracking#overview)

**Note**: While Gorilla is a great tool, I chose not to use it because there is a fee for recruiting participants.

---

###### My Path
1. Since I am proficient with **OpenSesame** (I’ve used it for creating SPR tasks and mouse-tracking tasks), I designed a **Visual World (VW) task** using **PyGaze on OpenSesame**.

---


#### Part V: Data Analysis

1. Ito, A., Knoeferle, P. Analysing data from the psycholinguistic visual-world paradigm: Comparison of different analysis methods. Behav Res 55, 3461–3493 (2023). https://doi.org/10.3758/s13428-022-01969-3 [Link to file](https://link.springer.com/article/10.3758/s13428-022-01969-3)
 
two datasets are from the following two studies and are available at this [OSF repository](https://osf.io/tzn8u/)   
[Ito et al. (2018b)](https://www.sciencedirect.com/science/article/pii/S0749596X17300633?via%3Dihub); [Knoeferle and Crocker (2006; Experiment 1)](https://onlinelibrary.wiley.com/doi/10.1207/s15516709cog0000_65):

Step 1 Data preparation
how to treat (very short and very long) fixations and blinks

tools:  
SR Research Data Viewer;   
R packages: gazeR (Geller et al., 2020), eyetrackingR (Dink & Ferguson, 2015), VWPre (Porretta et al., 2020)  

SR Research Data Viewer [tutorial videos](https://www.youtube.com/watch?v=pM_dxz-G_ic)  
preprocessind data [Data Viewer Video Tutorial: 07 - Filtering Cleaning and Adjusting Data](https://www.youtube.com/watch?v=DpOeGKF9YeY)




1. The data analysis focuses on experiments designed with **PyGaze**.   


---

##### References
- Dalmaijer, E., Mathôt, S., & Van der Stigchel, S. (2014). PyGaze: An open-source, cross-platform toolbox for minimal-effort programming of eye-tracking experiments. *Behavior Research Methods*. [DOI](https://doi.org/10.3758/s13428-013-0422-2)  
- Mathôt, S., Schreij, D., & Theeuwes, J. (2012). OpenSesame: An open-source, graphical experiment builder for the social sciences. *Behavior Research Methods, 44*(2), 314–324. [DOI](https://doi.org/10.3758/s13428-011-0168-7)  
- Peirce, J. W., Gray, J. R., Simpson, S., MacAskill, M. R., Höchenberger, R., Sogo, H., Kastman, E., Lindeløv, J. (2019). PsychoPy2: Experiments in behavior made easy. *Behavior Research Methods*. [DOI](https://doi.org/10.3758/s13428-018-01193-y)  

---


#### Part VI How I Create an Eyetracking experiment from beginning
[EB user manual 2024 version](EBUserManual2024.pdf)

The following tutorial are generated based on this user manual.

can you format the following content by using hugo markdown syntax?

### Creating EyeLink Experiments: A Beginner's Tutorial

In this tutorial, we'll guide you through creating a simple EyeLink experiment using SR Research Experiment Builder. This experiment will display a single word in the center of the screen in each trial, similar to the "SIMPLE" template of the EyeLink C Programming API.

### 1. Prerequisites
Before you start, make sure you have the SR Research Experiment Builder software installed. The examples in this tutorial assume a screen resolution of 1920 x 1080 at 100% display scale.

### 2. Creating the Experiment
### 2.1 Creating a New Experiment Project
1. **Open Experiment Builder**:
    - On Windows, click Start > All Applications > SR Research and choose “Experiment Builder”.
    - On macOS, go to the “Applications/Experiment Builder/” folder and open the “ExperimentBuilder” application.
2. **Create a new project**:
    - Click “File > New” on the application menu bar.
    - In the “New Project” dialog box:
        - Enter “Simple” in the “Project Name” edit box.
        - Click the button on the right end of the “Project Location” to browse to the directory where you want to save the experiment project. Make sure the directory exists if you enter it manually.
        - Leave the “Templates” field as “None”.
        - Check the “EyeLink Experiment” box.
        - Select the eye tracker version from the dropdown menu (e.g., EyeLink 1000 Plus) or select “Current” to allow any EyeLink eye tracker.

### 2.2 Configuring Experiment Preference Settings
1. **Access preferences**:
    - On Windows, select “Edit > Preferences” or press “F4”.
    - On macOS, click “ExperimentBuilder > Preferences” or press Command ⌘+“,”.
2. **Check display settings**:
    - Click “Preferences > Experiment > Devices > Display”. Ensure the settings (Width, Height, Bits per Pixel, and Refresh Rate) are supported by your video card and monitor. The default values 1920 × 1080 × 32 × 60 Hz are used in this example.
3. **Configure screen settings**:
    - Click “Preferences > Screen”. Set the Location Type as "Center Position" and check the "Antialis Drawing" box.
4. **Set tracker version**:
    - Ensure the "Tracker Version" setting in the "Preferences -> Experiment -> Devices -> EyeLink" preferences is set correctly for your eye tracker. If you use EyeLink 1000, 1000 Plus, or Portable Duo, configure the correct “Camera Mount” and “Mouse Usage setting.
5. **Set file encoding**:
    - If you plan to use non - ASCII characters, check the “Encode Files as UTF - 8” box in the Build/Deploy node.

### 2.3 The Topmost Experiment Layer
1. **Add nodes to the workspace**:
    - Open the “Action” Tab of the component toolbox and drag a “Display Screen” action into the work area.
    - Open the “Trigger” Tab and drag a “Keyboard” trigger, an “EyeLink Button” trigger, and a “Timer” trigger into the work space.
    - Set the Timer trigger duration to 120000 msec.
    - Open the “Action” Tab again and add a “Camera Setup” action and a “Sequence” node to the work space.
2. **Connect the nodes**:
    - Draw connections from the START node to the DISPLAY_SCREEN node.
    - Connect the DISPLAY_SCREEN action to the KEYBOARD, EL_BUTTON, and TIMER triggers.
    - Connect each of the three triggers to the EL_CAMERA_SETUP node, then from EL_CAMERA_SETUP to the SEQUENCE node.
    - Right - click any blank area in the work window and select "Arrange Layout" to organize the nodes.

### 2.4 Creating the Instructions Screen
1. **Open the Screen Builder**:
    - Double - click the DISPLAY_SCREEN node in the workspace.
2. **Add a multi - line text resource**:
    - Click the multiline text resource button on the screen builder toolbar and click anywhere on the screen to add the resource.
3. **Edit the text**:
    - Set the text margins to 100 in all fields.
    - Enter the instruction text, such as instructions for camera setup, calibration, and starting recordings.
    - Select all text (Ctrl + A on Windows or Command ⌘ + A on macOS) and set the text appearance (font name, size, style, alignment, line spacing, and color).
    - Click the “Close” button to finish.

### 2.5 Editing the Trial Sequence: Data Source
1. **Select the trial sequence node**:
    - Select the last “SEQUENCE” node in the structure list and enter a new value for the Label, e.g., “TRIAL”.
2. **Create the data source**:
    - Click the value cell of the “Data Source” property to bring up the Data Source Editor.
    - Click "Add Column" to create two columns: “trial” of type "Number" and “word” of type "String".
    - Click “Add Row” and set the “Number of Rows” to 12.
    - Enter values for the “trial” column (1 - 12) and the “word” column (e.g., “One”, “Two”, …, “Twelve”).

### 2.6 Editing the Trial Sequence: Preparing Sequence and Drift Correction
1. **Add actions to the trial sequence**:
    - Open the “Action” Tab and drag a “Prepare Sequence” action, a "Drift Correction" action, and a “Sequence” node into the workspace.
2. **Connect the actions**:
    - Draw connections from the “START” node to “PREPARE_SEQUENCE”, from “PREPARE_SEQUENCE” to “DRIFT_CORRECTION”, and from “DRIFT_CORRECT” to the “SEQUENCE” node.
    - Right - click any blank area in the work window and select "Arrange Layout".

### 2.7 Editing the Recording Sequence
1. **Set sequence properties**:
    - Select the newly added “Sequence” node, enter a new label like “RECORDING”, and check the “Record” and “Is Real Time” checkboxes.
2. **Add actions and triggers**:
    - Drag a “Display Screen” action, a “Timer” trigger, an “EyeLink Button” trigger, and a second “Display Screen” action (rename it as “DISPLAY_BLANK”) into the workspace.
    - Set the Timer trigger duration to 10000 msec and its “Message” to “Time out”.
    - Uncheck the “Send EyeLink DV Messages” box for the “DISPLAY_BLANK” action.
3. **Connect the nodes**:
    - Draw connections from the “START” node to “DISPLAY_SCREEN”, from “DISPLAY_SCREEN” to both “TIMER” and “EL_BUTTON”, and from both “TIMER” and “EL_BUTTON” to “DISPLAY_BLANK”.
    - Right - click and select “Arrange Layout”.

### 2.8 Modifying the Properties of a Display Screen
1. **Set message for the first display screen**:
    - Select the first DISPLAY_SCREEN node. In the properties window, double - click the value field of the “Message” property and enter a message like “SYNCTIME” to mark the screen presentation. Check the “Send EyeLink DV Messages” and “Use for Host Display” properties.
2. **Set message for the blank display screen**:
    - Select the “DISPLAY_BLANK” action. Double - click the value field of the “Message” property, enter a message like “blank_screen”, and uncheck the “Send EyeLink DV Messages” and “Use for Host Display” checkboxes.

### 2.9 Creating the Display Screen
1. **Add a text resource**:
    - Double - click the “DISPLAY_SCREEN” object in the work space to open the Screen Builder. Click the “Insert Text Resource” button and click on the screen to add the resource.
2. **Modify text properties**:
    - Double - click the Font Name property to select the desired font (e.g., Arial).
    - Double - click the Font Size property and enter the desired size (e.g., 40).
    - Set the text to load from the data source by clicking the “Text” property value field and using the Attribute Editor to select the “word” attribute from the data source.
    - Check the “Use Runtime Word Segment” box.
    - Align the text in the center of the screen and lock the selection.

### 2.10 Writing Trial Condition Variables to EDF file
1. **Access variable configuration**:
    - Click the Experiment node in the structure list.
    - In the properties table, click the value field of the “EyeLink DV Variables” property.
2. **Select variables to write**:
    - In the dialog box, make sure both the “Trial” and “Word” columns are included in the “Selected Variables” list. Click “OK” to finish.

### 2.11 Showing Experiment Progress Message on Tracker Screen
1. **Set the status message**:
    - Select the “RECORDING” sequence node in the structure list.
    - In the properties panel, click the value field of the “EyeLink Record Status Message” property and use the Attribute Editor to enter an equation like "Trial " + str(@parent.iteration@) + "/ " + str(@parent.iterationCount@) + " " + str(@TRIAL_DataSource.word@) to display the trial number and the word on the tracker screen.

### 3. Building the Experiment
1. **Save the project**:
    - Click the Save button on the application tool bar if you haven't saved your experiment project yet.
2. **Build the experiment**:
    - Click “Experiment > Build”. Check the “Output” tab in the Graph Editor Window for error and warning messages. If there are issues, double - click the messages to highlight the problem nodes or screen resources.
3. **Test run the experiment**:
    - After a successful build, click “Experiment > Test Run” to test the experiment. Note that “Test Run” is for testing and debugging only, not for data collection.

### 4. Deploying the Experiment
1. **Deploy the experiment**:
    - Click “Experiment > Deploy” to create an executable version of the experiment in a new folder. If a data source is used, a “datasets” subdirectory with a copy of the data set file will be created.

## 5. Running the Experiment
1. **Prepare to run**:
    - Make sure the EyeLink host software is running and the network connection between the host and display computers is established.
2. **Start the experiment**:
    - Go to the directory where the experiment was deployed and click “simple.exe” to start. Enter an EDF file name (no more than 8 characters, with only letters, numbers, and underscores) when prompted.
3. **Conduct the experiment**:
    - Follow the on - screen instructions for camera setup, calibration, validation, and pre - trial drift correction. After running all the trials, an EDF file will be transferred to the display computer. Be patient during the file transfer.

## 6. Common Errors and Solutions
### 6.1 Error in Initializing Graphics
If you see an “Could not initialize display to ***” error, check if the display settings (screen resolution, color bits, and refresh rate) are supported by your video card and monitor. Update the settings in “Preferences > Experiment > Devices > DISPLAY” if needed. Also, make sure your graphics card driver is up - to - date.

### 6.2 Invalid Tracker Type
If the eye tracker specified in the preferences doesn't match the one being used, Experiment Builder will show an error message. Set the correct tracker version in the “Preferences > Experiment > Devices > EYELINK” section.



create images for eyetracking experiments
organize the order of target and competitor (and/or distractor) in the image to display so that they are evenly distributed to the possible positions (e.g., top corner, left corner, right corner)(counterbalance the position effect)

create each image of target/competitor/distractor
use Microsoft Powerpoint to create image displays to be used in the experiment
export the slides into .png files (specify the size as 800*600)




Questions:
when to add "results" components?
When to add "variable" nodes? 
visual stimuli?
audio stimuli?
other response measures when recording eye movements?
longer passages to display?


dongle 
needed when: working on script, data viewer (analysis of data), deployment
not needed: after deployed and collect data


in the following I present the nuts and bolts in creating a visual world experiment using Eyelink 1000 plus.

The sample experiment has the following levels:
(--> means "connects to")

Level 1: Welcome and Introduction

START --> DisplayScreen action (lable: DISPLAY_EYE_TRACKING_EXPLANATION) (Welcome message & experiment introduction) --> Keyboard action & EyelinkButton action --> DisplayScreen action (label: CALI_INSTRUCTIONS) (explain calibration procedure) --> Keyboard trigger AND EyelinkButton trigger (offering two ways out) --> Sequence action (label: BLOCK)

Level 2: BLOCK sequence (iteration = 8)
START --> EyeLinkCameraSetup action (label: EL_CAMERA_SETUP_EXP) --> NullAction action (label: Null_Action) --> Conditional trigger (label: DETERMINE_PRAC_OR_EXP) (there are two connections further down)

connection #1: if iteration in the Conditional trigger equals 1, then it connects to a DisplayScreen (label: PRAC_INSTR) (practice instructions) --> Keyboard trigger (label: KEYBOARD_START) AND EyeLinkButton trigger (label: EL_BUTTON_START) --> TRIAL sequence

connection #2: if iteration in the Conditional trigger NOT equals 1, then it connects to another Conditional trigger (label: CONDITIONAL), there are two connections further down

connection #2.1: if iteration in CONDITIONAL equals 2, it connects to DisplayScreen action (label: EXP_INSTR) (experiment instruction) --> Keyboard trigger (label: KEYBOARD_START) AND EyeLinkButton trigger (label: EL_BUTTON_START) --> TRIAL sequence


connetion #2.2: if iteration in CONDITIONAL NOT equals 2, it connects to a DisplayScreen action (label: BREAK) (take a break) --> timer trigger (label: BREAK_TIMER) --> TRIAL sequence


Level 3: TRIAL sequence (iteration = 356; split by = [5, 12, 12, 12, 12, 12, 12, 12]; Data source: column = 9, row = 356)
START --> PrepareSquence action (label: PREPARE_SEQUENCE) --> DriftCorrection action (label: DRIFT_CORRECT) --> RECORDING sequency

Level 4: RECORDING sequence
(Record = check; Recording Pause Time = 20; Eyelink Record Status Message = = str(@self.iteration@) + "/89"; Trial Result = 0; Is Real Time = check; iteration Count = 1; Data Source = not specified;)
START --> DisplayScreen action (label: PIC_ONSET)



#### .ias files

Generate images
Experimental setting:
Here is an example stimuli:

> Tom is a school teacher who values kindness and empathy in his communication with students. Today, Tom is going to announce test results to two students, Mary and John. Mary failed each of the six tests, while John failed four tests but managed to pass two.
> Tom approached one of them and said, “**You** failed **some of** **the tests**.” After hearing this, **Mary** found out she had failed all six tests.


1. In each trial, I present a pre-generated image (via PowerPoint) together with an audio input. 
2. On each slide, there are three separate pictures. Each slide is converted into an image.
3. Set slide size in PowerPoint to match 16:9 (e.g., 33 cm × 18.5 cm)(The resolution of the screen of the display computer is 1920 * 1080; it is close to 16:9)
4. Each image consists of three separate pictures, which are organized in a triangle shape. Thus, one picture in a top-center position, one in the left-bottom position, and the last one in the right-bottom position. 
5. The PPT-generated images are ABOUT 1280** * 720 in size. (The actual width and height of PowerPoint-generated images are 1280 * 718; or you can set them as 1284 * 720) (The resolution of the screen of the display computer is 1920 * 1080; it is close to 16:9) The images will be centered both horizontally and vertically. 
6. why not 1920 * 1080 but 1280 * 720? This gives a nice large visible area, while leaving small margins on all sides. Exporting a 1920×1080 image would stretch everything, misaligning your interest area calculations unless you rescale manually.
7. Measurements of the three pictures in each image are as follows:
   Top-center picture: width 6 cm; height 6 cm; X (from top) 13.5 cm; Y (from top) 0.5 cm
   (X = 13.5 (i.e., distance from the top-left corner to the left side of the slide): full size of a slide is 33 cm; thus, half a slide is 16.5cm; size of the picture is 6 cm; thus, half a picture is 3 cm; thus the X of the top-center corner of the picture is 16.5-3 = 13.5)
   (Y = 0.5 (i.e., distance from the top-left corner to the top side of the slide))

   Left-bottom picture: width 6 cm; height 6 cm; X (from left) 4 cm; Y (from top) 12 cm
   (X = 4 (i.e., distance from top-left corner to the left side of the slide))
   (12 (i.e., distance from top-left corner to the top side of the slide) = 18.5 - 0.5 (margin from bottom; same as the margin from the top) - 6 (size of the full picture))
   
   Right-bottom picture: width 6 cm; height 6 cm; X (from left) 23 cm; Y (from top) 12 cm
   (23 (i.e., distance from top-left corner to the left side of the slide) = 33 - 4 (margin from right; same as the margin from the left) - 6 (size fo the full picture))
    (12 (i.e., distance from top-left corner to the top side of the slide) = 18.5 - 0.5(margin from bottom; same as the margin from the top) - 6 (size of the full picture))

8. The actual width and height of PowerPoint-generated images are 1280 * 718. 


9. Use Gpt to create .ias files

PROMPT
As the roles of the pictures are counter-balanced across images, I will set up the ias metrics for each image separately. The first thing to do is to set up ias metrics for three pictures in terms of the position, namely, top, left, right. 

Measurements of the three pictures in each image are as follows:
Each slide is 33 cm * 18.5 cm
Each image is generated vis PowerPoint with the Width of 1280 and Height of 718. 

Top picture: width 6.5 cm; height 6.5 cm; X (from top) 13.25 cm; Y (from top) 2 cm
Left picture: width 6.5 cm; height 6.5 cm; X (from left) 5 cm; Y (from top) 10 cm
Right-bottom picture: width 6.5 cm; height 6.5 cm; X (from left) 21.5 cm; Y (from top) 10 cm

Please generate an ias file for three pictures in the image that could work in Experimental Builder?


Resulting .ias file as a text file
# Label       X    Y    Width   Height
Top          514  78   252     252
Left         194  388  252     252
Right        834  388  252     252

Save the file as plain text file with .ias as the extension

10. Use the template ias file and rename the "Top", "Left" and "Right" as the roles of the three pictures based on "Target", "Competitor", and "Distractor". The following is an example (C1.ias)
# Label       X    Y    Width   Height
Competitor          514  78   252     252
Target         194  388  252     252
Distractor        834  388  252     252

12. what can ias files help in terms of data analysis?
    
   🎯 Interest Areas Define What You Care About in the Visual Scene
      In an eye-tracking experiment:
      The eye-tracker records raw gaze data — basically, X, Y coordinates at every time point.
      But by itself, a raw (X, Y) point doesn't tell you much:
      "Was the participant looking at the important object? Or just some background?"
      
      ✅ Interest Areas (IAs) are regions you define ahead of time (boxes or other shapes), where:
      You tell the system:
      👉 "If the participant's gaze falls inside this region, log it specially."
      Thus: You know exactly when and for how long the participant looked at something you care about.
      ✅ IAs turn meaningless gaze dots into interpretable, analyzable data.
   
   
   🧩 IAs Connect Eye Movements to Experimental Meaning
      In your case:
      You have three pictures (Target, Competitor, Distractor) on the screen.
      
      With IAs:
      Every fixation is automatically labeled by which picture it fell into (Target, Competitor, Distractor).
      This allows you to analyze participants’ behavior relative to your experimental conditions.


   ⏳ IAs Make Time-Based Analysis Possible
      In time-sensitive designs (like yours, with audio unfolding):

You want to know when participants look at the Target, not just whether they eventually looked.

With IAs:

You can measure how quickly participants shift their gaze toward the Target after hearing "you" or "some."

You can compute fixation probability over time, aligned with key moments in the stimulus.


   📈 IAs Enable Clean and Efficient Data Analysis
      Because EyeLink automatically logs:
      Fixation durations per IA
      First fixation landing site
      Total gaze time per IA
      Probability of fixating each IA over time
      
      ✅ Your analysis later (in R, Python, or SPSS) can directly use these logs:
      "Compare mean dwell time on Target between Polite and Direct conditions."
      "Calculate gaze bias toward Target during critical audio windows."



13. 



