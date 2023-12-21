---
title: "USP Constraint Catalog"
layout: single
classes: wide
permalink: /catalog
---

## Constraint Catalog

Constraints are applied to sets of sessions (referred as "the sessions" in the short descriptions) selected *via* selectors (see [schema](schema.md)).
Constraints may have parameters.
In the case where the parameters are repeated several times, the union of the parameters is used.

### Constraint list

<table>
	<thead>
		<tr>
			<th>Name</th>
			<th><abbr title="Number of selectors">Size</abbr></th>
			<th>Parameters</th>
			<th>Short description</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td><a href="#adjacent_rooms">adjacent_rooms</a></td>
			<td>single</td>
			<td><code>roomChain</code>: comma separated list of room identifiers<br><i>This parameter can be repeated. One <code>roomChain</code> defines adjacent rooms in order.</i></td>
			<td></td>
		</tr>
		<tr>
			<td>allowed_grids</td>
			<td>single</td>
			<td><code>dailySlots</code>: list of starting slots<br/><code>days</code>: list of allowed days<br/><code>weeks</code>: list of allowed weeks</td>
			<td>union parameters</td>
		</tr>
		<tr>
			<td>allowed_slots</td>
			<td>single</td>
			<td><code>first</code>: first allowed slot<br/><code>last</code>: last allowed slot<br/><code>period</code> (<i>optional</i>): the slots are dailyslots (<code>day</code>), weeklyslots (<code>week</code>) or absolute (<code>global</code> - default)</td>
			<td></td>
		</tr>
		<tr>
			<td>allowed_rooms</td>
			<td>single</td>
			<td><code>rooms</code>: comma separated list of room identifiers</td>
			<td></td>
		</tr>
		<tr>
			<td>allowed_teachers</td>
			<td>single</td>
			<td><code>teachers</code>: comma separated list of teacher identifiers</td>
			<td></td>
		</tr>
		<tr>
			<td>assign_rooms</td>
			<td>single</td>
			<td><code>rooms</code>: comma separated list of room identifiers</td>
			<td></td>
		</tr>
		<tr>
			<td>assign_slot</td>
			<td>single</td>
			<td><code>slot</code>: slot to be assigned</td>
			<td></td>
		</tr>
		<tr>
			<td>assign_teachers</td>
			<td>single</td>
			<td><code>teachers</code>: comma separated list of teacher identifiers</td>
			<td></td>
		</tr>
		<tr>
			<td>compactness</td>
			<td>single</td>
			<td><code>separation</code>: the <code>min-max</code> number of slots allowed between two sessions of the same day</td>
			<td></td>
		</tr>
		<tr>
			<td>different_daily_slot</td>
			<td>single</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>different_day</td>
			<td>single</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>different_rooms</td>
			<td>single</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>different_slot</td>
			<td>single</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>different_teachers</td>
			<td>single</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>different_week</td>
			<td>single</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>different_weekday</td>
			<td>single</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>different_weeklyslot</td>
			<td>single</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>forbidden_rooms</td>
			<td>single</td>
			<td><code>rooms</code>: comma separated list of room identifiers</td>
			<td></td>
		</tr>
		<tr>
			<td>forbidden_slots</td>
			<td>single</td>
			<td><code>first</code>: first forbidden slot<br/><code>last</code>: last forbidden slot<br/><code>period</code> (<i>optional</i>): the slots are dailyslots (<code>day</code>), weeklyslots (<code>week</code>) or absolute (<code>global</code> - default)</td>
			<td></td>
		</tr>
		<tr>
			<td>forbidden_teachers</td>
			<td>single</td>
			<td><code>teachers</code>: comma separated list of teacher identifiers</td>
			<td></td>
		</tr>
		<tr>
			<td>gap</td>
			<td>multiple</td>
			<td><code>scope</code>: should the gap be computed for all (<code>ALL</code>) the sessions in the sets or only the one finishing first and the one starting last (<code>FL</code>)<br/><code>value</code>: <code>min-max</code><br/><code>unit</code>: unit of the <code>value</code>. Can be <code>slot</code>, <code>day</code> or <code>week</code>.</td>
			<td></td>
		</tr>
		<tr>
			<td>no_overlap</td>
			<td>single</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>pairwise_no_overlap</td>
			<td>multiple</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>periodic</td>
			<td>single</td>
			<td><code>value</code>: number of <code>unit</code>s between two successive sessions<br/><code>unit</code>: unit of the <code>value</code> (can be <code>day</code> or <code>week</code>)</td>
			<td></td>
		</tr>
		<tr>
			<td>required_rooms</td>
			<td>single</td>
			<td><code>rooms</code>: comma separated list of room identifiers</td>
			<td></td>
		</tr>
		<tr>
			<td>required_teachers</td>
			<td>single</td>
			<td><code>teacherId</code>: teacher identifier<br/><code>nrSessions</code> : number of <code>min-max</code> sessions that should be assigned to <code>teacherId</code></td>
			<td>union parameters</td>
		</tr>
		<tr>
			<td>same_daily_slot</td>
			<td>single</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>same_day</td>
			<td>single</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>same_rooms</td>
			<td>single</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>same_slot</td>
			<td>single</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>same_teachers</td>
			<td>single</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>same_week</td>
			<td>single</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>same_weekday</td>
			<td>single</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>same_weeklyslot</td>
			<td>single</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>sequenced</td>
			<td>multiple</td>
			<td>None</td>
			<td></td>
		</tr>
		<tr>
			<td>workload</td>
			<td>single</td>
			<td><code>scope</code> : the workload should be computed for every <code>week</code> or every <code>day</code><br/><code>value</code> : <code>min-max</code><br/><code>unit</code> : should the <code>value</code> be a number of <code>session</code>s or <code>slot</code>s</td>
			<td></td>
		</tr>
	</tbody>
</table>

### Constraint explications

#### adjacent_rooms
#### allowed_grids

