---
layout: default
title: Import, Export & File Format
description: Export Workout Planner workouts and folders as JSON files, import them on another device, and the complete reference of the workout-planner JSON format.
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

| What | How | File name |
|---|---|---|
| One workout | Workout page › **⋯ › Export Workout**, or touch and hold it › **Export Workout** | `Workout name.json` |
| One folder (with everything inside) | Touch and hold it › **Export Folder**, or open it › **⋯ › Export Folder** | `Folder name.json` |
| Several items | **⋯ › Select**, select items, **⋯ › Export Data** | `Workout Planner (5 items).json` |

The iOS **share sheet** opens: send the file with **AirDrop**, **Messages**, **Mail**, or save it with **Save to Files** (iCloud Drive, On My iPhone…).

- A single workout is saved in the [workout format](#a-workout). Folders and selections are saved in the [library format](#a-library), which keeps the folder tree.
- Folders and workouts are written in alphabetical order.
- Characters not allowed in file names (`/ \ : ? % * | " < >`) are replaced by `-`.

> Your **history** (Me tab) is not part of the exports: only folders and workouts are.

## Import

1. Open the folder where you want the imported items.
2. Tap **⋯ › Import Data**.
3. Choose one or more `.json` files (you can select several at once in the Files picker).

Everything is added **inside the folder you are in**. The files can come from Workout Planner, or be [written by hand](#write-your-own-files).

### What happens during an import

- A file can contain **one workout**, **a list of workouts**, or a **library** of folders and workouts. The app detects which one.
- **Nothing is replaced.** Imported items are always added.
- If a name is already used in the destination, a number is added: *Leg Day* becomes *Leg Day 2* (then *Leg Day 3*…).
- A workout without a name takes the **name of the file**. A folder without a name is called **Imported Folder**.
- If a file can't be read, the other files are still imported, and an **Import Failed** alert lists the problem of each failed file, for example *“my file.json”: Missing key “type” at “blocks.[2]”.*

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

Files are plain **JSON** (UTF-8). All **durations are in seconds**.

### A workout

```json
{
  "format": "workout-planner",
  "version": 1,
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

| Key | Type | Required | Default | Meaning |
|---|---|---|---|---|
| `format` | text | no | – | Always `"workout-planner"` in exported files. Ignored when importing. |
| `version` | number | no | – | Always `1` in exported files. Ignored when importing. |
| `name` | text | no | file name | Name of the workout. |
| `description` | text | no | `""` | Description of the workout. |
| `blocks` | list of [blocks](#a-block) | no | `[]` | The program, in order. |

### A block

```json
{ "type": "exercise", "name": "Push-ups", "description": "Elbows close to the body", "duration": 40 }
{ "type": "rest", "duration": 20 }
{ "type": "group", "name": "Circuit A", "repetitions": 3, "blocks": [ ... ] }
```

| Key | Type | Used by | Default | Meaning |
|---|---|---|---|---|
| `type` | text | all | **required** | `"exercise"`, `"rest"` or `"group"`. Upper or lower case. `"loop"` is accepted as another word for `"group"`. |
| `name` | text | all | `""` | Name of the exercise, rest or group. An empty exercise name is allowed in files, but the editor will ask for one. |
| `description` | text | exercise | `""` | Coaching cue shown under the name on the timer. |
| `duration` | number | exercise, rest | `0` | Seconds. Decimals are rounded (`30.4` → `30`). Negative values become `0`. A block of 0 seconds is skipped by the timer. |
| `repetitions` | number | group | `1` | Number of rounds, kept between **1 and 99**. |
| `blocks` | list of blocks | group | `[]` | Content of the group. Groups can be nested. |

Keys that don't apply to a type are ignored (for example `duration` on a group). Unknown keys are ignored.

### A list of workouts

A file can also contain several workouts at the top level, as a JSON array:

```json
[
  { "name": "Morning", "blocks": [ { "type": "exercise", "name": "Jumping Jacks", "duration": 60 } ] },
  { "name": "Evening", "blocks": [ { "type": "exercise", "name": "Stretching", "duration": 300 } ] }
]
```

They are all imported into the current folder.

### A library

Folders and selections are exported as a library. It keeps the folder tree:

```json
{
  "format": "workout-planner",
  "version": 1,
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

| Key | Type | Meaning |
|---|---|---|
| `folders` | list of folders | Folders to create in the current folder. |
| `workouts` | list of [workouts](#a-workout) | Workouts to create in the current folder. |

A **folder** has a `name`, its own `folders` (sub-folders) and its own `workouts`. All three are optional.

### How the app recognizes the content

1. If the file starts with `[`, it is a **list of workouts**.
2. Otherwise, if the object has `folders` or `workouts` and **no** `blocks`, it is a **library**.
3. Otherwise, it is **one workout**.

## Write your own files

You can write workouts in any text editor, or ask a chatbot to write a file in this format, then import it. A few rules:

- Use straight quotes `"`, not curly quotes `“ ”`.
- No comma after the last item of a list or object.
- Every block needs a `type`.
- Durations in **seconds**: 1 min 30 s = `90`.
- Save the file with the `.json` extension (for example in the Files app, in iCloud Drive).

### Import errors

| Error | Cause |
|---|---|
| *Unknown block type “…”. Use “exercise”, “rest” or “group”.* | A `type` has another value. |
| *Missing key “type” at “blocks.[2]”.* | A block has no `type`. The position shows where: here the 3rd block of the workout (counting starts at 0). |
| *Wrong value at “blocks.[0].duration”: Expected to decode Double but found a string instead.* | A value has the wrong type, for example `"duration": "30"` (text) instead of `30` (number). |
| *The given data was not valid JSON.* | The file isn't valid JSON: a missing comma or bracket, a comma after the last item, curly quotes… |
