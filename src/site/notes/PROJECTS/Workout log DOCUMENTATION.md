---
{"dg-publish":true,"permalink":"/projects/workout-log-documentation/","tags":["portfolio","code","Projects","Obsidian"],"noteIcon":""}
---

# WORKOUT LOG DOCUMENTATION IN OBSIDIAN
#### Uses the following plugins:
BUTTONS
DATAVIEW
QUICKADD
HEATMAP


## PLAN
- Cut 250 calories a day for 1/2 lb a week
- Cut 500 calories a day  total for 1 lb a week

3500 calories / 7 days a week = 500 calories a day reduction

| Weight (lbs) | Weight (kg) | Height (in) | Height (m) | MPH | MPS  |
| ------------ | ----------- | ----------- | ---------- | --- | ---- |
| 120          | 63.49       | 62          | 1.57       | 3   | 1.34 |

---
## Pages / Structure
### [[TEMPLATES/Workout Template\|Workout Template]] (TEMPLATES/Workout Template)

![[Workout_Template.txt]]

---------------
### [[TRACK/Daily Workout Log\|Daily Workout Log]] (TRACK/Daily Workout Log)


![[Daily Workout Log--TEXT.txt]]


--------------
#### Other notes added to: 
##### Daily notes
[[TEMPLATES/Daily\|Daily]]
##### Weekly notes
[[TEMPLATES/Weekly\|Weekly]]
##### FITNESS folder (FITNESS/LOGS/</Workout Template goes here/>)

## Necessary tools:
### 1) Button plugin setup 
```text
```button
name Add Exercise
type command
action QuickAdd: Add Exercise
color blue
```{ #button-8s0k}


### 2) dataviewjs
#### Workout Details for Week
```text
# Workout Details for the Week of 2024-03-17
//display only the workouts where `date_created` falls within the Sunday to Saturday range of the week of `date_of_workout`
// pulls frontmatter from page
function getStartOfWeek(date) {
    const dayOfWeek = date.getDay();
    const startOfWeek = new Date(date);
    startOfWeek.setDate(date.getDate() - dayOfWeek);
    return startOfWeek;
}

let startOfWeekDateCreated = new Date(dv.current().date_created); // Convert date_created to a Date object
startOfWeekDateCreated = getStartOfWeek(startOfWeekDateCreated); // Get the start of the week for date_created

let pages = dv.pages("#workouts")
              .where(b => {
                const startOfWeekDateWorkout = getStartOfWeek(new Date(b.date_of_workout));
                const sundayDateWorkout = new Date(startOfWeekDateWorkout);
                sundayDateWorkout.setDate(startOfWeekDateWorkout.getDate() + 6);

                return startOfWeekDateCreated >= startOfWeekDateWorkout && startOfWeekDateCreated <= sundayDateWorkout;
              }) // Filter workouts based on the week range
              .groupBy(b => b.date_of_workout); // Group by date_of_workout

for (let group of pages.sort(d => d.key, 'desc')) { 
    dv.header(6, group.key);
    dv.table(["File", "Exercise", "Weight_lbs", "Height_in", "MPH", "Duration_min", "Distance_mi"], 
        group.rows
            .sort(k => k.exercise, 'asc')
            .map(k => [k.file.link, k["exercise"], k["Weight_lbs"], k["Height_in"], k["MPH"], k["Duration_min"],k["Distance_mi"]]))
}
````

#### Workout Details for Week -- old
```text

# Workout Details for the Week of 2024-03-17


### 3) dataview
#### Workout Totals for Week
```text
# Workout Totals for Week of 2024-03-17
| File | Date | Miles | Minutes | lbs | kgs | MPH | mps | Rate | Cal_Burned |
| ---- | ---- | ----- | ------- | --- | --- | --- | --- | ---- | ---------- |

{ .block-language-dataview}

#### Total Calories Burned for Week
```text
# Total Calories Burned for Week of 2024-03-17
| Total Weekly Calories Burned | Left for 1 Pound | % Burned |
| ---------------------------- | ---------------- | -------- |

{ .block-language-dataview}

#### Workout Totals for Year
```text 
# Workout Totals for 2024

| File                                                             | Date       | Miles | Minutes | lbs   | kgs   | MPH | mps  | Rate | Calories Burned |
| ---------------------------------------------------------------- | ---------- | ----- | ------- | ----- | ----- | --- | ---- | ---- | --------------- |
| [[FITNESS/LOGS/2024-02-09 With twins\|2024-02-09 With twins]] | 2024-02-09 | 0.77  | 19      | 138.6 | 62.86 | 2.4 | 1.07 | 3.53 | 67.11           |
| [[FITNESS/LOGS/2024-01-14 1st\|2024-01-14 1st]]               | 2024-01-14 | 1     | 30      | 138.9 | 62.99 | 3   | 1.34 | 4.29 | 128.73          |

{ .block-language-dataview}

#### Workout Stats for Year
```text
# Workout Stats for 2024 (Weight)
| Workouts | TotalW | AvgW   | MinW  | MaxW  |
| -------- | ------ | ------ | ----- | ----- |
| 2        | 277.5  | 138.75 | 138.6 | 138.9 |

{ .block-language-dataview}


### 4) **Quick add Plugin 
#### Setup -- FILE NAME: change to FITNESS/LOGS/{{DATE}} {{VALUE}}**

![Pasted image 20240214094250.png|500](/img/user/vault/attachments/Pasted%20image%2020240214094250.png)

### 5) Heatmap Calendar
```text
<span><span><strong>🏋️ Workouts 🏋️</strong></span></span><div class="heatmap-calendar-graph"><div class="heatmap-calendar-year">24</div><ul class="heatmap-calendar-months"><li>Jan</li><li>Feb</li><li>Mar</li><li>Apr</li><li>May</li><li>Jun</li><li>Jul</li><li>Aug</li><li>Sep</li><li>Oct</li><li>Nov</li><li>Dec</li></ul><ul class="heatmap-calendar-days"><li>Mon</li><li>Tue</li><li>Wed</li><li>Thu</li><li>Fri</li><li>Sat</li><li>Sun</li></ul><ul class="heatmap-calendar-boxes"><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="hasData" style="background-color: hsl(13, 100%, 60%);" data-date="2024-01-14"><span class="heatmap-calendar-content"><span><span><a data-tooltip-position="top" aria-label="2024-01-14 1st" data-href="2024-01-14 1st" href="2024-01-14 1st" class="internal-link" target="_blank" rel="noopener"></a></span></span></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="hasData" style="background-color: hsl(13, 100%, 50%);" data-date="2024-02-09"><span class="heatmap-calendar-content"><span><span><a data-tooltip-position="top" aria-label="2024-02-09 With twins" data-href="2024-02-09 With twins" href="2024-02-09 With twins" class="internal-link" target="_blank" rel="noopener"></a></span></span></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="today isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li><li class="isEmpty"><span class="heatmap-calendar-content"></span></li></ul></div>
```
```

#### heatmap calendar fix-- the code needed to make hover work
```text
const extractedDateFromFile = page.file.name.split(" ")[0] // code needed to extract date from title
```

---
## TODO

- [x] workout totals by week, add up total calories burned (-3500 to equal 1 lb) 🛫 2024-01-17 ✅ 2024-02-03
- [x] Fix Heatmaps? Need more data? Date issue -->  ~~page.file.frontmatter.date_of_workout~~ ✅ 2024-01-21 
	- [x] https://blacksmithgu.github.io/obsidian-dataview/annotation/metadata-page ✅ 2024-02-03
	- [x] https://github.com/Richardsl/heatmap-calendar-obsidian/issues/38s/ ✅ 2024-02-03 - this is the fix!
- [x] research [[BMR Calculator]] ✅ 2024-02-06
- [x] https://forum.obsidian.md/t/dataview-multiply-two-fields-within-a-file-then-get-the-sum-for-all-files/49354 ✅ 2024-02-03
- [x] https://forum.obsidian.md/t/sum-the-integer-in-yaml-tag-within-two-files-into-dataview-table/61128 ✅ 2024-02-03
- [x] https://forum.obsidian.md/t/dataview-start-of-week/38746 date(sow) date(eow) ✅ 2024-02-03
- [x] https://forum.obsidian.md/t/summarizing-calculated-values/61675/2 sum(map, (r)) ✅ 2024-02-03

## NOTES
- [x] Error in how Week Numbers are processed - Start of week defaults to Monday, not Sunday https://github.com/liamcain/obsidian-periodic-notes/issues/95 ; https://github.com/liamcain/obsidian-calendar-plugin/issues/222 ; https://github.com/liamcain/obsidian-calendar-ui/blob/master/src/utils.ts#L42 ✅ 2024-02-05
- [x] Change to ISO WW https://github.com/liamcain/obsidian-periodic-notes/issues/55 ; https://github.com/liamcain/obsidian-periodic-notes/issues/17 ✅ 2024-02-09
- [x] fix daily workout log to show all workouts within that week (week number?) 🛫 2024-02-06 ✅ 2024-02-09
	- [x] added property weekNum --> 06 ✅ 2024-02-09
	- [x] ``=dateformat(this.date_of_workout,"W")` ✅ 2024-02-09
	- [x] WHERE dateformat(date_of_workout,"W") = weekNum ✅ 2024-02-09
	- [x] https://forum.obsidian.md/t/dataview-periodic-notes-render-different-week-numbers/49452 ✅ 2024-02-09
- [x] add different types of workouts? v2.0, if other types of workout that are measurable ✅ 2024-02-09
- [x] hhttps://forum.obsidian.md/t/show-all-notes-for-a-given-week/39052ttps://forum.obsidian.md/t/show-all-notes-for-a-given-week/39052 ✅ 2024-02-09
- [x] >date(file.name).year = <% tp.date.now("YYYY")%> AND date(file.name).weekyear = <% tp.date.now("ww")%>-1 ✅ 2024-02-09

---
## References & Inspiration
1) https://www.youtube.com/watch?v=KXtrzfJ-_IM; https://github.com/BugBoysWorld/obsidian-workout-log
2) [Calories burned per minute = (0.035 X body weight in kg) + ((Velocity in m/s ^ 2) / Height in m)) X (0.029) X (body weight in kg)](https://www.womanandhome.com/health-wellbeing/fitness/calories-burned-walking/)
3) THE MATH:
```mathpad
(0.035*63.49)+((1.34^2)/(1.57))*(0.029)*(63.49)
```


