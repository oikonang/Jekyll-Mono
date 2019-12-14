---
layout: post
title: A week sailing on Maersk Lirquen
author: Angelos Ikonomakis
---
[figure_1]: ../images/Lirquen/xsens.png "Figure 1"
In this post, I will share some facts about the trip I am about to do (I am currently flying to Singapore by the way) on the next days to come. The main subject of this trip(as the title claims) is sailing on a 300m container vessel for 7 days, from Singapore to Busan(South Korea). The main purpose of the trip is to collect inertial data which will be sourced as measurement inputs into a nonlinear model I have built, for the purpose of my PhD project.

## Overview

During the trip, once per day, I will update my GPS location on the **live map** below. Additionally, you can follow me on **[Instagram](https://www.instagram.com/angelos.ikonomakis/)** if you want to see photos and stories during the trip under the hashtag #sailwithlirquenproject. The total trip duration will be 11 days, due to me living in Copenhagen and having to fly to Singapore for the embarkation, and flying back from Busan after the disembarkation. 

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
<link rel="stylesheet" href="https://cdn.leafletjs.com/leaflet-0.7/leaflet.css"/>
<script src="https://cdn.leafletjs.com/leaflet-0.7/leaflet.js"></script>
<script src="https://d3js.org/d3.v4.min.js" type="text/javascript"></script>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>

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
marker_finish.bindPopup("<b>Finishing Point!</b>").openPopup();

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
`;
//1,2017-07-05 22:21:22,4.745150538820687,108.09010738495566,1
//2,2017-07-06 23:42:11,10.246243937711045,112.47736388487485,1

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
            div.html("<h4>Realtime Location</h4>" + "<br/>" + "<strong>Starting point!</strong>"+ "<br/>" + "Date: " + d.date + " UTC")  
        }
        else if(+d.state == 1){
            // Write staff on tooltip
            div.html("<h4>Realtime Location</h4>" + "<br/>" + "Day " + d.day + "<br/>" + "Date: " + d.date + " UTC")  
        }
        else if(+d.state == 2){
            // Write staff on tooltip
            div.html("<h4>Realtime Location</h4>" + "<br/>" + "<strong>Finish point</strong>" + "<br/>" + "Total Days " + d.day + "<br/>" + "Date: " + d.date + " UTC")  
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

A short overview of the sensors that will be installed on the vessel, is described on the image below:

![xsens_overview][figure_1]

Unfortunately, due to confidentiality I am not allowed to share any delails regarding the purpose, the technical requirements, the software and hardware handling. So, stay tuned by following me on **[Instagram](https://www.instagram.com/angelos.ikonomakis/)**, and let the journey begin! 


