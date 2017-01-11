# Tracking Areas Searched While Accounting for Ocean Currents
## Abstract
This paper is a project proposal, proposing a stand-alone desktop application that creates a U|g|CS mission file that can be used to search the area a person who has fallen overboard is likely to be after accounting for ocean currents, given the time of the incident and the number of drones available to search. The application will use Google location history data for location information and NASA OSCAR data for ocean current information. 

## Introduction
### Problem Statement

**Problem**
It is difficult to track where a person that has fallen overboard in the ocean might be.

**Barriers**
The exact time the person fell is often unknown, and ocean currents move the person from their original location to unknown places.

**Solution**
Create a program that can figure out a person's likely location given the time range of when they fell overboard, using the ship's location history and ocean current data gathered from NASA's OSCAR program (**O**cean **S**urface **C**urrent **A**nalyses **R** ealtime) and can create a mission file that can be uploaded to Universal Ground Control Software to guide Seach and Rescue drones to the location.

## Motivation
### Frequency of MOB Situations and MOB Incident Fatality Rate
Every year, about 20 people fall overboard while on a cruise. When a person falls overboard on a cruise ship, their chance of survival is about 20% [reference].

![](Images\MobIncidents.PNG)

![](Images\MobSurvivalRate.PNG)

One reason for the low survival rate is the difficulty of finding a person who has fallen overboard because of several factors:
1. Even if a person is immediately noticed falling overboard, it can take more than a mile for the ship to turn around.[reference] At that distance it is very easy to lose sight of the person at that distance [reference]
* Once a person has been lost sight of, they are rarely found because a cruise ship has no rescue aircraft, they use lifeboats to search for the missing person, which have a limited range of vision in a vast ocean.

## Background

### Existing Work
The end goal is for their to be an efficient way to use drones for man overboard search and rescue operations on cruise ships. With that goal in mind there are several existing stand-alone products that provide much of the functionality necessary to make that goal a reality. These products are:
* Universal Ground Control Software U|g|CS
* Dedicated SAR drones


#### Universal Ground Control Software
Talk about U|g|CS here.

Universal Ground Control Software is a tool that allows you to control multiple drones. It has many features which can be found here [source]. Key features that will be useful for our end goals, include:
1. The ability to remotely control multiple drones.
* Drones can be set to fly predefined missions, or can be manually controlled via joystick.
* Ability to view video feeds from drones.
* Ability to map the ground area a camera is looking at.
* Ability to export and import missions for drones.


#### Dedicated SAR Drones
Talk about DJI Matrice 1000 SAR Kit here.

DJI and FLIR have collaborated to create a camera and drone setup that is ideal for SAR operations. Some key features which make it an ideal platform for SAR are:

1. 3 mile range.
* GPS tracking.
* The ability to send back a live camera feed, which U|g|CS can record for later playback.
* The ability to pick from multiple infrared color schemes to find one that works best for the situation.
* Ability to control the camera remotely.


In addition, this project will incorporate these services in order to meet it's goals:
* Google location history
* NASA ocean current data

#### Google Location History
Talk about how I will integrate google location services into the project.

If you allow Google to track your location and store your location history, you can retrieve your location history through an API [reference]. The process for doing so would be.

1. Google can track your phones location if you allow it to.
* You can download your location history using an API.
* The data can be in KML (a form of xml) or JSON format.
* Either way, the data can be easily parsed, in JSON the data is a collection of objects with timestamp, location, mode(walking, biking, riding) information.
* The data will be parsed based on the time range of the Man Overboard incident.

#### NASA Ocean Current Data
NASA tracks ocean currents on a macro scale through the use of satellites. New data comes in every 5 days and can be downloaded from an ftp server. Several visualization programs have been made.
![](Images\OscarVisualization.png)



## Proposed Project
### Description of the proposed solution/approach
The solution is to make a stand alone program that takes a time range and number of drones available as input from the user, and outputs a mission file that can be uploaded to U|g|CS and used to control multiple drones.

The program will take into account the following factors:
* A variable number of drones taking part in the SAR operation.
* The distance a person might have swum. In other words the search area gets larger over time since the person may not have stayed stationary.

The program will **not** take in to account the following factors:
* Wind affecting the flight of drones (Beyond the scope of Senior Project).
* Multiple trips required, and tracking areas searched on the previous trip. (This is important, and necessary for a working solution, however I feel it is beyond the scope of Senior Project)
* Travel time of the drones. (also important for a final solution but too much work.)
* Location and time of SAR operation start. (The program will assume current location and time as starting point and time for drones, mostly because it won't take long to create a mission file.)

Additional limitations/assumptions
* OSCAR data's spatial resolution is 1/3 of a degree of latitude which is about 23 miles.
* Good internet speed. (Currently cruise ships only have satellite internet, which is relatively slow and expensive.)
* Person may swim up to 6 MPH (Michael Phelps top speed in water).

A mockup of the screen is shown below
![mockup](Images/GuiMockUp.png)

### Delineation of major tasks/milestones
The major tasks and milestones for the project are as follows:
* Connect with Google Location History API to download location history for any given time range.
* Parse JSON received from google into data that can be used to create a search grid.
* Connect with OSCAR servers to automatically download ocean current data.
* Parse OSCAR files into data that can be used in our calculations.
* Create algorithms that will calculate out where a person is likely to be based on current time, time of MOB incident, and ocean current data.
* Reverse engineer U|g|CS mission file export format to be able to create our own based on the area to search and the number of drones available.

### List of required software/hardware for project and evaluation
To complete the project and it's evaluation the hardware and software that is required is:

* U|g|CS Open: Free.
* Parrot drone: CS Dept. has one already.

### Description of proposed timeline (Hours per major task)
The major tasks are expected to take this long:

### Team member organization, task delineation, and/or expected skill sets
This project will require a 3 person team, with all CS majors, with skill in data structures and algorithms
and data analysis.

Here is a break down of each team members responsibilities:
**Person 1**
* Work with Google Location History data, from automatically getting location history data to transforming that data into data that can be used to create a starting search grid
* Help with testing.

**Person 2**
* Work with OSCAR data from automatically downloading it and using it to transform starting search grid into current search grid
* Help with testing.

**Person 3**
* Reverse engineer U|g|CS mission file export format.
* Be able to convert the search grid to a mission file to control multiple drones.
* Create GUI/front end of the program.
* Help with testing.

A diagram of each persons responsibilities and their role in creating the overall project.  
Different colors signify different persons.
![](Images/ProgramDiagram.png)

## Testing and Evaluation
### List of target results/outcomes based on project reqs
1. The program must be able to download relevant google location history automatically.
* The program must be able to download OSCAR data automatically.
* The program must be able to write a valid U|g|CS mission file.
* The program will output a correct mission file within 10 seconds of necessary data being downloaded.


### Description of the specific measure, target value, and testing plan that will be used to assess attainment for each target result

1. **The program must be able to download relevant google location history automatically:** Pass/fail.
* **The program must be able to download OSCAR data automatically:** Pass/fail.
* **The program must be able to write a valid U|g|CS mission file:** Have the parrot drone fly a route created by the program.
* **The program will output a correct mission file within 10 seconds of necessary data being downloaded:** Pass/fail.

### Description of the method of evaluation the success of the project.
In order to consider the project a success, all target outcomes must be met.

## Conclusion
Restatement of problem statement, project goals, and summary of proposed solution and expected outcomes/deliverables

To recap, this project aims to help solve the problem of figuring out where ocean currents have taken someone who has fallen overboard on a cruise ship and directing SAR to their location. The deliverables for the project include a stand-alone desktop application that takes the time range of the MOB incident and the number of drones available to search and outputs a mission file that can be used by U|g|CS to guide drones to the search area.

## References
1.  [Cruise Ship MOB Stats](http://www.cruisejunkie.com/Overboard.html)
* [Cruise Vessel Safety and Security Act 2010](https://www.uscg.mil/hq/cg2/cgis/Docs/HR3360CruiseVesselSecurityandSafetyActof2010.pdf)
* [Cruise MOB fatality statistics](http://www.cruiseserver.net/travelpage/other/man_overboard.asp)
* [UGCS Information](https://www.ugcs.com/en)
* [OSCAR Ocean Surface Current Analysis Realtime](http://podaac.jpl.nasa.gov/dataset/OSCAR_L4_OC_third-deg)
* [More OSCAR Info](http://www.esr.org/oscar_index.html)
* [Ocean Current Visualization](https://earth.nullschool.net/)
* [USCS SAROPS](https://www.uscg.mil/acquisITION/international/sarops.asp)    
* [Extracting location information from Google](https://shkspr.mobi/blog/2015/09/get-your-google-location-history-the-hard-way-again/)
* [OSCAR guide](ftp://podaac-ftp.jpl.nasa.gov/allData/oscar/preview/L4/oscar_third_deg/docs/oscarthirdguide.pdf)
