# Details of the report
# Data:
  *	The dataset comprises of date range for the year 2019 and 2020
  *	After importing the Excel file into Power BI, performed the cleansing of data in Power Query Editor and created data model as follows

# Data Model:
  * Imported [Optical Data Set.xlsx] as a staging query, and created references in new [Data Model] group for [Patients], [Opticians], [Appointments]
     1.	[Patients] table:
        * Removed duplicates
        * Calculated Age of the patients from [DOB] column
        * Added custom column for [Next Appointment Date] using the age logic, [Status] for Today, Scheduled or Overdue to make a slicer, [Days Overdue]
     2. [Opticians] table
        * Merged first and last name columns; to combine first name and last name
     3. added [Dates] table using M Code;
        * marked as Date table
            * used parameter to get and set start date to Jan 1 of first appointment year
            * used parameter to get and set end date to Dec 31 of the year after this year
      4. added [Periods] table using Period Table M Code (Dynamic Date Range Slicer- Query M); adjusted for “current”, "today", "yesterday" and “previous” periods (week, month,  year)
      5. The raw data in Excel looks like the following:
          ![](https://github.com/nancy-gl/Optical_patients_report/blob/main/images/Excel%20Raw%20Data.png)
      6. The Power BI model looks like the following:
          ![](https://github.com/nancy-gl/Optical_patients_report/blob/main/images/Data%20Model.png)
      
# Visuals:
* Created report pages for [Overview], [Appointment Center], and [Patient Detail].
   1. [Overview] page
       * hid all pages except for [Overview] page 
       * added buttons for page navigation to [Appointment Center] report page
       * added card visuals to show some KPIs for appointments 
       * added a bar chart to show the distribution of patient traffic in the months
       * added Date slicer to enable to see particular date range  
       * The report page looks like the following:
       
        ![](https://github.com/nancy-gl/Optical_patients_report/blob/main/images/Overview%20page.png)
        
  2. [Appointments Center] page:
        *	used same flow of card and bar chart to follow the overview
        *	used Today’s Date card visual to compare the date from todays date
        *	used Slicer visuals to make selection for Age, Patient Name, Opticians and Period
        *	used Chiclet Slicer custom visual to select Status {Overdue, Scheduled, or Today} of Appointments
        *	used Table visual for the details of the Patient, with the Action for the reminder
        *	added button to select a patient from the table to drill through the detail for the same
        *	added a Home Button to go back to the Overview page

        ![](https://github.com/nancy-gl/Optical_patients_report/blob/main/images/Appointment%20Center.png)
        
        * drill-through can also be achieved by right clicking on the rows on the Table visual as shown

        ![](https://github.com/nancy-gl/Optical_patients_report/blob/main/images/Appointment%20Center%20drill-through.png)

  3. [Patient Detail] page:
        *	used this page as a drill-through page to see the details for patients’ eye measurement 
        *	used Card visuals to highlight the Appointment Details, and a multi-row card to display the personal information for the selected patient
        *	set “Patient Name as” drill-through target
        *	used line chart to see the trend and change in patient eye measurement value till date
        *	used Table visual to present patient’s appointment history, using data bars to represent a change in left or right eye measurement from the previous appointment
        *	added a Home Button to go back to previous page

        ![](https://github.com/nancy-gl/Optical_patients_report/blob/main/images/Patient%20page.png)
