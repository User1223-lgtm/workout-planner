---
layout: default
title: Creating & Editing Workouts
description: Create workouts from templates, from scratch or with AI, and edit exercises, rests and nested groups in the Workout Planner editor.
---

# Creating & Editing Workouts

<p class="lead">Start from a template, from scratch or with AI, then shape the workout block by block.</p>

<div class="toc" markdown="1">
On this page

* TOC
{:toc}
</div>

## Three ways to create a workout

{% include screen.html image="create-workout.jpg" alt="Create a Workout: From Scratch, From a Template, With AI" caption="Create a Workout" class="right" %}

Open the folder where you want the new workout, then tap **⋯ › Create a Workout**. The **Create a Workout** sheet asks *How do you want to start?*:

| Choice | What it does | Access |
|---|---|---|
| **From Scratch** | Opens an empty workout in the editor. | <span class="badge pro">Pro</span> |
| **From a Template** | Creates a ready-made workout in one tap. | <span class="badge free">Free</span> |
| **With AI** | Asks you 7 questions and Apple Intelligence plans the workout. | Pay per workout, or free once a month with Pro |

The new workout is always saved in the folder you were in. Tap **Cancel** to close the sheet without creating anything.

## From a template

Tap **From a Template**, then tap a template: the workout is **created immediately** in the current folder, and the **Workout Created** screen confirms it (tap **Done**). The same screen appears after **From Scratch** and **With AI**. If a workout with the same name already exists in the folder, the new one gets a number (*Tabata 2*).

| Template | Workout name | Structure | Total |
|---|---|---|---|
| **Tabata** | Tabata | Group *Tabata* ×8: Work 20 s, Rest 10 s | 4 min |
| **EMOM** | EMOM 10 | Group *EMOM* ×10: Work 60 s. Do your reps at the start of each minute and rest for the time left. | 10 min |
| **AMRAP** | AMRAP 20 | One 20-minute exercise: repeat your circuit as many times as possible. | 20 min |
| **HIIT 30/30** | HIIT 30/30 | Warm-up 3 min · Group *Intervals* ×10: Work 30 s, Rest 30 s · Cool-down 3 min | 16 min |
| **Circuit Training** | Circuit Training | Warm-up 2 min · Group *Circuit* ×3: Squats 40 s, Rest 20 s, Push-ups 40 s, Rest 20 s, Lunges 40 s, Rest 20 s, Plank 40 s, Round rest 60 s | 16 min |
| **Double Tabata** | Double Tabata | Group *Blocks* ×2: (Group *Tabata* ×8: Work 20 s, Rest 10 s), Block rest 60 s | 10 min |
| **Strength Sets** | Strength Sets | Group *Sets* ×5: Set 45 s, Rest 90 s | 11m 15s |
| **Running Intervals** | Running Intervals | Warm-up jog 5 min · Group *Intervals* ×6: Run 2 min, Walk 1 min · Cool-down 5 min | 28 min |

A template becomes a normal workout: you can rename, duplicate, move, export and start it like any other. Changing its blocks requires [Pro](pro.html).

## From scratch <span class="badge pro">Pro</span>

Tap **From Scratch** to open the editor with an empty workout. Give it a name, add blocks, then tap **Create** at the top right. Without Pro, this choice shows a crown and opens the Workout Planner Pro screen.

## With AI

See the dedicated page: [AI Workouts](ai-workouts.html).

## The editor <span class="badge pro">Pro</span>

The editor opens when you create a workout from scratch, or when you choose **Edit Workout** on an existing workout (from its page or from its touch-and-hold menu).

It contains three parts:

1. **Name** (required). It must be unique in the folder. If it is already used, the message *A workout with this name already exists in this folder.* appears under the field and you can't save.
2. **Description** (optional). A free text shown on the workout's page, also used by [search](organizing-workouts.html#search).
3. **Blocks**: the program. Its footer shows the **Total duration**.

At the top:

- **Create** (new workout) or **Save** (existing workout) writes your changes. It stays greyed out while the name is empty or already used.
- **Cancel** closes the editor. If you changed something, the app asks **Discard Changes?** with **Cancel** (keep editing) or **Discard**.
- While there are unsaved changes, swiping the editor down doesn't close it, so you can't lose your work by accident.

Nothing is saved until you tap **Create** or **Save**.

## Blocks

### The three kinds of blocks

| Block | Fields | Rules | Color |
|---|---|---|---|
| **Exercise** | Name, Description, Duration | Name and a duration above 0 are required. The description is optional: it appears under the name on the timer, so it is a good place for a coaching cue (*Keep your back straight…*). | <span class="badge exercise">red</span> |
| **Rest** | Duration | A duration above 0 is required. A rest is shown as *Rest*. | <span class="badge rest">green</span> |
| **Group of Blocks** | Name, Rounds | Rounds from **1 to 99** (×1 to ×99). The name is optional (an unnamed group is shown as *Group*). | <span class="badge group">orange</span> |

The **duration picker** has three wheels: **hours** (0–23), **minutes** (0–59) and **seconds** (0–59).

New blocks start with sensible values: an exercise lasts 30 s, a rest 15 s, and a group has ×3 rounds.

### Add a block

Tap **Add a Block** at the end of the list and choose **Exercise**, **Rest** or **Group of Blocks**. Fill in the form, then tap **Add**. The block is added at the end of the list.

### Change a block

- Tap an **exercise** or a **rest** to open its form. Change it, then tap **Done** (or **Cancel**).
- Tap a **group** to open it: see [Groups](#groups).

### Duplicate, move or delete a block

**Touch and hold** a block:

| Action | What it does |
|---|---|
| **Duplicate** | Inserts a copy right after the block (a group is copied with its whole content). |
| **Move › Move Up** / **Move Down** | Moves the block one place up or down. |
| **Move › Into a Group** | Lists the groups of the same list: choose one to put the block at the end of that group. |
| **Move › Out of “Group name”** | Only inside a group: takes the block out and places it right after the group, one level up. |
| **Delete** | Removes the block (and, for a group, everything inside). |

## Groups

A **group** is a list of blocks played several times in a row. It is how you build intervals, circuits and sets.

1. Add a **Group of Blocks**, give it a name (for example *Circuit A*) and a number of **Rounds**, then tap **Add**.
2. Tap the group in the list to **open** it. Its own page shows:
   - the **Group** name and the **Rounds** stepper (×1 to ×99), with the **total with N rounds** below;
   - its **Blocks**, with the duration of **One round** in the footer.
3. Add exercises, rests or other groups inside, exactly like at the top level.
4. Go back with the back button. Changes inside a group are part of the workout: they are saved when you tap **Save** or **Create** in the editor.

### Nested groups

A group can contain other groups, at any depth. The **Double Tabata** template is an example:

```
Blocks ×2
├─ Tabata ×8
│   ├─ Work 20 s
│   └─ Rest 10 s
└─ Block rest 60 s
```

The timer plays: 8 × (Work, Rest), then Block rest, then again 8 × (Work, Rest), then Block rest. During the workout, the timer shows where you are in every group (*Blocks 2/2*, *Tabata 5/8*).

### How long is a group?

`rounds × (sum of the blocks inside)`. In the example above: one *Tabata* = 8 × 30 s = 4 min; one round of *Blocks* = 4 min + 60 s = 5 min; the whole group = 2 × 5 min = **10 min**.

## How the timer reads your workout

When you start a workout, the timer turns the blocks into a flat list of **steps**:

- A **Get Ready** step of **10 seconds** is always added at the beginning.
- Each exercise and each rest becomes one step.
- Groups are unrolled round after round.
- Blocks lasting **0 seconds** are skipped, and empty groups produce nothing.
- A workout whose total duration is 0 can't be started.

Example: *Warm-up 2 min* followed by a group *Circuit ×2: Squats 40 s, Rest 20 s* gives 6 steps: Get Ready, Warm-up, Squats, Rest, Squats, Rest.

See [Running a Workout](timer.html) for the timer itself.

## Without Pro

Without Pro you can still:

- create workouts from **templates** and **with AI**;
- **rename**, **duplicate**, **move**, **delete** and **start** any workout.

Creating from scratch and changing the blocks of a workout require [Workout Planner Pro](pro.html). Your workouts never disappear if Pro ends: you just can't edit them anymore.
