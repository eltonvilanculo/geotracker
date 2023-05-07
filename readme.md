Based on GPSTACKER, this is a suitable update for the listed IOT devices listed below


* TK102/TK102B 
* TK103/TK103B 
* TK104
* TK106/TK106B

Install
=======

	npm install geotracker


Usage
=====

A very basic example will be this

```javascript
var gpstracker = require("gpstracker");
var server = gpstracker.create().listen(8000, function(){
    console.log('listening your gps trackers on port', 8000);
});

server.trackers.on("connected", function(tracker){
    
    console.log("tracker connected with imei:", tracker.imei);
    
    tracker.on("help me", function(){
        console.log(tracker.imei + " pressed the help button!!".red);
    });

	tracker.on("position", function(position){
        console.log("tracker {" + tracker.imei +  "}: lat", 
                            position.lat, "lng", position.lng);
    });

      tracker.on("acc", function (acc) {
    console.log("ACC ON");
  });

  tracker.on("door", function (door) {
    console.log("DOOR IS OPEN");
  });

    tracker.trackEvery(10).seconds();
});
```

