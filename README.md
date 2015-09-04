# Google Analytics for Storyline (GASL)

## What is it?

GASL is a javascript utility for Articulate Storyline that allows additional tracking to Google Analytics.


### How does it work?

GASL hooks into the SCORM functions of a published Storyline project. Storyline publishes its table of contents information to **"story_content/frame.xml"**. When resume data is saved, it is checked against the navigation to determine the current slide and then sent to GA for tracking.


## Features

- Automatic and manual pageView tracking
- Manual event tracking


## Usage

1. Update navigation in Storyline which will be published to **"story_content/frame.xml"**.
   - Only pages included in the navigation will be automatically tracked in Google Analytics.

       Home > Player > Menu > Reset from story (icon)
2. Add the following line to the published **"story.html"**, **"index_lms.html"**, and **"index_lms_html5.html"** just before the `</html>` tag...

    `<script src="gasl-scorm.js" type="text/javascript"></script>`

3. Update the **gaConfig** section in **gasl.js**.

### Javascript Triggers

In Storyline, create a Javascript trigger. To manually track a pageView, use the following code:

    gasl.trackPageview(sPath, sTitle);

To manually track an event, use the following code:

    gasl.trackEvent(sCategory, sAction, [sLabel, eventData]);

### Additional Info

See the comments in **gasl.js** (particularly the **gaConfig**) for additonal usage information.

**Note:** GASL does not automatically track slide numbers because it's possible for a slide to move in your project which would invalidate historical data in Google Analytics. 

Think GASL could do better? Suggest improvements via a pull request!


## Compatibility

GASL has been tested with the following:
- Articulate Storyline 2 Update 3: 1412.922 
- Published with SCORM 1.2 and HTML5
- Chrome 45, Firefox 38, IE 7+

