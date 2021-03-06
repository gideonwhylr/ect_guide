# Event Calendar Tags - Getting Started 

> Intended audience :  **Developers** (or anyone at all friendly with HTML :) ) 


## Overview {docsify-ignore}

Setting up the Event Calendar is as easy as setting up Google Analytics. Simply copy and paste some snippets of code into your HTML to render a fully functional Calendar out-of-the-box. 

The Calendar displays the Events you store in Yext and lets visitors filter through them. You have full control over the data and look-and-feel of the Calendar. 


## Import eventcalendartags.js

This script should go right before your closing `</head>` tag. Really, you it can go anywhere, but it's best to put in the `<head>` to avoid clutter. 


**eventcalendartags.js** 
```html
<script src="https://assets.sitescdn.net/events/events.js"> </script> 
```

## Import Bootstrap for styling (optional but highly reccomended)

We've built the calendar using bootstrap elements. Importing this script will make your calendar pretty out of the box. 

**Bootstrap** 
```html 
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">

<script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/js/bootstrap.min.js" integrity="sha384-JZR6Spejh4U02d8jOt6vLEHfe/JQGiRRSQQxSfFWpi1MquVdAyjUar5+76PVCmYl" crossorigin="anonymous"></script>
```


If you want to use Bootstrap more natively, follow download instructions [here](https://getbootstrap.com/docs/4.0/getting-started/download/)

## Initialize Calendar

Add this snippet to the bottom of your `<body>` tag on the page. 

!> Be sure to replace your Live API Key in the code below ([learn more about your live API key](http://developer.yext.com/docs/guides/get-started/))

Ideally, this should be the last script tag on your page. This ensures it works with all other scripts and tags associated with the calendar. 


```html
<script>
	EventCalendar.Initialize({
		apiKey: 'ADD YOU API KEY HERE',
		resultsTemplate: '#result-template',
		resultsElement: '#results',
		filters: [
			EventCalendar.Filters.Date({
				startDateElement: '.start-date',
				endDateElement: '.end-date'
			}),
			EventCalendar.Filters.Location({
				element: '.location-filter'
			}),
			EventCalendar.Filters.LiveApiFilter({
				element: '.name-filter',
				query: function(value) {
					return {
						name: {
							contains: [value]
						}
					}
				}
			})
		]
	});
</script>
```


## Build Calendar HTML

**The template below** defines what each _event tile_ looks like: 


```html
<script id="result-template" type="text/template">
    <div class="row row-inset pt-3 pb-3 border-bottom border-primary">
        <div class="col-sm-9 d-flex  ">
            <div class="flex-column-centered calendar-item">
                <div class="text-primary date-month"> {{formatDate Event.startDateTime month="short"}}</div>
                <div class="date-day"> {{formatDate Event.startDateTime day="numeric"}} </div>
            </div>
            <div class="flex-column-left">
                <div>{{Event.name}}</div>
                <div>{{ Event.description }}</div>
                <div> <i class="fa fa-map-marker mr-2 text-primary"></i> {{Event.venueName}} - {{Event.address}} - {{Event.city}} </div>
            </div>
        </div>
        <div class="col-sm-3">
  		  <a href="{{Event.websiteUrl}}" target="_blank" class="btn btn-outline-primary "> View Details</a> 
   
		</div>
    </div>
</script>
```

You will get something like this: 

![alt text](/assets/event_tile.png)

The template can go anywhere on your page. You can customize the HTML however your like -- [here are some examples](examples.com). 

## Place Results in HTML

**Next**, copy the code below to actually build the list. Copy it where you want the list to appear. 

```html 
<!-- Other HTML on your page --> 

<div id=“results”> </div>

<!-- Other HTML on your page  --> 

```

You'll get something like this: 

![alt text](/assets/event_list.png)


## Your Calendar is Ready! {docsify-ignore}

You’re all set. Your page will load a calendar pulling all your events from Yext. 

![alt text](/assets/full_cal.png)


# Next Steps
Learn how to customize your calendar, including setting up filters, a map, and much more. See how [here](ect_customization.md). 








