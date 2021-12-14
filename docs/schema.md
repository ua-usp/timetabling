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
	<room id="room-a1" capacity="90" label="Building-A"/>
	<room id="room-a2" capacity="286" label="Building-A"/>
	<room id="room-h1" capacity="20" label="Building-H"/>
	<room id="room-h2" capacity="42" label="Building-H"/>
	<room id="room-h3" capacity="38" label="Building-H"/>
</rooms>
```

In this example, we define 5 rooms with different capacities, and chose to label them with the building they belong.

## Teachers

Teachers are the ones giving lectures and tutoring students.
In a USP problem, teachers are only listed to be refered to in other sections.
As every resources of a USP problem, teachers can be freely labelled.

```xml
<teachers>
    <teacher id="teacher-1" label="Computer-Sciences"/>
    <teacher id="teacher-2" label="Computer-Sciences"/>
</teachers>
```

## Courses

Courses are the main resources of a USP problem.
They are the only mandatory resources in a problem.

Universities organise courses to their students in order for them to get a diploma.
The hierarchy of courses is complex (in which cursus the course takes place, etc.) and is not represented here.
Nonetheless, this hierarchy can be represented with labels.
In the example below, the course `course-1` is a 3rd year of bachelor course from the computer sciences department.

```xml
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

		    <allowedRooms sessionRooms="single">
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

A student class is a group of students attending the course.
The size of the group is limited (`maxHeadCount`).
A student registered to the course will be assigned to exactly one class of each part of the course.
A class has `nrSessions` sessions, meaning that the total number of sessions for a part is `nrSessions` times the number of classes.
We may want to force the fact that the students of one class have to attend another class.

In our example above, we force the fact that the students of the tutorials attend the lecture.
Note that this is useless because a student must attend all the parts, and the lecture part has only one class.
In our example have three classes of practice and two of tutorial, the table below illustrate how we would like the students to be splitted.
By forcing the students of the practice `course-1-practice-1` to attend the tutorial `course-1-tutorial-1` and the students of the practice `course-1-practice-3` to attend the tutorial `course-1-tutorial-2`, we are assured that the students of `course-1-practice-2` will be split between the two tutorials.

| Lecture | Tutorial | Practice |
|---------|----------|----------|
| course-1-lecture-1 | course-1-tutorial-1 | course-1-practice-1 |
| course-1-lecture-1 | course-1-tutorial-1 | course-1-practice-2 |
| course-1-lecture-1 | course-1-tutorial-2 | course-1-practice-2 |
| course-1-lecture-1 | course-1-tutorial-2 | course-1-practice-3 |

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

The `allowedSlots` element is used to define the time-related information of a session.
First it defines the length of a session (`sessionLength`) by giving the number of slots used for one session.
Second, it reduces the problem size: instead of using all the slots of the USP problem, we define all the starting slots.
The starting slots are defined by giving the corresponding daily slots, days and weeks: it defines a kind of time grid where the sessions can be put.
A [rule](#rules) can be used to forbid some slots in this grid.

The set of rooms in which the sessions is defined for two reasons: first reduce the size of possible rooms and second to give the possiblity to the teachers to select rooms with specific features (e.g. laboratories).
A session can take place in one (`sessionRooms="single"`à or several (`sessionRooms="multiple"`) rooms.

Teachers give the number of sessions (`nrSessions`) they will teach in the part.
Each session of the part have a fixed amount of teachers/tutors (`sessionTeachers`).
We thus define how many hours a teacher will spend in the part, but the solver will have to affect a teacher to a specific session.
The teacher repartition between classes of a part can be given with [rules](#rules).
In our example, `teacher-1` teaches all the sessions of the lecture and both classes of the tutorials.
The two teachers `teacher-1` and `teacher-2` shares evenly the sessions of the practice (12 sessions each).
Whether `teacher-1` does all the first sessions then `teacher-2` the last ones, or `teacher-1` and `teacher-2` have a class each and share the third, is not described here.

## Students

## Rules

## Solution
