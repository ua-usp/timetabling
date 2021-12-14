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

## Teachers

## Courses

## Students

## Rules

## Solution
