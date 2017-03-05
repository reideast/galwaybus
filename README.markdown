# Modifications to Galway Bus API
##Forked from Vinny Coyne [http://www.vinnycoyne.com](http://www.vinnycoyne.com)

I added a page to list bus times for stops you request in the URL: stops.html. Use the URL param "stop_num" to refer to a 6-digit stop reference number. This is a flat, simple page that requires a refresh to re-run the API requests. It can displays muliple stops if multiple stop_num's are specified.

### Example:

`stops.html?stop_num=522561&stop_num=524121`

You can access a running version at: [https://intense-ocean-53209.herokuapp.com/stop.html?stop_num=522561&stop_num=524121](https://intense-ocean-53209.herokuapp.com/stop.html?stop_num=522561&stop_num=524121)

Use [https://intense-ocean-53209.herokuapp.com/stopFinder.html](https://intense-ocean-53209.herokuapp.com/stopFinder.html) to easily find those 6-digit stop numbers.

# Galway Bus RTPI API

The rtpi.ie website has access to real-time data for the Galway Bus Éireann transit system. Unfortunately, this data is not officially accessible to developers, and is in a weird, proprietary, JSON-ish format. The aim of this project is to provide a simple API to access this data, returning it in a valid JSON format. It was also a good excuse to finally learn how to use node.js :)

**Live demo available at [http://galwaybus.herokuapp.com](http://galwaybus.herokuapp.com)**

**For more info, visit [http://www.vinnycoyne.com](http://www.vinnycoyne.com)**

## Usage

### Routes

* **`GET /routes.json`**

 Lists all the available bus routes in the Galway transit system. This list is hard-coded and would need to be updated manually, should the routes ever change.

* **`GET /routes/<timetable_id>.json`**

 Returns a list of stops on a given route. Use the `timetable_id` retrieved from the `routes.json` API. In the reponse, the `stops` key will contain all stops, separated into two arrays — the separate arrays represent the opposite directions taken by the bus on the route.
 
### Stops

* **`GET /stops.json`**

 Lists all the available bus stops in the Galway transit system.

* **`GET /stops/<stop_ref>.json`**

 Returns a list of departure times for a given bus stop. Use the `stop_ref` retrieved from the `stops.json` API.

* **`GET /stops/nearby.json?latitude=<latitude>&longitude=<longitude>`**

	Lists ten nearest stops to the coordinates provided in the `latitude` and `longitude` URL parameters. Includes departure times.
 
 
### Schedules

* **`GET /schedules.json`**

 Lists all the available bus routes in the Galway transit system, including links to their PDF timetables on the Bus Éireann website. This list is hard-coded and would need to be updated manually, should the routes ever change.