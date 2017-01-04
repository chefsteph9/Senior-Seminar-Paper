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
Create a program that can track a person's likely location given the time range of when they fell overboard, using the ship's location history and ocean current data gathered from NASA.

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

#### Dedicated SAR Drones
Talk about DJI Matrice 1000 SAR Kit here.


In addition, this project will incorporate these services in order to meet it's goals:
* Google location history
* NASA ocean current data

#### Google Location History
Talk about how I will integrate google location services into the project.

#### NASA Ocean Current Data
Talk about how I will integrate NASA Ocean current data into the project.

## Proposed Project
### Description of the proposed solution/approach
The solution is to make a stand alone program that takes a time range and number of drones available as input from the user, and outputs a route file that can be uploaded to U|g|CS and used to control multiple drones.

The program will take into account the following factors:
* A variable number of drones taking part in the SAR operation.
*

The program will **not** take in to account the following factors:
* Wind
* Multiple trips required, and tracking areas searched on the previous trip.
* Location and time of SAR operation start. (The program will assume current location and time as starting point and time for drones)

A mockup of the screen is shown below
![mockup](Images/GuiMockUp.png)

### Delineation of major tasks/milestones
The major tasks and milestones for the project are as follows:

### List of required software/hardware for project and evaluation
To complete the project and it's evaluation the hardware and software that is required is:

* U|g|CS One

### Description of proposed timeline (Hours per major task)
The major tasks are expected to take this long:

### Team member organization, task dilineation, and/or expected skill sets
This project will require a 3 person team, with all CS majors.


## Testing and Evaluation
### List of target results/outcomes based on project reqs

### Description of the specific measure, target value, and testing plan that will be used to assess attainment for each target reult

### Description of the method of evaluation the success of the project.

## Conclusion
Restatement of problem statement, project goals, and summary of proposed solution and expected outcomes/deliverables

## References
