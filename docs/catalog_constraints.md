---
title: "USP Constraint Catalog"
layout: single
permalink: /catalog
---

##Constraint Catalog

|Name | Entity | Arity |  Parameter (name,type,size) | Conditional | Explication | Tag |
|:------|:------------------|:------------|:------------------|:-------------|:---------------|:---------------------|:--------|
|assign_slot | All | max 1 | slot -> 1 (1,tuple?:slots)   | yes | Assign a slot or slot tuple to a session|time|
|allocation_group|Part| max 1  | no  | no  | Domain allocation for class with group in the solution|group, domain|
|assign_room  | Course, Part, Class, Sessions, Teacher, Student |max 1 |rooms-> 1 (1,tuple:rooms) | yes | Assign a set of room to session in entry|room, instanciation|
|at_most_daily | Course, Part, Class, Teacher, Room, Student | max 1 |count -> 1 (1:slot), first -> 1 (1:slot), last -> 1 (1:slot)  | yes | Limit a number of session in intervalle|time, repartition|
|at_most_weekly | Course, Part, Class, Teacher, Room, Student | max 1 | count -> 1 (1:slot)| yes | Limit a number of session in intervalle |time,repartition|
|connected_room |  Course, Part, Class, Teacher, Room, Student ​| max 1 | roomChain -> min 1,max n (tuple:room)[ordered]  | yes | Session need connected rooms |room, share|
|disjunctive_group | Student | max 1 | yes | yes | A group cant have overlap of 2 sessions | overlap, student |
|disjunctive_room | Room   | max 1 | no | yes | A room cant host 2 sessions at same moment | overlap, room |
|disjunctive_teacher | Teacher | max 1 | no | yes | A teacher cant gives  classes at same moment| overlap, teacher|
|domain_class_group | Class | max 1 | no | no | A subset of group to classes (need solution)| domain, group, class|
|domain_session_teacher | Session | max 1 | no | no | A subset of teacher for sessions| domain, teacher, session|
|domain_class_room |Class | max 1 | no | no | A subset of room for class |domain, class, room|
|forbidden_slot | All | max 1 | first -> 1 (1:slot), last -> 1 (1:slot) | yes | A session cant take slot in intervalle |time, domain|
|implicite_sequenced_sessions | Class | max 1 | no | no | All sessions in classes are sequenced|session, orchestration|
|not_consecutive_rooms | Course, Part, Class, Teacher, Student | max 1 | minGap -> 1 (1:slot), rooms-> min 1, max n (2,k:room) | yes | If 2 sessions have rooms in tuple then need a gap of mingap to walk from one the other|room, domain|
|part_schedule | all | max 1 | no  | yes | we allowed time part value|time, part, domain|
|same_daily_slot | all | min 1, max n | no | yes | all slots of  selected sessions  are equal to the same daily slot | time, repartition, domain|
|same_day  | all | min 1, max n | no | yes | all slots of  selected sessions  are equal to the same day | time, repartition, domain|
|same_rooms | Course, Part, Class, Session, Teacher, Student  | min 1, max n | no | yes | all set rooms of  selected sessions  are equal |rooms, domain, repartition|
|same_slots | all  | min 1, max n | no | yes | all slots of  selected sessions  are equal |time, domain, repartition|
|same_teachers | Course, Part, Class, Session, Room, Student  | min 1, max n | no | yes | all set teachers of  selected sessions  are equal | teacher, repartition, domain|
|same_week | all | min 1, max n | no | yes | all slots of  selected sessions  are equal to the same week | time, repartition, domain|
|same_weeklyday | all | min 1, max n | no | yes | all slots of  selected sessions  are equal to the same weekly day | time, repartition, domain|
|same_weeklyslot | all | min 1, max n | no | yes | all slots of  selected sessions  are equal to the same weekly slot | time, repartition, domain|
|sequenced | Course, Part, Class, Session | min 1, max n | no | no | Sessions are ordered in the horizon slot (i.e i < j slot[session[i]] < slot[session[j]] |session, orchestration|
|teacher_repartition | Class | min 2, max n | class -> min 2 (1:case_selector)  | no | repartition of teacher into a differentes classes of part | repartition, teacher, session|
|weekly | Course, Part, Class, Session | min 1, max n | no | no | A session tuple is weekly | repartition, time, orchestration|


##Constraint camoufled

|Name | Entity | Conditional | Explication | Tag|
|:--------|:--------|:--------|:--------|:--------|
|size_room_domain | Class | no | Allocate number of room are demand to the part | domain, room|
|session_no_overlap_two_day | Session | no | A sessions duration dont overlap into 2 day of week| domain, time, overlap| 
