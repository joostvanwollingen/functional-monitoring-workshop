# Tips & Tricks

## Already finished?
Wow! You are fast! If you are done trying and playing with Grafana, take a look at these tips & tricks.
If you created something cool, please show us and share with the audience!

## Dashboard
For a dashboard that is on display 24/7 it is vital to show the most important information first. This should be the key metrics that define the health of the service. Put these on the first row(s) of you dashboard.

Setup your dashboard to refresh automatically every 5 seconds under the time range button in Grafana. For very large dashboards it can help reduce the page load times by collapsing panels you don't need all the time.

## Rotate several tabs
If you have multiple dashboards you want to display you can use a plugin such as [Tab Revolver](https://chrome.google.com/webstore/detail/revolver-tabs/dlknooajieciikpedpldejhhijacnbda) to change the tabs every x seconds.

## Setup alerts to show as a table
By setting up alerts as a table in Grafana you can have an overview of everything that has happened with your service.

## Engineer of the Day on your monitor
Create a "Text" panel and set the mode to HTML. Replace the names in the script below.
```
<div id="sprint" style="margin-top: 3px; padding-top: 3px; color:#00719e; font-size:30pt; text-align: center; font-weight: bold; font-family: 'Cambria', 'Times New Roman', serif;"/>

<div style="margin-top: 0px; text-align: center;" class="panel-title-container drag-handle" panel-menu=""><span class="panel-title drag-handle pointer ng-scope"><span class="panel-title-text drag-handle ng-binding">Engineer on Duty</span><span class="panel-links-icon"></span></span></div>
<div id="eod" style="height:30x; margin-top: 0px; padding-top: 0px; color:#ae5a41; font-size:30pt; text-align: center; font-weight: bold;" />

<script>
 updateSprintAndEOD();

 function updateSprintAndEOD() {
   // weekday :: 1 = Monday;
   // weekday :: 2 = Tuesday;
   // weekday :: 3 = Wednesday;
   // weekday :: 4 = Thursday;
   // weekday :: 5 = Friday;

   var sprintAB = new Array(2);
   sprintAB[0] = "a";
   sprintAB[1] = "b";

   var date = new Date();
   var sprint1 = new Date("2009-01-18");
   var weekday = date.getDay();

   var timeDifference = date.getTime() - sprint1.getTime();
   var sprintCalculation = ( timeDifference / 1000 / 60 / 60 / 24 / 7 / 4 ) + 1;
   var sprintAdditionCalculation = Math.round(sprintCalculation) - Math.floor(sprintCalculation);

   var sprintNo = Math.floor(sprintCalculation);
   var sprintAddition = sprintAB[sprintAdditionCalculation];

   var eodSchedule = new Array(7);
   eodSchedule[0] = new Array("A-sprint", "B-sprint");
   eodSchedule[1] = new Array("Ivo", "Ivo");
   eodSchedule[2] = new Array("Joost", "Joost");
   eodSchedule[3] = new Array("Ivo", "Ivo");
   eodSchedule[4] = new Array("Joost", "Joost");
   eodSchedule[5] = new Array("Ivo", "Ivo");
   eodSchedule[6] = new Array("Operations", "Operations");

   var eod = eodSchedule[weekday][sprintAdditionCalculation];

   document.getElementById("sprint").innerHTML = sprintNo + sprintAddition;
   document.getElementById("eod").innerHTML = eod;

    var everyEightHours = 8 * 60 * 60 * 1000;
    setTimeout("updateSprintAndEOD()", everyEightHours);
 }
</script>
```
You may have to adjust your Grafana settings as described in this [issue](https://github.com/grafana/grafana/issues/15647).
