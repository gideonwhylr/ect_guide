# Add a map to your Event Calendar


![alt text](/assets/map.png)
 

## Initialize with Google Maps API Key

Provide your Google Maps API key in the initialization script and declare a map element: 

```html
<script>
	EventCalendar.Initialize({
		apiKey: '3662421a932a9bf10491994d9eb27044',
		resultsTemplate: '#result-template',
		resultsElement: '#results',
		googleMapsApiKey: 'YOUR-API-KEY-HERE', 
		map: '#map' 
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

## Add Map element to your HTML

Add this html element where you want it to appear on your page

```html 
<!-- Any other HTML on your page --> 

<div id="map"> </div>

<!-- Any other HTML on your page --> 

```