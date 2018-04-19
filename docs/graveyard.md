## Getting started

Event Calendars are implemented in three 3 steps: 

1. Import our ect.js library onto your page 
2. Initialize the event calendar with a snippet of javascript 
3. Build the calendar out in html 

Thus, you’ll be copying three snippets of code onto your webpage: 


![alt text](/assets/ect_schematic.png)

If your code-editor only shows you a porting of the page(i.e. You’re using something like Wix or squarespace) that’s fine. Following our guide here. 

> Let’s get started! 

# Customization


## Automatic Geo-filter

> The browser will ask to use the visitors location. The calendar will only show events within a radius that you define

```html
 <script>

	EventCalendar.Initialize({
		apiKey: '3662421a932a9bf10491994d9eb27044',
		resultsTemplate: '#result-template',
		resultsElement: '#results',
		
		// the rest of your initialization script 
		
		automaticallyGeolocate: 'true' , 
		locationRadius: '10',

		
	});
</script>
```
