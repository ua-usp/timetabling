---
title: "XML Schema specifications"
layout: single
toc: true
toc_sticky: true
permalink: /schema
---

USP is defined by a XML Schema.
This schema represents both an instance and its solution.

```xml
<timetabling name="main_structure" nrWeeks="12" nrDaysPerWeek="5" nrSlotsPerDay="1440">
    <rooms>
      <!-- ... -->
    </rooms>
  
    <teachers>
      <!-- ... -->
    </teachers>

    <courses>
      <!-- ... -->
    </courses>

    <students>
      <!-- ... -->
    </students>
    
    <rules>
      <!-- ... -->
    </rules>

    <solution>
      <!-- ... -->
     </solution>
</timetabling>
```

A USP problem uses a time frame.
This time frame is defined by the number of weeks available for the courses (`nrWeeks`), the number of days where courses can occur in the week (`nrDaysPerWeek`), and how many time slots are they in a day (`nrSlotsPerDay`).
It is assumed that the weeks are consecutives, the days are consecutives even if the problem has less days than a full week, the first slot of a day starts at midnight, the last slot of a day ends at midnight, and slots are consecutives.

A USP problem is described by its resources: the rooms available for the courses, the teachers giving courses, the courses themselves and the students attending the courses.
Some of those resources may have specific rules on how they are available for example.

The solution of a USP problem instance will be outputed in the same file as the input, so that the solution is with all the data that lead to this solution.

## Rooms

Rooms are the first resources defined in a USP problem.
The only thing we need to now about a room is its capacity.
As every resources of a USP problem, rooms can be freely labelled.

```xml
<rooms>
	<room id="AMPHI-A" capacity="90" label="BUILDING-A"/>
	<room id="AMPHI-B" capacity="286" label="BUILDING-A"/>
	<room id="H001" capacity="20" label="BUILDING-H"/>
	<room id="H002" capacity="42" label="BUILDING-H"/>
	<room id="H003" capacity="38" label="BUILDING-H"/>
</rooms>
```

In this example, we define 5 rooms with different capacities, and chose to label them with the building they belong.

## Teachers

Teachers are the ones giving lectures and tutoring students.
In a USP problem, teachers are only listed to be refered to in other sections.
As every resources of a USP problem, teachers can be freely labelled.

```xml
<teachers>
    <teacher id="TURING Alan" label="COMPUTER-SCIENCES"/>
    <teacher id="LOVELACE Ada" label="COMPUTER-SCIENCES"/>
</teachers>
```

## Courses

## Students

## Rules

## Solution
