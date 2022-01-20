---
title: "USP Constraint Catalog"
layout: single
permalink: /catalog
---

## Constraint Catalog

<table>
<thead>
<tr>
<th rowspan="2">Name </th>
<th rowspan="2"> Entity </th>
<th rowspan="2"> Arity </th>
<th colspan="4">  Parameter  </th>
<th rowspan="2"> Conditional </th>
<th rowspan="2"> Explication </th>
<th rowspan="2"> Tag </th>
</tr>
<tr>
<th>name</th>
<th>number</th>
<th>type</th>
<th>size</th>
</tr>
</thead>
<tbody>
<tr><td>assign_slot </td><td> All </td><td> max 1 </td><td> slot </td> <td>1</td> <td>min 1</td> <td> slots  </td><td> yes </td><td> Assign a slot or slot tuple to a session</td><td>time</td></tr>
<tr><td>allocation_group</td><td>Part</td><td> max 1  </td><td colspan="4"> no  </td><td> no  </td><td> Domain allocation for class with group in the solution</td><td>group, domain</td></tr>
<tr><td>assign_room  </td><td> Course, Part, Class, Sessions, Teacher, Student </td><td>max 1 </td><td>rooms</td><td> 1 </td><td> min 1</td><td>rooms </td><td> yes </td><td> Assign a set of room to session in entry</td><td>room, instanciation</td></tr>
<tr><td rowspan="3">at_most_daily </td><td rowspan="3"> Course, Part, Class, Teacher, Room, Student </td><td rowspan="3"> max 1 </td><td >count</td><td> 1</td> <td>max 1</td><td>slot</td><td rowspan="3"> yes </td><td rowspan="3"> Limit a number of session in intervalle</td><td rowspan="3">time, repartition</td></tr>
<tr> <td>first</td> <td>max 1</td><td>max 1</td><td>slot</td> </tr>
<tr> <td>last</td><td>max 1</td><td>max 1</td><td>slot</td> </tr>
<tr><td>at_most_weekly </td><td> Course, Part, Class, Teacher, Room, Student </td><td> max 1 </td><td> count</td><td>1</td> <td>1</td><td>slot</td><td> yes </td><td> Limit a number of session in intervalle </td><td>time,repartition</td></tr>
<tr><td>connected_room </td><td>  Course, Part, Class, Teacher, Room, Student ​</td><td> max 1 </td><td> roomChain  </td><td> min 1 </td><td> min 2 [ordered] </td><td>room  </td><td> yes </td><td> Session need connected rooms </td><td>room, share</td></tr>
<tr><td>disjunctive_group </td><td> Student </td><td> max 1 </td><td colspan="4"> no </td><td> yes </td><td> A group cant have overlap of 2 sessions </td><td> overlap, student </td></tr>
<tr><td>disjunctive_room </td><td> Room   </td><td> max 1 </td><td colspan="4"> no </td><td> yes </td><td> A room cant host 2 sessions at same moment </td><td> overlap, room </td></tr>
<tr><td>disjunctive_teacher </td><td> Teacher </td><td> max 1 </td><td colspan ="4"> no </td><td> yes </td><td> A teacher cant gives  classes at same moment</td><td> overlap, teacher</td></tr>
<tr><td>domain_class_group </td><td> Class </td><td> max 1 </td><td colspan="4"> no </td><td> no </td><td> A subset of group to classes (need solution)</td><td> domain, group, class</td></tr>
<tr><td>domain_session_teacher </td><td> Session </td><td> max 1 </td><td colspan="4"> no </td><td> no </td><td> A subset of teacher for sessions</td><td> domain, teacher, session</td></tr>
<tr><td>domain_class_room </td><td>Class </td><td> max 1 </td><td colspan="4"> no </td><td> no </td><td> A subset of room for class </td><td>domain, class, room</td></tr>
<tr><td rowspan="2">forbidden_slot </td><td rowspan="2"> All </td><td rowspan="2"> max 1 </td><td> first</td> <td> 1 </td><td>1</td><td>slot</td><td rowspan="2"> yes </td><td rowspan="2"> A session cant take slot in intervalle </td><td rowspan="2">time, domain</td><tr>
<tr><td>last </td><td> 1 </td><td>1</td><td>slot</td></tr>
<tr><td>implicite_sequenced_sessions </td><td> Class </td><td> max 1 </td><td colspan="4"> no </td><td> no </td><td> All sessions in classes are sequenced</td><td>session, orchestration</td></tr>
<tr><td rowspan="2">not_consecutive_rooms </td><td rowspan="2"> Course, Part, Class, Teacher, Student </td><td rowspan="2"> max 1 </td><td> minGap</td> <td> 1</td> <td>1</td><td>slot </td><td rowspan="2"> yes </td><td rowspan="2"> If 2 sessions have rooms in tuple then need a gap of mingap to walk from one the other</td><td rowspan="2">room, domain</td></tr>
<tr><td>rooms</td><td> 2</td> <td>min 1</td> <td>room, label</td></tr>
<tr><td>part_schedule </td><td> all </td><td> max 1 </td><td colspan="4"> no  </td><td> yes </td><td> we allowed time part value</td><td>time, part, domain</td></tr>
<tr><td>same_daily_slot </td><td> all </td><td> min 1 </td><td colspan="4"> no </td><td> yes </td><td> all slots of  selected sessions  are equal to the same daily slot </td><td> time, repartition, domain</td></tr>
<tr><td>same_day  </td><td> all </td><td> min 1 </td><td colspan="4"> no </td><td> yes </td><td> all slots of  selected sessions  are equal to the same day </td><td> time, repartition, domain</td></tr>
<tr><td>same_rooms </td><td> Course, Part, Class, Session, Teacher, Student  </td><td> min 1 </td><td colspan="4"> no </td><td> yes </td><td> all set rooms of  selected sessions  are equal </td><td>rooms, domain, repartition</td></tr>
<tr><td>same_slots </td><td> all  </td><td> min 1 </td><td colspan="4"> no </td><td> yes </td><td> all slots of  selected sessions  are equal </td><td>time, domain, repartition</td></tr>
<tr><td>same_teachers </td><td> Course, Part, Class, Session, Room, Student  </td><td> min 1 </td><td colspan="4"> no </td><td> yes </td><td> all set teachers of  selected sessions  are equal </td><td> teacher, repartition, domain</td></tr>
<tr><td>same_week </td><td> all </td><td> min 1</td><td colspan="4"> no </td><td> yes </td><td> all slots of  selected sessions  are equal to the same week </td><td> time, repartition, domain</td></tr>
<tr><td>same_weeklyday </td><td> all </td><td> min 1 </td><td colspan="4"> no </td><td> yes </td><td> all slots of  selected sessions  are equal to the same weekly day </td><td> time, repartition, domain</td></tr>
<tr><td>same_weeklyslot </td><td> all </td><td> min 1</td><td colspan="4"> no </td><td> yes </td><td> all slots of  selected sessions  are equal to the same weekly slot </td><td> time, repartition, domain</td></tr>
<tr><td>sequenced </td><td> Course, Part, Class, Session </td><td> min 1</td><td colspan="4"> no </td><td> no </td><td> Sessions are ordered in the horizon slot (i.e i &lt; j slot[session[i]] &lt; slot[session[j]] </td><td>session, orchestration</td></tr>
<tr><td>teacher_repartition </td><td> Class </td><td> min 2 </td><td> class-<i>i</i></td> <td> min 2</td> <td>1</td> <td>Option  </td><td> no </td><td> repartition of teacher into a differentes classes of part </td><td> repartition, teacher, session</td></tr>
<tr><td>weekly </td><td> Course, Part, Class, Session </td><td> min 1</td><td colspan="4"> no </td><td> no </td><td> A session tuple is weekly </td><td> repartition, time, orchestration</td></tr>
</tbody>
</table>



## Constraint camoufled


|Name | Entity | Conditional | Explication | Tag|
|:--------|:--------|:--------|:--------|:--------|
|size_room_domain | Class | no | Allocate number of room are demand to the part | domain, room|
|session_no_overlap_two_day | Session | no | A sessions duration dont overlap into 2 day of week| domain, time, overlap| 
