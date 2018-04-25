# Adding filters to your  Calendar

> You can use nearly any field in the Live API as an onscreen filter for your visitors. 

![alt text](/assets/filters.png)

We'll explain how this works in general, then go into specific examples(filters for location, date, etc). 

**First**, you add filters in your initilization script. Below, we show a generic field in the Live API.  
```html 
<script>
	EventCalendar.Initialize({
		// the rest of your inilization script 
		filters: [
			EventCalendar.Filters.LiveApiFilter({
				element: '.MY-CUSTOM-FILTER',
				query: function(value) {
					return {
						'<ANY-LIVE-API-FIELD>': {
							contains: [value]
						}
					}
				}
			})
		]
	});
</script>

```

**Next**, add the UI for the filters where you want it to appear on your page
```html
<!-- Other HTML on your page --> 

<input class="MY-CUSTOM-FILTER"> </div> 
<button type="submit" class="ect-search">Filter</button>   

<!-- Other HTML on your page --> 

```

The HTML element we added above was *declared* in the initilization script. In general, you declare any filter you want to use in the initlization script, and then render it in the HTML directly. 

*Let's look at some examples*.

## Filter by location 

Initlization script: 
```javascript
filters: [
	EventCalendar.Filters.Location({
        element: '.location-filter'
	})
] 
```

UI on page: 
```html 
<div>
	<input type="text" class="form-control location-filter" id="location-filter" placeholder="Event Location">
</div>"
```

## Filter by date 

Initlization script: 
```javascript
filters: [
	EventCalendar.Filters.Date({
        startDateElement: '.start-date',
        endDateElement: '.end-date' 
	})
] 

```

UI on page: 
```html 
<div class="input daterange">
        <input type="text" class="form-control start-date"  placeholder="After this Date">
        <input type="text" class="form-control end-date" placeholder="Up until this Date">        
</div>
```


## Filter by other fields 

> Choose any field in the live api as an on-screen filter for your visitors


Initlization script: 
```javascript
filters: [
	EventCalendar.Filters.LiveApiFilter({
	        element: '.venue-name',        // name the element something that corresponds to the filter you're working with  
	        query: function(value) {
	                return {
	                        venueName: {         // use any field from the Live API here 
	                                contains: [value]
	                        }
	                }
	        }
	})
] 

```

UI on page: 
```html 
<div class="input">
        <input type="text" class="form-control venue-name"  placeholder="Event Venue">       
</div>
```
