---
{"dg-publish":true,"permalink":"/projects/archive-ics-to-csv-to-md/","tags":["Portfolio","code","Projects","Python"],"created":"2024-01-08T17:31:00","updated":"2024-03-23T09:40:00"}
---

[[DO LIST/Archived calendars to obsidian\|Archived calendars to obsidian]]

Converting historic calendar events to Full Calendar in Obsidian

## 1. Convert ICS files to CSV
1. Export ICS from from  Calendar app
2. Run convert_ICS 
	1. File will export to: C:/Users/XXXXX/OneDrive/xfer/CALENDARS/COMPLETE
## 2. Run convert_ics code

```python
pip install icalendar

from datetime import datetime
import csv
import os
import sys
from icalendar import Calendar

current_directory = os.getcwd()
print(current_directory)

# Path to the .ics file
FILE_NAME = "COURSES"
ics_file_path = f'{FILE_NAME}.ics'

# Create a new CSV file
csv_file_path = f'{FILE_NAME}.csv'
csv_file = open(csv_file_path, 'w', newline='', encoding='utf-8')

# Write the CSV header
csv_writer = csv.writer(csv_file)
csv_writer.writerow(['Subject', 'Start Time', 'End Time', 'Description','Location'])

# Read the iCalendar file
with open(f'C:/Users/XXXXX/OneDrive/xfer/CALENDARS/COMPLETE/ICS/{FILE_NAME}.ics', 'rb') as ics_file:
    cal = Calendar.from_ical(ics_file.read())
    for event in cal.walk('VEVENT'):
        subject = event['SUMMARY']
        start_time = event['DTSTART'].dt
        end_time = event['DTEND'].dt
        description = event['DESCRIPTION']
        location = event['LOCATION']
        csv_writer.writerow([subject, start_time, end_time, description, location])

# Close the CSV file
csv_file.close()
```


## 3. Clean csv output (power query)
1) Check errors (try --> HasError = "True") --> automated power query file in /COMPLETE/WORKING_XLSX/
2) Replace value for TimeZone Start time and End time (-04:00 --> +00:00) or (-05:00 --> +00:00)
	1) Duplicate Start Time and End Time
	2) Split Start Time/End Time into START_DATE/START_TIME (Date Type) and END_DATE/END_TIME (time type)
3) Export new csv file (for example, PSF2.csv)

## 4. Convert CSV to MD --> Run CSV2MD code
```python
#FIELDS: Index, Subject, START_DATE, START_TIME, END_DATE, END_TIME, Description, Location
import pandas as pd
#from datetime import datetime
import datetime as dt
from datetime import datetime,date

CAL_NAME="DSF"
tag_name="\n- '#Nico'"  #How to export multiple tags? another \n?

data = pd.read_csv(f'C:/Users/XXXXX/OneDrive/xfer/CALENDARS/COMPLETE/CSV/{CAL_NAME}2.csv', delimiter=',')

files = data.values.tolist()

for file in files:
    index = file[0]
    subject = file[1]
    start_date = pd.to_datetime(file[2]).strftime("%Y-%m-%d")
    start_time = pd.to_datetime(file[3]).strftime("%H:%M")
    end_date = pd.to_datetime(file[4]).strftime("%Y-%m-%d")
    end_time = pd.to_datetime(file[5]).strftime("%H:%M")
    description = file[6]
    location = file[7]
    file_name = f'C:/Users/XXXXX/OneDrive/xfer/CALENDARS/COMPLETE/CSV/{CAL_NAME}/{start_date}_{index}_{CAL_NAME}.md'
    with open(file_name, 'w', encoding='utf-8') as f:
        f.write(f'---\ntitle: {subject}\ndate: {start_date}\nstartTime: {start_time}\ncompleted: {end_date}\nendTime: {end_time}\ntags:{tag_name}\n---\nIndex: {index}_{CAL_NAME}\nDescription: {description}\nLocation: {location}\n')
        f.close()
print(f'{file_name} saved.')
```









