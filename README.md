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

    `<script src="gasl.js" type="text/javascript"></script>`

3. Update the [**gaConfig**](https://github.com/nekcih/GASL/blob/master/gasl.js#L18-L26) section in [**gasl.js**](https://github.com/nekcih/GASL/blob/master/gasl.js).

### Javascript Triggers

In Storyline, create a Javascript trigger. To manually track a pageView, use the following code (where sTitle is optional):

    gasl.trackPageview(sPath, [sTitle]);

To manually track an event, use the following code (where sLabel and eventData are optional):

    gasl.trackEvent(sCategory, sAction, [sLabel, eventData]);

### Additional Info

See the comments in [**gasl.js**](https://github.com/nekcih/GASL/blob/master/gasl.js) (particularly the [**gaConfig**](https://github.com/nekcih/GASL/blob/master/gasl.js#L18-L26)) for additonal usage information.

**Note:** GASL does not automatically track slide numbers because it's possible for a slide to move in your project which would invalidate historical data in Google Analytics. 

Automatic event tracking based on SCORM interactions would be difficult because the cmi.suspend_data is compressed with a proprietary algorithm. It is chunked and base64 encoded. To decode, you would have to know the number of parts to each chunk which could possibly be extrapolated from the html5 output. 

Think GASL could do better? Suggest improvements via a pull request!


## Compatibility

GASL has been tested with the following:
- Articulate Storyline 2 Update 3: 1412.922 
- Published with SCORM 1.2 and HTML5
- Chrome 45, Firefox 38, IE 7+

