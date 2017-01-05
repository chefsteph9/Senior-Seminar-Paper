# Tracking Areas Searched While Accounting for Ocean Currents
## Abstract
Abstract gets filled in last.

## Introduction
### Problem Statement

**Problem**
It is difficult to track where a person that has fallen overboard in the ocean might be.

**Barriers**
The exact time the person fell is often unknown, and ocean currents move the person from their original location to unknown places.

**Solution**
Create a program that can figure out a person's likely location given the time range of when they fell overboard, using the ship's location history and ocean current data gathered from NASA's OSCAR program (**O**cean **S**urface **C**urrent **A**nalyses **R** ealtime) and can create a route file that can be uploaded to Universal Ground Control Software to guide Seach and Rescue drones to the location.

## Motivation
### Frequency of MOB Situations and MOB Incident Fatality Rate
Every year, about 20 people fall overboard while on a cruise. When a person falls overboard on a cruise ship, their chance of survival is about 20% [reference]. There are several reasons for this:
1.

## Background
* Explanations of technical processes or concepts that you are using, which might be unfamiliar to your audience.
* A brief description of the prior work in the field. You should reference and briefly discuss the major papers/advances in your topic field.

### Existing Work
The end goal is for their to be an efficient way to use drones for man overboard search and rescue operations on cruise ships. With that goal in mind there are several existing stand-alone products that provide much of the functionality necessary to make that goal a reality. These products are:
* Universal Ground Control Software U|g|CS
* Dedicated SAR drones


#### Universal Ground Control Software
Talk about U|g|CS here.

Universal Ground Control Software is a tool that allows you to control multiple drones. It has many features which can be found here [source]. I will only talk about the features that will be useful for our endgoals, namely:


#### Dedicated SAR Drones
Talk about DJI Matrice 1000 SAR Kit here.


In addition, this project will incorporate these services in order to meet it's goals:
* Google location history
* NASA ocean current data

#### Google Location History
Talk about how I will integrate google location services into the project.
1. Google can track your phones location if you allow it to.
* You can download your location history using an API.
* The data can be in KML (a form of xml) or JSON format.
* Either way, the data can be easily parsed, in JSON the data is a collection of objects with timestamp, location, mode(walking, biking, riding) information.
* The data will be parsed based on the time range of the Man Overboard incident.

#### NASA Ocean Current Data
Talk about how I will integrate NASA Ocean current data into the project.



## Proposed Project
### Description of the proposed solution/approach
The solution is to make a stand alone program that takes a time range and number of drones available as input from the user, and outputs a route file that can be uploaded to U|g|CS and used to control multiple drones.

The program will take into account the following factors:
* A variable number of drones taking part in the SAR operation.
* The distance a person might have swum. In other words the search area gets larger over time since the person may not have stayed stationary.

The program will **not** take in to account the following factors:
* Wind affecting the flight of drones (Beyond the scope of Senior Project).
* Multiple trips required, and tracking areas searched on the previous trip. (This is important, and necessary for a working solution, however I feel it is beyond the scope of Senior Project)
* Location and time of SAR operation start. (The program will assume current location and time as starting point and time for drones, mostly because it won't take long to create a route file.)

Additional limitations
* OSCAR data's spatial resolution is 1/3 of a degree of latitude which is about 23 miles.

A mockup of the screen is shown below
![mockup](Images/GuiMockUp.png)

### Delineation of major tasks/milestones
The major tasks and milestones for the project are as follows:
* Connect with Google Location History API to download location history for any given time range.
* Parse JSON received from google into data that can be used to create a search grid.
* Connect with OSCAR servers to automatically download ocean current data.
* Parse OSCAR files into data that can be used in our calculations.
* Create algorithms that will calculate out where a person is likely to be based on current time, time of MOB incident, and ocean current data.
* Reverse engineer U|g|CS route file export format to be able to create our own based on the area to search and the number of drones available.

### List of required software/hardware for project and evaluation
To complete the project and it's evaluation the hardware and software that is required is:

* U|g|CS One: $60

### Description of proposed timeline (Hours per major task)
The major tasks are expected to take this long:

### Team member organization, task dilineation, and/or expected skill sets
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
* Reverse engineer U|g|CS route file export format.
* Create GUI/front end of the program.
* Help with testing.

## Testing and Evaluation
### List of target results/outcomes based on project reqs
* The program will output a route file within 1 minute of user entering necessary data.


### Description of the specific measure, target value, and testing plan that will be used to assess attainment for each target reult

### Description of the method of evaluation the success of the project.

## Conclusion
Restatement of problem statement, project goals, and summary of proposed solution and expected outcomes/deliverables

## References
