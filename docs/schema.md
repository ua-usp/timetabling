---
title: "USP Schema"
layout: single
toc: true
toc_sticky: true
permalink: /schema
---

USP is defined by an XML Schema.
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

A USP problem is defined by a set of course sessions and the resources required: the rooms available for the courses, the teachers giving courses and the students attending the courses.
Some of those resources may have specific rules on how they are available for example.
Courses and resources are identified by a unique identifier and can be labelled by a list of labels.

The solution of a USP problem instance will be outputed in the same file as the input, so that the solution is with all the data that lead to this solution.

The examples below of this page are based on the time frame from the example above: 12 weeks, 5 days a week (Mondays to Fridays) and 1440 slots a day (1 slot per minute).

## Rooms

Rooms are the first resources defined in a USP problem.
The only thing we need to now about a room is its capacity.
A negative capacity means that a the room capacity has no limit.
As every resources of a USP problem, rooms can be freely labelled.

```xml
<!-- into the root element 'timetabling' -->
<rooms>
	<room id="room-a1" capacity="90" label="Building-A"/>
	<room id="room-a2" capacity="286" label="Building-A"/>
	<room id="room-h1" capacity="20" label="Building-H"/>
	<room id="room-h2" capacity="42" label="Building-H"/>
	<room id="room-h3" capacity="38" label="Building-H"/>
	<room id="teams-1" capacity="-1" label="Teams" />
</rooms>
```

In this example, we define five rooms with different capacities, and chose to label them with the building they belong.
A sixth room (`teams-1`) is a virtual one, with no capacity.

## Teachers

Teachers are the ones giving lectures and tutoring students.
In a USP problem, teachers are only listed to be refered to in other sections.
As every resources of a USP problem, teachers can be freely labelled.

```xml
<!-- into the root element 'timetabling' -->
<teachers>
    <teacher id="teacher-1" label="Computer-Sciences"/>
    <teacher id="teacher-2" label="Computer-Sciences"/>
</teachers>
```

In this example, we define two teachers from the Computer Sciences department, and chose to label them with their department.

## Courses

Universities organise courses to their students in order for them to get a diploma.
The hierarchy of courses is complex (in which cursus the course takes place, etc.) and is not represented here.
In a USP problem, the courses are independant from each other.
Nonetheless, this hierarchy can be represented with labels in order to state rules on such courses.
In the example below, the course `course-1` is a 3rd year of bachelor course from the computer sciences department.

```xml
<!-- into the root element 'timetabling' -->
<courses>
	<course id="course-1" label="Bachelor,Year-3,Computer-Sciences">
		<part id="course-1-lecture" nrSessions="12"  label="Lecture">
		    <classes>
		        <class id="course-1-lecture-1" maxHeadCount="80" />
		    </classes>
		    
		    <allowedSlots sessionLength="80">
		        <dailySlots>480,570,660,750,840,930,1020,1110,1200</dailySlots>
		        <days>1-5</days>
		        <weeks>1-12</weeks>
		    </allowedSlots>

		    <allowedRooms sessionRooms="multiple">
		        <room refId="room-a1" />
		        <room refId="room-a2" />
		    </allowedRooms>

		    <allowedTeachers sessionTeachers="1">
		        <teacher refId="teacher-1" nrSessions="12" />
		    </allowedTeachers>
		</part>
		
		<part id="course-1-tutorial" nrSessions="10" label="Tutorial">
			<classes>
				<class id="course-1-tutorial-1" maxHeadCount="30" parent="course-1-lecture-1" />
				<class id="course-1-tutorial-2" maxHeadCount="30" parent="course-1-lecture-1" />
			</classes>
			
			<allowedSlots sessionLength="160">
				<dailySlots>480,570,660,750,840,930,1020,1110,1200</dailySlots>
				<days>1-5</days>
				<weeks>1-12</weeks>
            </allowedSlots>
            
            <allowedRooms sessionRooms="single">
            	<room refId="room-a1" />
            	<room refId="room-a2" />
            	<room refId="room-h1" />
            	<room refId="room-h2" />
            	<room refId="room-h3" />
        	</allowedRooms>
        	
        	<allowedTeachers sessionTeachers="1">
        		<teacher refId="teacher-1" nrSessions="20" />
    		</allowedTeachers>
		</part>
		
		<part id="course-1-practice" nrSessions="8" label="Practice">
			<classes>
				<class id="course-1-practice-1" maxHeadCount="20" parent="course-1-tutorial-1" />
				<class id="course-1-practice-2" maxHeadCount="20" />
				<class id="course-1-practice-3" maxHeadCount="20" parent="course-1-tutorial-2" />
			</classes>
			
			<allowedSlots sessionLength="160">
				<dailySlots>480,570,660,750,840,930,1020,1110,1200</dailySlots>
				<days>1-5</days>
				<weeks>1-12</weeks>
			</allowedSlots>
			
			<allowedRooms sessionRooms="single">
				<room refId="room-h1" />
				<room refId="room-h2" />
				<room refId="room-h3" />
			</allowedRooms>
			
			<allowedTeachers sessionTeachers="1">
				<teacher refId="teacher-1" nrSessions="12" />
				<teacher refId="teacher-2" nrSessions="12" />
			</allowedTeachers>
		</part>
	</course>
</courses>
```

A course is divided into parts.
A student that decide to follow a course must attend all the parts of the course.
In the part, we define the student classes, the time slots when the sessions can start, the rooms in which the sessions can be and the teachers.

```xml
<!-- into a 'part' element -->
<classes>
	<class id="course-1-practice-1" maxHeadCount="20" parent="course-1-tutorial-1" />
	<class id="course-1-practice-2" maxHeadCount="20" />
	<class id="course-1-practice-3" maxHeadCount="20" parent="course-1-tutorial-2" />
</classes>
```

A class is a set of students attending the course part.
The size of the class is limited (`maxHeadCount`).
A student registered to the course will be assigned to exactly one class of each part of the course.
The same number of sessions (`nrSessions`) will be scheduled for each class of a part.
We may want to force the fact that the students of one class have to attend another class (`parent`).

In our example above, we have three classes of practice and two of tutorial, the table below illustrate how we would like the students to be split.
By forcing the students of the practice `course-1-practice-1` to attend the tutorial `course-1-tutorial-1` and the students of the practice `course-1-practice-3` to attend the tutorial `course-1-tutorial-2`, we are assured that the students of `course-1-practice-2` will be split between the two tutorials.
In our example we require students attending the tutorial to attend the lecture.
Note that this is useless in this particular case because the lecture part has only one part, therefore all students must necesseraly attend this lecture.

<table>
	<thead>
		<tr>
			<th>Lecture</th>
			<th>Tutorial</th>
			<th>Practice</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td rowspan="4">course-1-lecture-1</td>
			<td rowspan="2">course-1-tutorial-1</td>
			<td>course-1-practice-1</td>
		</tr>
		<tr>
			<td rowspan="2">course-1-practice-2</td>
		</tr>
		<tr>
			<td rowspan="2">course-1-tutorial-2</td>
		</tr>
		<tr>
			<td>course-1-practice-3</td>
		</tr>
	</tbody>
</table>


```xml
<!-- into a 'part' element -->
<allowedSlots sessionLength="80">
    <dailySlots>480,570,660,750,840,930,1020,1110,1200</dailySlots>
    <days>1-5</days>
    <weeks>1-12</weeks>
</allowedSlots>
```

Sessions of a class have the same duration and are typically subject to time constraint related to their possible start time.
In a USP problem, the duration of a session is measure by the number of slots used by the session (`sessionLength`).
The list of possible start times is represented by a time grid of starting slots (`dailySlots`) among some days of the week (`days`) for some defined weeks (`weeks`).
The time grid reduces the time horizon.
Rules can also be stated to forbid additional slots.

Remember here that in our examples, a slot last 1 minute, there are 5 days per week and 12 weeks.
In the example above, sessions last `80` slots (80 minutes in our case).
The time grid has 9 possible start slots: 08h00 (`480`), 09h30 (`570`), 11h00 (`660`), 12h30 (`750`), 14h00 (`840`), 15h30 (`930`), 17h00 (`1020`), 18h30 (`1110`) or 20h00 (`1200`).
This grid is valid for all the all the days (`1-5`) and all the weeks (`1-12`).

```xml
<!-- into a 'part' element -->
<allowedRooms sessionRooms="single">
	<room refId="room-h1" />
	<room refId="room-h2" />
	<room refId="room-h3" />
</allowedRooms>
```

In a general case not all rooms will be compatible for a given part due to specific features such as equipments or laboratories.
We thus define the set of rooms in which the sessions may take place.
Some parts will require a single room per session (`sessionRooms="single"`) while other parts will require several rooms (`sessionRooms="multiple"`).

In the example above, the sessions should take place in one room among `room-h1`, `room-h2` and `room-h3`.
Int the main example at the top of the section, the lecture (part id `course-1-lecture`) takes place in one room and is broadcasted in another one.
That is why the session should take place in several rooms among the ones that have this type of equipment.
The model does not know that rooms `room-a1` and `room-a2` can handle these sessions, but the university has the information and thus can filter the rooms to affect them to the part.

```xml
<!-- into a 'part' element (with 8 sessions and 3 classes) -->
<allowedTeachers sessionTeachers="1">
	<teacher refId="teacher-1" nrSessions="12" />
	<teacher refId="teacher-2" nrSessions="12" />
</allowedTeachers>
```

Teachers give the number of sessions (`nrSessions`) they will teach in the part.
Each session of the part have a fixed amount of teachers/tutors (`sessionTeachers`).
We thus define how many hours a teacher will spend in the part, but the solver will have to affect a teacher to a specific session.
The teacher repartition between classes of a part can be given with rules.

In our example above, `teacher-1` teaches all the sessions of the lecture and both classes of the tutorials.
The two teachers `teacher-1` and `teacher-2` shares evenly the sessions of the practice (12 sessions each).
Whether `teacher-1` does all the first sessions then `teacher-2` the last ones, or `teacher-1` and `teacher-2` have a class each and share the third, or another repartition, is not described here.

## Students

## Rules

## Solution
