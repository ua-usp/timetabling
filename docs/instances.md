---
title: "USP Instances"
layout: single
permalink: /instances
---

We built a real-life instance modeling the second semester of the last year of Bachelor in Computer Sciences at [Université d'Angers](https://www.univ-angers.fr/fr/index.html).

The instance contains 5 mandatory courses and 2 courses to choose among 4 additional courses.
The instance thus consists of 9 courses decomposed into 24 parts, 45 classes and 241 sessions.
Courses are taught during 12 weeks, 5 days a week (Monday to Friday), where each day is divided into 1440 slots.
At the Faculty of Sciences of Université d'Angers, course sessions last 1h and 20 minutes or 2 hours and start at regular intervals every 90 minutes starting at 8h00 and finishing at 19h50.
The 90 minutes interval includes a 10 minutes break allowing students and lecturers to change rooms.

The instance contains 8 rooms, 12 lecturers and 67 students.
In our case, student sectioning was performed in advance and prepartitioned the students into 4 groups.
Lecturers are either course owners involved in all the parts of a course (lecture, tutorial and lab) or tutors that are involved in labs of different courses.
There are 47 rules defined in the instance.

This instance can be downloaded in [XML](/assets/instances/ua_l3info_2021.xml), [JSON](/assets/instances/ua_l3info_2021_extension.json) or [DZN](/assets/instances/ua_l3info_2021.dzn) (with the specific [tt_rules_constraints.mzn](/assets/instances/tt_rules_constraints.mzn) file).

