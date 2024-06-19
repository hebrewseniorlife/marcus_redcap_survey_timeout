# REDCap / Shazam - Survey Idle Timeout
Shazam code and instructions for enabling a survey timeout feature in REDCap using Shazam 

## Purpose
The purpoose of this code is to provide REDCap surveys with an idle timout feature. If a survey is started and abandoned with an open screen ("left idle") the survey will reset after a specified period of time. All partial responses will be cleared. This functionality prevents subsequent device users (e.g. public kiosk, clinic ipads, etc.) from accidentally viewing unfinished surveys. 

A survey is considered idle when no user interaction is detected. This includes screen clicks and page scrolls. The device will render a message when the idle timeout has expired (e.g. 10 minutes of idle time).  The user will not be able to recover the survey once the timeout has executed. By design, no countdown warnings are provided to the user. 

See customization section below.

## Prerequisits
+ REDCap (v14.x.x+)
+ Shazam REDCap Module (v1.3.13+)

## Dependancies (developer notes)
+ Jquery, Bootstrap (see REDCap core)
+ Idle Timer (Javascript Library)
  + https://github.com/thorst/jquery-idletimer

## Installation Instructions
1. Install Shazam on REDCap Instance (see REDCap Modules in Control Center)
2. Enable Shazam on REDCap Project (administrative rights required)
3. Create Survey with at least one blank description field (e.g. "idetimeout_placeholder")
4. Create Shazam field (see Shazam Setup link in project)
5. Paste the contents of the HTML, CSS and JS files into the corresponding tab fields.
>  + [HTML Content](idletime_placeholder.html)
>  + [CSS](idletime_placeholder.css)
>  + [Javascript](idletime_placeholder.js)
6. Save and Test
7. See Configuration Below

### Customization / Configuration
+ Idletimeout - See JS code line 2. 
```javascript
var idleTimeInMinutes = 30
```
+ Timeout Message - See HTML code line 12
```html
<p class="fs-6">
    The survey form has been reset to prevent other patients from viewing your unfinished responses. We apologize for any inconvenience this may cause.
</p>
```

## Caveats / TDB
+ REDCap multiple page surveys are not supported currently.  REDCap saves partial survey reponses in memory between survey page loads.  The Javascript needs to be modified to accomodate this workflow.
