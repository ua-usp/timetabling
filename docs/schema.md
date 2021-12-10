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

The XML root element `timetabling` has 4 mandatory attributes:
- `name`: The name of the instance
- `nrWeeks`: Defines the size of the instance by defining how many calendar weeks are needed. The weeks are considered consecutives in the problem.
- `nrDaysPerWeek`: Defines the size of the instance by defining how many days can be used in the week. The days are considered consecutives in the problem.
- `nrSlotsPerDay`: Defines the size of the instance by defining how many time slots can be used in the day. The slots are considered consecutives in the problem and all the slots cover an entire day, meaning that the first slot will start at midnight and the last slot will end at midnight.

## Rooms

## Teachers

## Courses

## Students

## Rules

## Solution
