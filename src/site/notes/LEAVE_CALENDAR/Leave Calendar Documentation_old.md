---
{"dg-publish":true,"permalink":"/leave-calendar/leave-calendar-documentation-old/","tags":["Projects"],"noteIcon":"","created":"2025-01-04 4:29:00 pm","updated":"2025-01-04 4:32:54 pm"}
---

[[LEAVE_CALENDAR/Leave Details\|LEAVE DETAILS]]

[[LEAVE_CALENDAR/LEAVE LIST\|LEAVE LIST]]

### This project was heavily influenced by ChatGPT, and a LOT (a LOT) of back and forth!!!
### Plugins needed

- Dataview
- Buttons
- QuickAdd
- Templater
### Overview

This JavaScript code generates a leave calendar that tracks and displays sick, annual, and personal leave over a specified date range. The calendar also takes into account holidays and leave requests.

This version of the code assumes the following:

- Pay Period Start Date is 9/20/2024
- Annual Leave is accrued at the rate of 4.6 hours every 14 days after Pay Period Start Date
- Sick Leave is accrued at the rate of 2.7 hours every 14 days after Pay Period Start Date
- Person Leave is accrued at the rate of 8 hours every year, beginning on the first of the year, only to be used once
- Max Annual Leave is 200 hours
- Max Sick Leave is 56 hours
- I assume these [[LEAVE_CALENDAR/Leave_Requests/Holidays\|Holidays]]

### File Structure

The system relies on the following folder and file structure:

```bash
LEAVE_CALENDAR/
├── Leave Calendar.md             # Main page containing the leave calendar
├── Leave Details                 # Folder containing detailed leave information (if needed)
├── UPGRADES                      # For testing and new features (optional)
├── Leave_Requests/
│   ├── Holidays.md              # A markdown file containing the list of holidays
│   ├── <date>.md                # Markdown files for each leave request, named by date (e.g., 2024-01-01.md)
└── TEMPLATES/
    └── LEAVE_REQUEST             # Template for creating new leave requests
```


### Key Sections

1. **Loading the Holidays**
    
    - The code loads a list of holidays from the `LEAVE_CALENDAR/Leave_Requests/Holidays.md` file. The holidays are identified by dates in the `YYYY-MM-DD` format.
    
```javascript
`const holidayPage = dv.pages('"LEAVE_CALENDAR/Leave_Requests/Holidays.md"');`
```
    
    
    - **What to modify:**  
        If your holiday data is stored in a different file, update the path to the appropriate markdown file.
2. **Accrual Rates and Maximum Balances**
    
    - The accrual rates specify how much leave (sick, annual, and personal) is earned per pay period (14 days).
    - The maximum balances define the cap on how much sick and annual leave can be accumulated.
    
```javascript
    const accrualRates = {     
    sick: 2.7, // Sick leave accrues 2.7 hours per pay period     
    annual: 4.6, // Annual leave accrues 4.6 hours per pay period     
    personal: 8 // Personal leave: 8 hours per year };`
```
    
    - **What to modify:**
        - Change the `sick`, `annual`, and `personal` values to adjust the leave accrual rates.
        - Modify `maxSickBalance` and `maxAnnualBalance` to set the maximum leave balances.
3. **Pay Period Configuration**
    
    - The first pay period start date is set to `September 20, 2024`, and the pay period length is 14 days.

```javascript
    const firstPayPeriodStart = new Date(2024, 8, 20); // First pay period: September 20, 2024
const payPeriodLength = 14; // 14 days per pay period
```
    
    - **What to modify:**
        - Change `firstPayPeriodStart` to the start date of your first pay period.
        - Adjust `payPeriodLength` if your pay periods are different.
          
4. **Date Helper Functions**
    
    - Several helper functions handle date operations like formatting and adding days.
    
```javascript
    function toISODateString(date) {
    return date.toISOString().split("T")[0];
}

function addDays(date, days) {
    const result = new Date(date);
    result.setDate(result.getDate() + days);
    return result;
}

function formatDate(date) {
    return new Intl.DateTimeFormat("en-US", {
        month: "2-digit",
        day: "2-digit",
        year: "numeric"
    }).format(date);
}
```
    
    - **What to modify:**  
        These functions handle date formatting and manipulation. If you need different date formats or other operations, modify these functions.
        
5. **Leave Request Parsing**
    
    - The code fetches leave requests from the `LEAVE_CALENDAR/Leave_Requests` folder and processes them. Each leave request is stored in a markdown file named by the date of the request (e.g., `2024-01-01.md`).
    
```javascript
const leaveRequests = dv.pages('"LEAVE_CALENDAR/Leave_Requests"')
    .where(p => p.date && new Date(p.date) >= firstPayPeriodStart); 
```
    
    - **What to modify:**  
        Ensure the path (`"LEAVE_CALENDAR/Leave_Requests"`) matches where your leave requests are stored. Each leave request file should contain a `date` field, which is used to track the leave.
6. **Render Calendar**
    
    - The `renderCalendar` function generates the table, calculating balances and leave usage for each day in the specified date range.
    
```javascript
    function renderCalendar(start, end, events) {
    // Logic to render the leave calendar
}
```
    
    - **What to modify:**  
        You can adjust how the calendar is rendered, including adding more details or changing the layout.
7. **Table Start and End Dates**
    
    - The `tableStartDate` is the date from which the calendar begins. The `tableEndDate` is calculated to be 3 months after the `tableStartDate`.
    
```javascript
    const tableStartDate = new Date(); // This will get the current date and time
const tableEndDate = new Date();
tableEndDate.setMonth(tableEndDate.getMonth() + 3); // Adds 3 months to today's date

```
    
    - **What to modify:**
        - Set `tableStartDate` to the desired start date for the calendar (e.g., `new Date(2024, 8, 9)`).
        - Adjust the `tableEndDate` calculation to reflect a different duration. For example, to add 6 months, change `setMonth(tableEndDate.getMonth() + 3)` to `setMonth(tableEndDate.getMonth() + 6)`.
          
8. **Rendering the Table**
    
    - The `dv.table` function generates the calendar table using the start and end dates.
    
```javascript
    dv.table(
    ["Date", "Leave Type", "Hours Taken", "Sick Balance", "Annual Balance", "Personal Balance", "Color"],
    renderCalendar(tableStartDate, tableEndDate, events)
);

```
    
    - **What to modify:**  
        If you want to change the columns displayed in the table, modify the array `["Date", "Leave Type", "Hours Taken", "Sick Balance", "Annual Balance", "Personal Balance", "Color"]` to match the desired headers.

---

### How to Adjust Dates

1. **Set the Start Date for the Calendar:**
    
    - Find the line:
        
```javascript
   const tableStartDate = new Date();
```
        
    - Modify this line to set a specific start date, for example:

```javascript
const tableStartDate = new Date(2024, 8, 9); // September 9, 2024
```
	
    
1. **Set the End Date for the Calendar:**
    
    - The end date is calculated based on the start date:
        
```javascript
        tableEndDate.setMonth(tableEndDate.getMonth() + 3); // Adds 3 months to today's date
```
        
    - If you want the calendar to end 6 months after the start date, change it to:
        
```javascript
tableEndDate.setMonth(tableEndDate.getMonth() + 6); // Adds 6 months
```