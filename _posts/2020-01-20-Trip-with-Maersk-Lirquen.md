---
layout: post
title: A week sailing on Maersk Lirquen
author: Angelos Ikonomakis
---
[figure_1]: ../images/Lirquen/xsens.png "Figure 1"
[figure_2]: ../images/Lirquen/IMG_20191209_073519.jpg?fixOrientation "Figure 2"
[figure_3]: ../images/Lirquen/IMG_20191209_073917__01.jpg?fixOrientation "Figure 3"
[figure_4]: ../images/Lirquen/IMG_20191209_105839.jpg?fixOrientation "Figure 4"
[figure_5]: ../images/Lirquen/IMG_20191209_105902.jpg "Figure 5"
[figure_6]: ../images/Lirquen/IMG_20191209_105908.jpg "Figure 6"
[figure_7]: ../images/Lirquen/IMG_20191209_105934.jpg "Figure 7"
[figure_8]: ../images/Lirquen/IMG_20191209_110317.jpg "Figure 8"
[figure_9]: ../images/Lirquen/IMG_20191209_111901.jpg "Figure 9"
[figure_10]: ../images/Lirquen/IMG_20191209_111905.jpg "Figure 10"
[figure_11]: ../images/Lirquen/IMG_20191209_113555.jpg "Figure 11"
[figure_12]: ../images/Lirquen/IMG_20191209_115612.jpg "Figure 12"
[figure_13]: ../images/Lirquen/IMG_20191209_130245.jpg "Figure 13"
[figure_14]: ../images/Lirquen/IMG_20191209_130252.jpg "Figure 14"
[figure_15]: ../images/Lirquen/IMG_20191210_032441.jpg "Figure 15"
[figure_16]: ../images/Lirquen/IMG_20191210_032428.jpg "Figure 16"
[figure_17]: ../images/Lirquen/IMG_20191210_032332.jpg "Figure 17"
[figure_18]: ../images/Lirquen/IMG_20191210_041713.jpg "Figure 18"
[figure_19]: ../images/Lirquen/IMG_20191210_043107__01.jpg "Figure 19"
[figure_20]: ../images/Lirquen/IMG_20191210_053557__01.jpg "Figure 20"
[figure_21]: ../images/Lirquen/IMG_20191211_082842.jpg "Figure 21"
[figure_22]: ../images/Lirquen/IMG_20191211_082847.jpg "Figure 22"
[figure_23]: ../images/Lirquen/IMG_20191211_134618.jpg "Figure 23"
[figure_24]: ../images/Lirquen/IMG_20191211_141825.jpg "Figure 24"
[figure_25]: ../images/Lirquen/IMG_20191212_105726.jpg "Figure 25"
[figure_26]: ../images/Lirquen/IMG_20191212_105741.jpg "Figure 26"
[figure_27]: ../images/Lirquen/IMG_20191212_105858.jpg "Figure 27"
[figure_28]: ../images/Lirquen/IMG_20191212_160853.jpg "Figure 28"
[figure_29]: ../images/Lirquen/IMG_20191214_085117__01.jpg "Figure 29"
[figure_30]: ../images/Lirquen/Lirquen_Sens_Loc_1.png "Figure 30"
[figure_31]: ../images/Lirquen/IMG_20191214_124401.jpg "Figure 31"
[figure_32]: ../images/Lirquen/IMG_20191215_012941.jpg "Figure 32"
[figure_33]: ../images/Lirquen/IMG_20191215_020812__01.jpg "Figure 33"
[figure_34]: ../images/Lirquen/IMG_20191215_020826__01.jpg "Figure 34"
[figure_35]: ../images/Lirquen/IMG_20191215_021320.jpg "Figure 35"
[figure_36]: ../images/Lirquen/IMG_20191215_010902.jpg "Figure 36"
[figure_37]: ../images/Lirquen/IMG_20191212_183341.jpg "Figure 37"
[figure_38]: ../images/Lirquen/IMG_20191214_220259__01.jpg "Figure 38"
In this post, I will share some facts about my first trip on a container vessel. The main subject of this trip(as the title claims) is sailing on a 300m container vessel for 7 days, from Singapore to Busan(South Korea). The main purpose of the trip is to collect inertial data which will be sourced as measurement inputs into a nonlinear model I have built, for the purpose of my PhD project.

## Overview

During the trip, once per day, I was updating my GPS location on the **live map** below. The total trip duration was planned to be 11 days, due to me living in Copenhagen and having to fly to Singapore for the embarkation, and flying back from Busan after the disembarkation. 

<style>
    #realtime_map {
    width:100%;
    height:550px;
    border:none;
}  
.lineConnect {
    fill: none;
    stroke: black;
    opacity: 1;
}
div.tooltip { 
    all:initial;
    float:right;
    width:120px;
    height: 120px;
    padding: 6px 8px;
    margin: 10px 10px 0 0;
    font: 14px/16px Arial, Helvetica, sans-serif;
    background: white;
    background: rgba(255,255,255,0.8);
    box-shadow: 0 0 15px rgba(0,0,0,0.2);
    border-radius: 5px;
}
.tooltip>h4{
    margin: 0 0 5px;
    color: #777;
}
.legend {
    all:initial;
    float:right;
    width:120px;
    height: 55px;
    padding: 6px 8px;
    margin: 160px -135px 0 0;
    font: 14px/16px Arial, Helvetica, sans-serif;
    background: white;
    background: rgba(255,255,255,0.8);
    box-shadow: 0 0 15px rgba(0,0,0,0.2);
    border-radius: 5px;
}
.legend i {
    width: 12px;
    height: 12px;
    float: left;
    margin-right: 8px;
    opacity: 0.7;
    border-radius: 6px;
}
</style>

<!-- Add Leaflet's CSS
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.6.0/dist/leaflet.css" Integrity="sha512-xwE/Az9zrjBIphAcBb3F6JVqxf46+CDLwfLMHloNu6KEQCAWi6HcDUbeOfBIptF7tcCzusKFjFw2yuvEpDL9wQ=="
   crossorigin=""/>
 Make sure you put this AFTER Leaflet's CSS
 <script src="https://unpkg.com/leaflet@1.6.0/dist/leaflet.js" integrity="sha512-gZwIG9x3wUXg2hdXF6+rVkLF/0Vi9U8D2Ntg4Ga5I5BZpVkVxlJWbSQtXPSiUTtC0TjtGOmxa1AJPuV0CPthew=="
   crossorigin=""></script>-->


<!-- //cdn.leafletjs.com/leaflet-0.7/leaflet-->
<div id="realtime_map"></div>

<script>
/*
 * Leaflet.Sleep
 */

/*
 * Default Button (touch devices only)
 */

L.Control.SleepMapControl = L.Control.extend({

  initialize: function(opts){
    L.setOptions(this,opts);
  },

  options: {
    position: 'topright',
    prompt: 'disable map',
    styles: {
      'backgroundColor': 'white',
      'padding': '5px',
      'border': '2px solid gray'
    }
  },

  buildContainer: function(){
    var self = this;
    var container = L.DomUtil.create('p', 'sleep-button');
    var boundEvent = this._nonBoundEvent.bind(this);
    container.appendChild( document.createTextNode( this.options.prompt ));
    L.DomEvent.addListener(container, 'click', boundEvent);
    L.DomEvent.addListener(container, 'touchstart', boundEvent);

    Object.keys(this.options.styles).map(function(key) {
      container.style[key] = self.options.styles[key];
    });

    return (this._container = container);
  },

  onAdd: function () {
    return this._container || this.buildContainer();
  },

  _nonBoundEvent: function(e) {
    L.DomEvent.stop(e);
    if (this._map) this._map.sleep._sleepMap();
    return false;
  }

});

L.Control.sleepMapControl = function(){
  return new L.Control.SleepMapControl();
};


/*
 * The Sleep Handler
 */

L.Map.mergeOptions({
  sleep: true,
  sleepTime: 750,
  wakeTime: 750,
  wakeMessageTouch: 'Touch to Wake',
  sleepNote: true,
  hoverToWake: true,
  sleepOpacity:.7,
  sleepButton: L.Control.sleepMapControl
});

L.Map.Sleep = L.Handler.extend({

  addHooks: function () {
    var self = this;
    this.sleepNote = L.DomUtil.create('p', 'sleep-note', this._map._container);
    this._enterTimeout = null;
    this._exitTimeout = null;

    /*
     * If the device has only a touchscreen we will never get
     * a mouseout event, so we add an extra button to put the map
     * back to sleep manually.
     *
     * a custom control/button can be provided by the user
     * with the map's `sleepButton` option
     */
    this._sleepButton = this._map.options.sleepButton();

    if (this._map.tap) {
      this._map.addControl(this._sleepButton);
    }

    var mapStyle = this._map._container.style;
    mapStyle.WebkitTransition += 'opacity .5s';
    mapStyle.MozTransition += 'opacity .5s';

    this._setSleepNoteStyle();
    this._sleepMap();
  },

  removeHooks: function () {
    if (!this._map.scrollWheelZoom.enabled()){
      this._map.scrollWheelZoom.enable();
    }
    if (this._map.tap && !this._map.tap.enabled()) {
      this._map.touchZoom.enable();
      this._map.dragging.enable();
      this._map.tap.enable();
    }
    L.DomUtil.setOpacity( this._map._container, 1);
    L.DomUtil.setOpacity( this.sleepNote, 0);
    this._removeSleepingListeners();
    this._removeAwakeListeners();
  },

  _setSleepNoteStyle: function() {
    var noteString = '';
    var style = this.sleepNote.style;

    if(this._map.tap) {
      noteString = this._map.options.wakeMessageTouch;
    } else if (this._map.options.wakeMessage) {
      noteString = this._map.options.wakeMessage;
    } else if (this._map.options.hoverToWake) {
      noteString = 'click or hover to wake the map';
    } else {
      noteString = 'click to wake';
    }

    if( this._map.options.sleepNote ){
      this.sleepNote.appendChild(document.createTextNode( noteString ));
      style.pointerEvents = 'none';
      style.maxWidth = '180px';
      style.transitionDuration = '.2s';
      style.zIndex = 5000;
      style.opacity = '.6';
      style.margin = 'auto';
      style.textAlign = 'center';
      style.borderRadius = '4px';
      style.top = '50%';
      style.position = 'relative';
      style.padding = '5px';
      style.border = 'solid 2px black';
      style.color = 'black';
      style.background = 'white';

      if(this._map.options.sleepNoteStyle) {
        var noteStyleOverrides = this._map.options.sleepNoteStyle;
        Object.keys(noteStyleOverrides).map(function(key) {
          style[key] = noteStyleOverrides[key];
        });
      }
    }
  },

  _wakeMap: function (e) {
    this._stopWaiting();
    this._map.scrollWheelZoom.enable();
    if (this._map.tap) {
      this._map.touchZoom.enable();
      this._map.dragging.enable();
      this._map.tap.enable();
      this._map.addControl(this._sleepButton);
    }
    L.DomUtil.setOpacity( this._map._container, 1);
    this.sleepNote.style.opacity = 0;
    this._addAwakeListeners();
  },

  _sleepMap: function () {
    this._stopWaiting();
    this._map.scrollWheelZoom.disable();

    if (this._map.tap) {
      this._map.touchZoom.disable();
      this._map.dragging.disable();
      this._map.tap.disable();
      this._map.removeControl(this._sleepButton);
    }

    L.DomUtil.setOpacity( this._map._container, this._map.options.sleepOpacity);
    this.sleepNote.style.opacity = .4;
    this._addSleepingListeners();
  },

  _wakePending: function () {
    this._map.once('mousedown', this._wakeMap, this);
    if (this._map.options.hoverToWake){
      var self = this;
      this._map.once('mouseout', this._sleepMap, this);
      self._enterTimeout = setTimeout(function(){
          self._map.off('mouseout', self._sleepMap, self);
          self._wakeMap();
      } , self._map.options.wakeTime);
    }
  },

  _sleepPending: function () {
    var self = this;
    self._map.once('mouseover', self._wakeMap, self);
    self._exitTimeout = setTimeout(function(){
        self._map.off('mouseover', self._wakeMap, self);
        self._sleepMap();
    } , self._map.options.sleepTime);
  },

  _addSleepingListeners: function(){
    this._map.once('mouseover', this._wakePending, this);
    this._map.tap &&
      this._map.once('click', this._wakeMap, this);
  },

  _addAwakeListeners: function(){
    this._map.once('mouseout', this._sleepPending, this);
  },

  _removeSleepingListeners: function(){
    this._map.options.hoverToWake &&
      this._map.off('mouseover', this._wakePending, this);
    this._map.off('mousedown', this._wakeMap, this);
    this._map.tap &&
      this._map.off('click', this._wakeMap, this);
  },

  _removeAwakeListeners: function(){
    this._map.off('mouseout', this._sleepPending, this);
  },

  _stopWaiting: function () {
    this._removeSleepingListeners();
    this._removeAwakeListeners();
    var self = this;
    if(this._enterTimeout) clearTimeout(self._enterTimeout);
    if(this._exitTimeout) clearTimeout(self._exitTimeout);
    this._enterTimeout = null;
    this._exitTimeout = null;
  }
});

L.Map.addInitHook('addHandler', 'sleep', L.Map.Sleep);

// The center must be updated whenever I put a new coordinate on the map
var center = [22.46,111.50]

var mymap = L.map('realtime_map').setView(center, 4);
        L.tileLayer('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token={accessToken}', {
    attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/">OpenStreetMap</a> contributors, <a href="https://creativecommons.org/licenses/by-sa/2.0/">CC-BY-SA</a>, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
    maxZoom: 18,
    id: 'mapbox/streets-v11',
    accessToken: 'pk.eyJ1Ijoib2lrb25hbmciLCJhIjoiY2ozM2RjcjIyMDBjODJ3bzh3bnRyOHBxMyJ9.nQH16WG-DcBB_TQEEJiuCA'
}).addTo(mymap);

// Create starting marker
var marker_start = L.marker([1.274548, 103.758484]).addTo(mymap);
marker_start.bindPopup("<b>Starting Point!</b>").openPopup();

// Create finishing marker
var marker_finish = L.marker([35.11, 129.05]).addTo(mymap);
marker_finish.bindPopup("<b>Wanted to get there!</b>").openPopup();

//  Initialize the SVG layer (OLD CSS)
mymap._initPathRoot() 

/* We simply pick up the SVG from the map object (OLD CSS)*/
var svg = d3.select("#realtime_map").select("svg"),
g = svg.append("g");

// Define the div for the tooltip
var div = d3.select("#realtime_map")
            .append("div") 
            .attr("class", "tooltip")       
            .style("opacity", .9);

// Add a starting message
div.html("<h4>Live Location</h4>"+ "<br/>" + "Hover over a point");

// Define the div for the legend
var legend = d3.select("#realtime_map")
               .append("div")
               .attr("class", "legend")
               .style("opacity", .9);
               
// Add a starting message
legend.html('<i style="background: green"></i>' + 'Starting Point' + '<br/>' + 
            '<i style="background: yellow"></i>' + 'Daily Update' + '<br/>' +
            '<i style="background: red"></i>' + 'Finish Point');
            
// Hardcode the values of the csv
var csv = `day,date,lat,lon,state
0,2019-12-09 08:59:00,1.274548,103.758484,0
1,2019-12-10 21:42:00,1.273252,103.9429,1
2,2019-12-11 21:00:00,2.6905,105.145,1
3,2019-12-12 22:28:00,8.3,109.4,1
4,2019-12-13 21:35:00,14.8,112.5,1
5,2019-12-15 02:30:00,22.33255,114.1172,2
`;

var collection = d3.csvParse(csv);

// Stream transform. transforms geometry before passing it to
// listener. Can be used in conjunction with d3.geoPath
// to implement the transform.
var transform = d3.geoTransform({point: projectPoint});

//d3.geoPath translates GeoJSON to SVG path codes.
//essentially a path generator. In this case it's
// a path generator referencing our custom "projection"
// which is the Leaflet method latLngToLayerPoint inside
// our function called projectPoint
var path = d3.geoPath().projection(transform);

// Add a LatLng object to each item in the dataset
collection.forEach(function(d) {
d.LatLng = new L.LatLng(d.lat,
d.lon)
})

// For simplicity I hard-coded this! I'm taking
// the first object (the origin)
// and destination and adding them separately to
// better style them.
// var startpoint = collection[0]
// var endpoint = collection[collection.state==0]
// console.log(endpoint)
// Add the points of the days excluding the starting and finishing day
var feature = g.selectAll("path")
.data(collection)
.enter().append("circle")
.style("fill", function(d) {
if(+d.state == 0){
return 'green'
}
else if(+d.state == 1){
return 'yellow'
}
else if(+d.state == 2){
return 'red'
}
})  
.style("opacity", function(d) {
if(+d.state == 0){
return 1
}
else if(+d.state == 1){
return 0.7
}
else if(+d.state == 2){
return 0.8
}
})   
.attr("r", function(d) {
if(+d.state == 0){
return 10
}
else if(+d.state == 1){
return 5
}
else if(+d.state == 2){
return 10
}
})
.on("mouseover", mouseover)
.on("mouseout" , mouseout);


// Here we will make the points into a single
// line/path. Note that we surround the featuresdata
// with [] to tell d3 to treat all the points as a
// single line. For now these are basically points
// but below we set the "d" attribute using the 
// line creator function from above.
var linePath = g.selectAll(".lineConnect")
.data([collection])
.enter()
.append("path")
.attr("class", "lineConnect");

// Here we're creating a FUNCTION to generate a line
// from input points. Since input points will be in 
// Lat/Long they need to be converted to map units
// with applyLatLngToLayer
var toLine = d3.line()
.x(function(d) {
return applyLatLngToLayer(d).x
})
.y(function(d) {
return applyLatLngToLayer(d).y
})
.curve(d3.curveCardinal);


mymap.on("viewreset", update);
update();

// Create a function to handle the layers on zoum in and out
function update() {
feature.attr("transform", 
function(d) { 
return "translate("+ 
mymap.latLngToLayerPoint(d.LatLng).x +","+ 
mymap.latLngToLayerPoint(d.LatLng).y +")";
}
)
linePath.attr("d", toLine)
} // close update

// Create a function to handle the tip on mouseover
function mouseover(d){
        if(+d.state == 0){
            // Write staff on tooltip
            div.html("<h4>Realtime Location</h4>" + "<br/>" + "<strong>Starting point!</strong>"+ "<br/>" + "Date: " + d.date + " UTC+8")  
        }
        else if(+d.state == 1){
            // Write staff on tooltip
            div.html("<h4>Realtime Location</h4>" + "<br/>" + "Day " + d.day + "<br/>" + "Date: " + d.date + " UTC+8")  
        }
        else if(+d.state == 2){
            // Write staff on tooltip
            div.html("<h4>Realtime Location</h4>" + "<br/>" + "<strong>Finish point</strong>" + "<br/>" + "Total Days " + d.day + "<br/>" + "Date: " + d.date + " UTC+8")  
        }
        // Show tooltip
        div.transition()    
           .duration(200)    
           .style("opacity", .9);

        // Place the tooltip
        // div.style("left", (d3.event.pageX) + "px")   
        //    .style("top", (d3.event.pageY - 28) + "px");
}// close mouseover
// Create a function to handle the tip on mouseout
function mouseout(d){
        // remove the tip
        div.transition()
           .duration(500)
           .style("opacity", .9); 

        div.html("<h4>Realtime Location</h4>"+ "<br/>" + "Hover over a point");
}// close mouseout
// Use Leaflet to implement a D3 geometric transformation.
// the latLngToLayerPoint is a Leaflet conversion method:
//Returns the map layer point that corresponds to the given geographical
// coordinates (useful for placing overlays on the map).
function projectPoint(x, y) {
    var point = mymap.latLngToLayerPoint(new L.LatLng(y, x));
    this.stream.point(point.x, point.y);
}  // close projectPoint  

// similar to projectPoint this function converts lat/long to
// svg coordinates except that it accepts a point from our 
// GeoJSON
function applyLatLngToLayer(d) {
    var y = d.lat
    var x = d.lon
    return mymap.latLngToLayerPoint(new L.LatLng(y, x));
} // close applyLatLngToLayer
</script>

Here is a short overview of the sensors that had been installed on the vessel:

![xsens_overview][figure_1]

Unfortunately, due to confidentiality I am not allowed to share any delails regarding the purpose, the technical requirements, the software and hardware handling. But I can share my daily routine since the beginning till the end of the trip!

## Day 1

This is the first day of my trip on the vessel. The agent was at the hotel on time (2019-12-09 Mon 07:00) where we started heading to the terminal. The weather was warm and cloudy with a few raindrops. 

![terminal_1][figure_2]  ![terminal_2][figure_3]

The driver dropped me at the immigration office of the terminal where I showed my documents and passed through the final gate before moving to the vessel. I reached the ship during the process of loading and unloading containers. I walked up the stairs and I passed through a first document-check by a deck officer. Then, the officer(Kevin) showed me the way to my cabin which was located on the B-deck, I settled my personal stuff, packed my back-pack with all the necessary equipment I would use and moved on to look for the sensor installation locations. 

But before going further, I first had to get dressed accordingly. It is not allowed to walk around the deck without wearing the required PPE. I contacted the cadet who showed me the room earlier and he took me to the PPE storage room where he gave me the MAERSK uniform, gloves, boots and helmet. Having dressed up accordingly, I went to find the cadet who would assist me and be my navigator during the installation position scouting.

![own_1][figure_7]

The first location we started looking at was at the aft part of the deck. My initial intention was to place the sensor on an open space, close to the centerline, where the GPS antenna would be functional. Fortunately, while going through the location scouting, heavy rain started falling on the deck so hard that it helped me realize that those open spaces were no-go options due to my non-waterproof equipment. 


:-------------------------|:-------------------------:|-------------------------:|
![aft_1][figure_4]        |  ![aft_2][figure_5]       | ![aft_3][figure_6]

Therefore, the next optimal option was to discard the antenna and place the sensor somewhere within the hull, quite close to where we were. The position was found just one level below the initial planning, always as close to the centerline as possible. So we ended up installing the first sensor at the steering gear room.

:----------------------:|:-------------------------:
![steering_1][figure_8] | ![steering_5][figure_12]

:-----------------------:|:-----------------------:|:------------------------:
![steering_2][figure_9] | ![steering_3][figure_10]| ![steering_4][figure_11] 

The second location was easier. We went straight to the Bridge and repeated the same installation act right next to the magnetic gyrocompass of the vessel. 

:----------------------:|:-------------------------:|
![bridge_1][figure_13]  | ![bridge_2][figure_14]

To further understand the location of each sensor, I have drawn the sketch below.

![sketch_19][figure_30]

For the rest of the day, I was testing the exporting functionality of the MT software suite for files greater than 1GB. Apparently, the software required plenty of time to process and export an ASCII file out of the initially recorded .mgi file. In the meanwhile, I was in constant conversation with XSENS engineers to find the best possible way to process the data after ther recording.

Last but not least, I had to figure out the TT-sense configuration. For this to happen, I would need the assistant of the Chief Engineer(Armin) who was supposed to be resting until late afternoon. So I managed to talk with him 2 hours before the ETD from Singapore and together we went down to the propeller shaft, where TT-sense control box was located. The plan was to renew the SD card installed inside the box. 

:-----------------------:|:-----------------------:|:------------------------:
![TT_1][figure_15]       | ![TT_2][figure_16]      | ![TT_3][figure_17] 


After a long day(and night) I was able to capture a few photos of the vessel's late check-out at the port of Singapore on (2019-12-10 Tue 03:00). 

![Singapore_19][figure_19]
![Singapore_20][figure_20]

I also recorded a nightmode time-lapse of the first 3 hours of the trip! Click on the image below and enjoy the whole video (It's only 1min long)!

<a href="http://www.youtube.com/watch?feature=player_embedded&v=GiwQQOUFg24
" target="_blank"><img src="http://img.youtube.com/vi/GiwQQOUFg24/0.jpg" 
alt="IMAGE ALT TEXT HERE" width="100%" height="580" border="10" /></a>

Surprisingly and quite unexpectedly, the vessel had to anchor a few hours after its departure. There had been oil spoilage at the starboard(right) part of the hull and a cleaning crew ought to come and fix it before we reached the next port. The cleaning was scheduled for (2019-12-10 Tue 08:00) so hopefully, there would not be any significant delay.

Consequently, the sensors had to stop recording. The bridge sensor had stopped but the aft sensor was still recording, since I had no key to go to the steering room -yet.

## Day 2

I spent most of the day sleeping since the jetlag and the long night hours of sailing before the anchoring, affected my stamina. I woke up at (2019-12-10 Tue 15:30) and went straight to the bridge for some hot coffee and a nice talk with the captain(Nikolay). He informed me that the vessel familiarization procedure(which is mandatory for every new crew member on the vessel) had been canceled and would fix a new schedule for the day after. 

A couple of hours later, I joined dinner and talked with Armin, who informed me that the SD card I replaced in the TT-sense control box had not recorded anything and that even the monitoring system had stopped working. Hence, I had to create a copy of the old SD card and give it back to him, so as to put it back in the control box before we started sailing again. Shortly after, I sent a message to the sensor manufacturer informing them about the malfunction and asking for further requirements for the new SD.

The next step was to search for a key so as to be able to access the steering room whenever needed. Nikolay said that we could find a key for the padlock the day after since the one holding the keys was the Chief Officer. “So until tomorrow”, I thought, “the aft sensor will keep on recording”. Nikolay also informed me that the cleaning of the hull would start at (2019-12-10 Tue 22:00) and last for five hours, so the plan was that we would finally start sailing early the morning to come; full speed to Hong-Kong.

This day I wasn't full-on. Apparently, the spasmodic sleeping and resting, as well as the multiple traveling, were harder to process than I thought. So I went back to sleep at around (2019-12-10 Tue 23:59).

## Day 3

A good breakfast is always welcome, especially after a long day of mainly sleeping and recovering my system. So, straight to the bridge for a coffee and the latest news on the cleaning. I was informed that the cleaning schedule had been delayed for 3 hours (meaning that it started at (2019-12-11 Wed 01:00)), so it was actually still happening when I reached the bridge. Nikolay mentioned that they should have finished earlier, but they had left a part uncleaned due to its difficult structure, so he had to call them back to clean it better this time and reach the deepest staining. That, of course, meant some extra delay. 


![clean_1][figure_21] 
![clean_2][figure_22]

In the meanwhile, it was perfect timing for a vessel familiarization. I went for a one-hour ship familiarization tour, where I was explained the main concepts and actions in case of an emergency situation. When the tour ended, I went back to the bridge to talk with the captain about the new ETA in Hong Kong. By (2019-12-11 Wed 12:30) it was finally confirmed that the cleaners had done their best and that we could disengage the anchor and sail for Hong Kong. The pilot arrived at 13:30 and the trip was about to begin. I went down to the aft, found the person who was holding the padlock key for the steering gear and made clear that the sensor had restarted and that the previous data file was securely duplicated. When we started moving, I initiated the bridge sensor too.

I stayed at the bridge for a couple of hours to experience the manoeuvering within the anchored and moving vessels so as to create a new timelapse. Meanwhile, I was looking for the best possible option to choose for my project. The -in total- 30 hours of delay had made my schedule very tight and I didn’t want to risk reaching Busan later than my booked flight. So after analyzing all my potential options, in terms of cost, time and damage of the data collection, I saw that it was best to disembark from the vessel in Hong Kong instead of the initial destination of Busan. 

![Singapore_23][figure_23]
![Singapore_24][figure_24]

Click on the image below and enjoy the timelapse video, beginning from disengaging the anchor outside Singapore, towards Hong Kong passing through the busy South China Sea!

<a href="http://www.youtube.com/watch?feature=player_embedded&v=bGou14vw_bM
" target="_blank"><img src="http://img.youtube.com/vi/bGou14vw_bM/0.jpg" 
alt="IMAGE ALT TEXT HERE" width="100%" height="580" border="10" /></a>

Time for dinner. On Wednesdays and Saturdays, there is ice cream as a dessert and that was great news! So after a long day, it was time for resting, exercising at the ship’s gym and having a cozy dinner. The last task of the day was to check our location coordinates at around (2019-12-11 Wed 21:00) and update the live feed on the map. 

## Day 4

This day was the first sunny day of my trip! 

![trip_1][figure_29]

Apart from that, I was finally familiarized with the time difference and I followed the complete schedule of the ship. Huray! Waking up in time for breakfast at 07:00, making it to lunch at 12:30 and then dinner at 17:30, made me feel like a true crew member. Additionally, I took place in the scheduled drill! Drill means that for safety reasons, the crew is given a risk scenario, which they have to deal with while sailing. At Maersk, "our people" is one of the core values of the company and safety comes along with it. So this kind of drills like "fire alarm" and "abandon ship" happen occasionally for various reasons, either to maintain crew's awareness and memory to recall how to deal with emergency situations, or to ensure that the safety equipment (lifeboats, life jackets, suits, AED, etc.) is well maintained and always in excellent condition of use at any time.

:----------------------:|:-------------------------:|:-------------------------:|
![drill_1][figure_25]   | ![drill_2][figure_26]     | ![drill_3][figure_27]

After the drill training and after having lunch, it was time to do some laundry. While washing I went in my room to read … and enjoy a little siesta. Later on, I continued working on the data collection setup. I realized that the timestamp in the DELL computers I was using for the data collection, was stuck to a random date in 2015, which created an extra mess since the local time (in which I kept all of my notes concerning the data collection) was UTC+7, the timestamps were UTC(based always on the timezone of the computer setup) and my phone was sometimes capturing the Philippines local time, which is UTC+8. So I had to calculate all the errors and make sure that everything captured would at the end be converted to UTC - the format of the data lake I was about to merge the data with, after the data collection and cleaning.

In the meanwhile, as every day, I had to keep in mind restarting the data recording in both sensors, so as to be sure that the recording was running as expected. For the rest of the afternoon, I focused on cleaning a sample of the data recording in Python, so as to be ready to do the job on a massive file size at the end of the trip. Each day, 40GB of data were being recorded. So at the end of the trip, there had to be around 200GB of data. The earlier I was prepared for that, the better.

![emacs_1][figure_28]

I forgot to mention that I also had to deal with the flight tickets change. And all that with a lousy internet connection. In situations like that, you realize how internet-dependent our era has transformed us. I was lucky I brought my books along. I missed reading so much and this trip was the best opportunity to start again on that mindful habit. The last stop of the day was the gym, always. I think that keeping your mind and body in good shape should be a must for every individual. Especially, when living in a boat.

## Day 5

The days at sea have become second nature to me by now. It’s impressive how fast we grow on new realities. In the beginning, I thought I would experience intense nausea, but in fact I had not even been the least dizzy so far. I am literally impressed with myself, especially after today’s bad weather. Well, maybe it wasn't that bad, but the waves were quite high and together with the strong winds, the ship was pitching a lot. And of course, the further you move from the center of gravity, the more you feel the motion.

Besides the standard daily tasks of monitoring the sensors, restarting them, documenting the timestamps, etc., I also managed to start the data processing of a small data sample from one of the sensors. It was a good first step, given that there is no internet and not much to do without connection. I also recorded a small(17mins) HD video trying to monitor the bending of the hull in rough weather. It is amazing plus scary to watch it bending by looking from the bridge. You see a wave hitting the bow, and how it transmits its frequency to the rest of the hull coming right towards you. **An absolute must see**!

<a href="http://www.youtube.com/watch?feature=player_embedded&v=1h1XmmPZM18
" target="_blank"><img src="http://img.youtube.com/vi/1h1XmmPZM18/0.jpg" 
alt="IMAGE ALT TEXT HERE" width="100%" height="580" border="10" /></a>

I talked to the captain and the officers about various things lucking from my understanding of life at sea and of how procedures work while sailing. At the end of the day, since I was missing some cardio activity and after being at the gym for two days in a row, I decided to do 30mins of intense running intervals up and down the stairs to the bridge. I managed to climb 6 times from the upper deck to the bridge and down (which is similar to a 10-floor-building) with 45sec of rest after each interval. After a long day, it was time for updating my geolocation at the live map and finally have some good rest for the last 24 hours of that trip.

## Day 6

All good (and bad) things, eventually come to an end and this is the last day of this trip. It started like all the other days with a good breakfast at 07:00, a coffee at the bridge around 07:30, the monitoring of the sensor recording and finally starting on some work. 

Today, I finalized the python script that does the first filtering and cleaning of the raw data coming from the XSENS sensors. Specifically, as mentioned above, each sensor logs 20GB per day. Most of this information is not relevant to my project, so I managed to use this initial dataset as input into a script that exports the same file, but first minimizes its size by 90%. Apart from that, I rebuilt its shape in a way that it serves the scope of the project.

At this point, it is also useful to mention that the main interest of this project was on the inaccurate measurements of the speed log and underline how one can avoid such issues with the lowest possible investment. It doesn't happen often that the speed log is giving the wrong measurements, but when it does, it creates a whole mess either to the officers that navigate the ship and to the company that monitors the consumption based on these measurements. I was lucky to be present at such an event while onboard! The speed log apparently started increasing consecutively for almost 3 hours. It was logging speed measurements up to 30 knots, which is impossible to happen, given the constant RPM and always based on the speed trials. Below is a snapshot from the navigation system, indicating the ocean current intensity of 12.5 knots.

![false_1][figure_31]

Apparently, this incident was meant to happen. As a result of this observation, my endless questions to the officers and the captain helped me learn the most about the frequency and the geolocation where they have experienced this incident before. Each of them gave me a different story and an indispensable experience that I would never acquire otherwise. And the good thing is that they don't always sail on the same ship, so they are a good sample to base my assumptions on.

After that amazing outcome -that brought me to my highest satisfaction about knowledge on the field during this trip- and after the greatest medium-raw dinner steak (on Friday nights the cooks are doing some magic) I went straight to bed for my short nap, meant to last until we reached the port of Hong Kong. 

We finally reached the port of Hong Kong at 01:00 of Saturday early hours. The pilot was then called to drive us towards our slot at the terminal. I enjoyed the last moments of my journey with a few night shots of Hong Kong.

![hk_5][figure_36]
![hk_7][figure_38]
![hk_1][figure_32]
![hk_2][figure_33]
![hk_3][figure_34]
![hk_4][figure_35]

After docking, I went straight to bed. I had to wake up early so as to take charge on some last procedures on the sensors and surely enjoy my last moments on the vessel.

## Day 7

So, 07:00 call for the usual breakfast, 07:30 on carefully recollecting the sensors from the steering gear room and the bridge, 07.45 going down to the engine room to make a copy of the data from the thrust sensor, etc, etc. The plan was that we (the captain and I) would be recollected from the agent at 11:30 in the afternoon. We were supposed to get driven straight to our hotel, where the agent would later that night again pick us up to take us to the airport. Surprisingly I had to hurry! Sharah (officer) told me that the agent was going to get me at 08:00 (3 hours earlier than planned) due to a probable delay at the immigration office! I needed to do it all faster than I thought and I got super anxious. This is where I started running like crazy, to manage and get all I mentioned above done as fast as possible, and at the same time inform the agent that he should delay my pickup for at least 1 hour, since it would be impossible for me to be ready on time.

So, I went straight to my room after having a short 5min breakfast, packed my stuff and went straight to the bridge to start the recollection, where I realized that the elevator was not working! Note here that from my deck to the bridge it is 8 levels up and to the engine room another 4 levels down. Given the fact that I would have to do all that wearing my uniform made the situation even more stressful… Finally, I managed to coordinate with the driver’s delayed pick up, so I showed up at the ship’s stairs 1 minute before the agent arrived. What a relief! Then, the agent drove me to the immigration office of Hong-Kong and after an hour of waiting, he finally drove me to the hotel. I took a shower and a short walk around the neighborhood while waiting for the captain to arrive at the hotel and have lunch with me.

One would expect an exciting ending, although there is not much more to add for this trip; apart from sleeping and then waving around at the airport for hours, until my flight departed at 01:00. This is the end of the trip! It was a whole new world to which I was exposed to and I will definitely carry a piece of it and the people that highlighted it for my long eternal time.

![hk_6][figure_37]

You can follow me on **[Instagram](https://www.instagram.com/angelos.ikonomakis/)** if you want to see photos and stories during the trip under the hashtag #sailwithlirquenproject.



