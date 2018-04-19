# Calendar Customization

## Filters

> You can use nearly any field in the Live API as an onscreen filter for your visitors. 

![alt text](/assets/filters.png)


**First**, add filters in your initilization script 
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



### Filter by location 

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
	<input type="text" class="form-control" id="location-filter" placeholder="Event Location">
</div>"
```

### Filter by date 

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


### Filter by other fields 

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


## Google Map

> Add a map of your events!

![alt text](/assets/map.png)
 

**First**, provide your Google Maps API key in the initialization script and declare a map element: 

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

**Next**, add this html element where you want it to appear on your page

```html 
<!-- Any other HTML on your page --> 

<div id="map"> </div>

<!-- Any other HTML on your page --> 

```

## Pre-filter events on your page 

> Visitors only see a set of events based on filters you define

**For example**, if you have local store pages and want to put a calendar at the bottom of each, only showing events for that location.


**To prefilter results**, add a filter to the initialization script: 

```javascript 
apiFilters : [{"ANY LIVE API FIELD":{"CONDITION":["VALUE"]}}],

```

To only show events with "Gourmet" in the name, include the following: 

```javascript 
apiFilters : [{"Name":{"Contains":["Gourment"]}}],

```

#### More Examples: {docsify-ignore} 

Only show events after the current date: 

```html
<script>
	var isoDate = new Date().toISOString();
    var now = isoDate.substring(0, isoDate.lastIndexOf(':')).replace('T', ' ');
	EventCalendar.Initialize({
		apiKey: 'YOUR LIVE API KEY HERE',
		resultsTemplate: '#result-template',
		resultsElement: '#results',
		apiFilters : [{"startDateTime":{"ga":[now]}}],
		// the rest of your initialization script 

	});
</script>

```


You can pass in any well-formed filter for the Live API. [Learn more about Live API Filters](http://developer.yext.com/docs/guides/using-live-api/)  

## Images 

> Add images to your event tiles 

![alt text](/assets/event_image.png)


Here is an example of code that would pull in images to your event tile: 
```html 
<script id="result-template" type="text/template">
	<div class="container mb-4">
		<div class="row border" style="border-radius: 10px;">
			<div class="col px-0 background-image" style="background-image: url('{{Event.photos.0.url}}'); border-top-left-radius: 10px; border-bottom-left-radius: 10px;">
			</div>

			<div class="col-8 px-3 pt-3">
				<h4 class="card-text">{{Event.name}}</h4>
				<p class="card-text"><strong>{{formatDate Event.startDateTime day="numeric" month="long" year="numeric"}}</strong></p>
				<p class="card-text description">{{Event.description}}</p>

				<div class="event-tickets pb-3">
					<a class="btn btn-outline-secondary" role="button" href="{{Event.url}}">View Website</a> {{#if Event.ticketUrl}}
					<a class="btn btn-outline-secondary" role="button" href="{{Event.ticketUrl}}">Get Tickets</a> {{/if}}
				</div>
			</div>
		</div>
	</div>
</script>

```


## Loading template 

> Define what visitors see when the page is loading 

![alt text](/assets/loading.png)

Declare the loading template in the initialization script

```html

 <script>

	EventCalendar.Initialize({
		apiKey: '3662421a932a9bf10491994d9eb27044',
		resultsTemplate: '#result-template',
		resultsElement: '#results',
		// the rest of your initialization script 
		
		loadingTemplate: '#loading-template',		
	});
</script>

```


Define the template anywhere on your page
```html 
<script id="loading-template" type="text/template">
      
<!-- Add whatever you like below --> 
<div> Loading Results...</div>

</script>

```

Whatever html you place in the script tag will appear while the list of events is loading. It will appear wherever you placed your `<div id=“results”> </div>` element. It will be replaced automatically when all events load.


## Results per Page

> Set how many events appear in your list

```html
 <script>

	EventCalendar.Initialize({
		apiKey: '3662421a932a9bf10491994d9eb27044',
		resultsTemplate: '#result-template',
		resultsElement: '#results',
		
		// the rest of your initialization script 
		
		resultsPerPage: '10', 

		
	});
</script>
```


## Pagination

> Add page control to your list 

![alt text](/assets/pagination.png)

```html 
<!-- Copy this where you want page controls to appear --> 

<div class="btn btn-outline-secondary ect-paginate-start"> <i class="fa fa-angle-double-left"></i> </div>
<div class="btn btn-outline-secondary ect-paginate-back"> <i class="fa fa-angle-left"></i> </div>
<div class="btn btn-outline-secondary ect-paginate-forward"> <i class="fa fa-angle-right"></i> </div>
<div class="btn btn-outline-secondary  ect-paginate-end"> <i class="fa fa-angle-double-right"></i> </div>

```



