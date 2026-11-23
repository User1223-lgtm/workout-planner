---
layout: default
title: History & Statistics
description: The Me tab of Workout Planner — calendar of completed workouts, weekly and monthly charts, averages, totals, sharing your stats and deleting the history.
---

# History & Statistics

<p class="lead">The Me tab keeps every workout you complete, and turns them into a calendar, charts and numbers.</p>

<div class="toc" markdown="1">
On this page

* TOC
{:toc}
</div>

## What is recorded

A workout is recorded when the timer reaches the **end** (or when you skip past the last step). For each completed workout, the app keeps:

| Data | Meaning |
|---|---|
| Workout name | A copy of the name at the time. The history stays even if you later rename or delete the workout. |
| Date and time | When it started and when it finished. |
| **Time** | The real time from start to finish, pauses included. |
| **Planned** | The planned duration of the workout (sum of its blocks). |
| **Exercises** | The number of exercises of the workout (rounds included). |

A workout ended early with **✕ › End Workout** is not recorded. Everything is stored only on your device.

The **Me** tab has two parts, selected at the top: **Workouts** and **Data**.

## Workouts: the calendar

{% include screen.html image="me-workouts.jpg" alt="The calendar of November with completed workouts" caption="Me › Workouts" class="right" %}

- The **month** is shown at the top. Use **‹** and **›** to go to the previous or next month.
- Under the month: the number of workouts and the total time of that month (*9 workouts · 8h 18m 55s*), or *No workout this month*.
- The **calendar** starts on the first day of the week of your region (Monday in France, Sunday in the United States).
- A **green dot** under a day means you completed at least one workout that day. **Today** is circled.
- **Tap a day** to see its workouts below the calendar, with the finish time and three numbers: **Time**, **Planned** and **Exercises**. If you trained twice that day, both are listed. A day without workout says *No workout completed on this day.*

Workouts are placed on the day they **finished**.

## Data: the statistics

{% include screen.html image="me-data.jpg" alt="Charts of the week and the month" caption="Me › Data" class="right" %}

Before your first completed workout, this page says **No Data Yet**.

### This Week and This Month

Two cards, each with **three charts**. Swipe a card sideways (or tap the dots under it) to switch between them:

| Chart | Shows |
|---|---|
| **Workouts** (green) | Number of completed workouts |
| **Training Time** (blue) | Real time spent training |
| **Exercises** (red) | Number of exercises done |

- **This Week**: one bar per day of the current week. The current day is highlighted.
- **This Month**: one bar per week of the current month: *Week 1* = days 1–7, *Week 2* = 8–14, *Week 3* = 15–21, *Week 4* = from the 22nd to the end of the month.

The total of the period is shown at the top right of each chart.

### Averages

| Number | How it is calculated |
|---|---|
| **Average Duration** | Total real time ÷ number of workouts |
| **Average Exercises** | Total exercises ÷ number of workouts |
| **Workouts per Week** | Number of workouts ÷ number of weeks since the week of your first workout (this week included) |
| **Workouts per Month** | Number of workouts ÷ number of months since the month of your first workout (this month included) |

### Totals

**Total Training Time**, **Total Exercises** and **Total Workouts**, since your first workout.

## Share your stats

When you have at least one workout, a **share** button appears at the top right of the **Data** page. Choose **Share My Stats**:

| Choice | Image |
|---|---|
| **This Week** | The three charts of the week |
| **This Month** | The three charts of the month |
| **All Time** | All the averages and totals |

The app draws a dark image (1080 pixels wide, PNG named *My Workout Stats.png*) titled **My Training Stats**, with the app logo and the line *Plan and time your workouts with Workout Planner*, plus a link to the app on the App Store. Then the iOS share sheet opens: Messages, WhatsApp, Instagram, Save Image, AirDrop…

## Delete your history

**Settings › Data › Delete Workout History** deletes every completed workout: the calendar and all the statistics of the Me tab are emptied, and the Stats widget goes back to zero.

- Your **saved workouts are not touched**: only the history is deleted.
- The app asks for a confirmation first. **This can't be undone.**
- The button is greyed out when the history is already empty.

It isn't possible to delete a single entry of the history.

## Widgets

The **Stats** widget shows the same charts and numbers on your Home Screen and Lock Screen. See [Widgets](widgets.html#stats).
