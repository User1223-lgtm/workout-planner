---
layout: default
title: Import, Export & File Format
description: Export Workout Planner workouts and folders as JSON library files, import them on another device, and the complete reference of the format.
---

# Import, Export & File Format

<p class="lead">Share workouts as small <code>.json</code> files, move your library to a new device, or write workouts yourself.</p>

<div class="toc" markdown="1">
On this page

* TOC
{:toc}
</div>

<blockquote class="pro-note" markdown="1">

Import and export are part of [Workout Planner Pro](pro.html). Without Pro, these actions show a crown and open the Pro screen.

</blockquote>

## Export

There is **one file format**, whatever you export: the **library**. A library contains folders and workouts, and keeps the folder tree. Exporting one workout simply gives a library that contains only this workout.

| What you export | How | The library contains | File name |
|---|---|---|---|
| One workout | Workout page › **⋯ › Export Workout**, or touch and hold it › **Export Workout** | This workout | `Workout name.json` |
| One folder | Touch and hold it › **Export Folder**, or open it › **⋯ › Export Folder** | This folder, with everything inside | `Folder name.json` |
| Several items | **⋯ › Select**, select items, **⋯ › Export Data** | The selected folders and workouts | `Workout Planner (5 items).json` |

The iOS **share sheet** opens: send the file with **AirDrop**, **Messages**, **Mail**, or save it with **Save to Files** (iCloud Drive, On My iPhone…).

- Folders and workouts are written in alphabetical order.
- Characters not allowed in file names (`/ \ : ? % * | " < >`) are replaced by `-`.

> Your **history** (Me tab) is not part of the exports: only folders and workouts are.

## Import

1. Open the folder where you want the imported items.
2. Tap **⋯ › Import Data**.
3. Choose one or more `.json` files (you can select several at once in the Files picker).

The content of the library is added **inside the folder you are in**: an exported workout comes back as a workout, an exported folder as a folder. The files can come from Workout Planner, or be [written by hand](#write-your-own-files).

### What happens during an import

- **Nothing is replaced.** Imported items are always added.
- If a name is already used in the destination, a number is added: *Leg Day* becomes *Leg Day 2* (then *Leg Day 3*…).
- A workout without a name takes the **name of the file**. A folder without a name is called **Imported Folder**.
- Only **libraries** can be imported.
- If a file isn't in the right format, the other files are still imported, and an **Import Failed** alert lists the refused files: *“my file.json”: This file doesn't have the right format.*

## Move your library to a new device

1. On the old device, at the root of **My Workouts**: **⋯ › Select › Select All**, then **⋯ › Export Data**, and **Save to Files** (for example in iCloud Drive) or send it with AirDrop.
2. On the new device: **⋯ › Import Data** and choose the file.

Both devices need Pro (Pro is linked to your Apple Account, so it is available on all your devices: see [Restore purchases](pro.html#restore-purchases)).

## Example file

Download [example-workouts.json](downloads/example-workouts.json): 11 ready-to-use workouts in 4 folders.

| Folder | Workouts |
|---|---|
| HIIT & Cardio | Tabata Burner, HIIT 20, EMOM 12 |
| Strength | Upper Body Push, Leg Day, Core Crusher |
| Combat Sports | Boxing Rounds |
| Mobility & Yoga | Morning Mobility, Evening Yoga Flow |
| *(root)* | 7-Minute Workout, Running Intervals |

## The file format

Files are plain **JSON** (UTF-8). All **durations are in seconds**. Every file is a **library**: it's the only format the app exports and imports.

### A library

```json
{
  "format": "workout-planner",
  "folders": [
    {
      "name": "Strength",
      "folders": [
        { "name": "Week 1", "folders": [], "workouts": [ { "name": "Leg Day", "blocks": [] } ] }
      ],
      "workouts": [
        { "name": "Core Crusher", "description": "", "blocks": [] }
      ]
    }
  ],
  "workouts": [
    { "name": "7-Minute Workout", "description": "", "blocks": [] }
  ]
}
```

| Key | Type | Required | Meaning |
|---|---|---|---|
| `format` | text | no | Always `"workout-planner"` in exported files. Ignored when importing. |
| `folders` | list of [folders](#a-folder) | at least one of the two | Folders to create in the current folder. |
| `workouts` | list of [workouts](#a-workout) | at least one of the two | Workouts to create in the current folder. |

The export of one workout looks like this:

```json
{
  "format": "workout-planner",
  "folders": [],
  "workouts": [
    { "name": "Tabata Burner", "description": "A short and intense Tabata session.", "blocks": [ ... ] }
  ]
}
```

### A folder

```json
{ "name": "Strength", "folders": [ ... ], "workouts": [ ... ] }
```

| Key | Type | Default | Meaning |
|---|---|---|---|
| `name` | text | `Imported Folder` | Name of the folder. |
| `folders` | list of folders | `[]` | Its sub-folders. |
| `workouts` | list of [workouts](#a-workout) | `[]` | Its workouts. |

### A workout

```json
{
  "name": "Tabata Burner",
  "description": "A short and intense Tabata session.",
  "blocks": [
    { "type": "exercise", "name": "Warm-up", "description": "Easy jog in place", "duration": 120 },
    {
      "type": "group",
      "name": "Tabata",
      "repetitions": 8,
      "blocks": [
        { "type": "exercise", "name": "Burpees", "duration": 20 },
        { "type": "rest", "duration": 10 }
      ]
    },
    { "type": "exercise", "name": "Cool-down", "duration": 120 }
  ]
}
```

| Key | Type | Default | Meaning |
|---|---|---|---|
| `name` | text | file name | Name of the workout. |
| `description` | text | `""` | Description of the workout. |
| `blocks` | list of [blocks](#a-block) | `[]` | The program, in order. |

### A block

```json
{ "type": "exercise", "name": "Push-ups", "description": "Elbows close to the body", "duration": 40 }
{ "type": "rest", "duration": 20 }
{ "type": "group", "name": "Circuit A", "repetitions": 3, "blocks": [ ... ] }
```

| Key | Type | Used by | Default | Meaning |
|---|---|---|---|---|
| `type` | text | all | **required** | `"exercise"`, `"rest"` or `"group"`. Upper or lower case. Any other value is refused. |
| `name` | text | all | `""` | Name of the exercise, rest or group. An empty exercise name is allowed in files, but the editor will ask for one. |
| `description` | text | exercise | `""` | Coaching cue shown under the name on the timer. |
| `duration` | number | exercise, rest | `0` | Seconds. Decimals are rounded (`30.4` → `30`). Negative values become `0`. A block of 0 seconds is skipped by the timer. |
| `repetitions` | number | group | `1` | Number of rounds, kept between **1 and 99**. |
| `blocks` | list of blocks | group | `[]` | Content of the group. Groups can be nested. |

Keys that don't apply to a type are ignored (for example `duration` on a group). Unknown keys are ignored.

## Write your own files

You can write workouts in any text editor, or ask a chatbot to write a file in this format, then import it. A few rules:

- The file must be a [library](#a-library): put your workouts inside `{ "workouts": [ … ] }`, even if there is only one.
- Use straight quotes `"`, not curly quotes `“ ”`.
- No comma after the last item of a list or object.
- Every block needs a `type`.
- Durations in **seconds**: 1 min 30 s = `90`.
- Save the file with the `.json` extension (for example in the Files app, in iCloud Drive).

### Import errors

When a file is refused, the app shows *This file doesn't have the right format.* Check the rules above: the file must be a library (`folders` and/or `workouts`), be valid JSON, and every block needs a known `type`.
