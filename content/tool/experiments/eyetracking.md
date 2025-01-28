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

