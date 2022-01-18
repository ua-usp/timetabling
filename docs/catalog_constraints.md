---
title: "USP Constraint Catalog"
layout: single
toc: true
toc_sticky: true
permalink: /Catalog
---

##Constraint Catalog

|Name | parameter (size:type) | arity |  entry | Condtionnel | Explication|
|:------|:----------|:------------|:------------------|:-------------|:---------------|:-----------------|
|Allocate slot | slot -> 1 (1,tuple?:slots) | max 1 | All | Oui | Allcate a slot or slot tuple to a session| 
|Allocation group flex| No  | max 1  | Part  | non  | Domain allocation for class and group|
|Allocation Room size  | No  | max 1  | Class  | Non  | Allocate number of room are demand to the part|
|Assign room  | rooms-> 1 (1,tuple:rooms) | max 1 | All | Oui | Assign a set of room to session in entry|
|At most daily |count -> 1 (1:slot), first -> 1 (1:slot), last -> 1 (1:slot)| max 1 | Course, Part, Class, Teacher, Room, Student | oui | Limit a number of session in intervalle|
|At most weekly| count -> 1 (1:slot)| max 1| Course, Part, Class, Teacher, Room, Student | oui | Limit a number of session in intervalle |
|Connected room| roomChain -> min 1,max n (tuple:room)[ordered] ​| max 1 |  Course, Part, Class, Teacher, Room, Student | oui | Room are connected|
|Course no overlap two day | No | max 1 | Sessions | non | A sessions duration dont overlap into 2 day of week|--> pas sur 
|Disjunctive group | No | max 1 | Student | noui | A group cant have overlap of 2 sessions |
|Disjunctive room | No | max 1 | Room | oui | A room cant host 2 sessions at same moment |
|Disjunctive teacher| No | max 1 | Teacher | oui | A teacher cant gives  classes at same moment|
|Domain class group | No | max 1 | Class | non | A subset of group to classes|
|Domain sessuion teacher | No | max 1 | sessions | non | a subset of teacher for sessions|
|Domain class room | No | max 1 | Class | non | a subset of room for class|
|Forbidden Slot | first -> 1 (1:slot), last -> 1 (1:slot) | max 1 | all | Oui | A session cant take slot in intervalle |
|Implicite sequenced sessions | No | max 1 | class | non | All sessions in classes are sequenced|
|Not consecutive rooms |  minGap -> 1 (1:slot), rooms-> min 1, max n (2,k:room)| max 1 | all | noui | If 2 sessions have rooms in tuple then need a gap of mingap to walk from one the other|
|Part Schedule | No | max 1 | all | oui | we allowed time part value|
|Same daily slot |No | max 1,n | all | oui | all slots of  selected sessions  are equal to the same daily slot|
|Same day  |No | max 1,n | all | oui | all slots of  selected sessions  are equal to the same day|
|Same rooms  |No | max 1,n | Course, Part, Class, Session, Teacher, Student | oui | all set rooms of  selected sessions  are equal|
|Same slots |No | max 1,n | all | oui | all slots of  selected sessions  are equal|
|Same teachers |No | max 1,n | Course, Part, Class, Session, Room, Student | oui | all set teachers of  selected sessions  are equal|
|Same week |No | max 1,n | all | oui | all slots of  selected sessions  are equal to the same week|
|Same weekly day |No | max 1,n | all | oui | all slots of  selected sessions  are equal to the same weekly day| 
|Same weekly slot |No | max 1,n | all | oui | all slots of  selected sessions  are equal to the same weekly slot|
|Sequenced |No | max 1,n | Course, Part, Class, Sessions | non | sessions are ordered in the horizon slot (i.e i < j slot[session[i]] < slot[session[j]] |
|Teacher repartition | class -> min 2 (1:case_selector) | min 2,n | Class | non | repartition of teacher into a differentes classes of part|
|Weekly | No | max 1,n | Course, part, class, sessions | non | a session tuple is weekly| 
