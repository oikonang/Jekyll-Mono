---
layout: post
title: Visualization of Titanic Disaster using D3
author: Angelos Ikonomakis
---
[figure_1]: ../images/figure_1.png "Figure 1"
[figure_2]: ../images/figure_2.png "Figure 2"
[figure_3]: ../images/figure_3.png "Figure 3"
[figure_4]: ../images/figure_4.png "Figure 4"
[figure_5]: ../images/figure_5.png "Figure 5"
[figure_6]: ../images/figure_6.png "Figure 6"
[figure_7]: ../images/figure_7.png "Figure 7"    

## Overview

In an attempt to experimentize with the visualization tools (Dimple.js, D3.js, visualization design principles, visual encodings, HTML, CSS, SVG) I created a polished data visualization that tells a story about survival rates of Titanic disaster, allowing a reader to explore trends or patterns.

<html>
<head>
  <meta charset="utf-8">

  <script src="http://d3js.org/d3.v3.min.js"></script>
  <script src="http://dimplejs.org/dist/dimple.v2.0.0.min.js"></script>

  <style type="text/css">
    text.dimple-axis{
      font-size: 50px;
      font-weight: bold;
      font-style: helvetica;
      margin-left: 100px;
    }
    text.dimple-storyboard-label{
      opacity: 1;
    }
  </style>

</head>
<body>
    <div id="chartContainer"></div>
    <script type="text/javascript">
      var svg = dimple.newSvg("#chartContainer", 1250, 580);
      d3.csv("DATA/titanic_3.csv", function (data) {
      
        // Create a notification chart at the right bottom of the chart to give an overview of data
        var notification = new dimple.chart(svg, data);
        notification.setBounds(980, 250, 200, 200);
        svg.selectAll("title_text")
        .data(["40.62% of the total 2024 Crew", 
          "and Passengers Survived.",
          "",
          " 32.06% of whom were Male and ",
          "67.93% of whom were Female."
        ])
        .enter()
        .append("text")
        .attr("x", 980)
        .attr("y", function (d, i) { 
          return 300 + i * 22; 
        })
        .style("font-family", "arial")
        .style("font-size", "18px")
        .style("color", "Black")
        .text(function (d) { 
          return d; 
        });
          
        // Create the indicator chart on the right of the main chart
        var indicator = new dimple.chart(svg, data);
          
        // Pick green as the default and purple for the selected class
        var defaultColor = indicator.defaultColors[3];
        var indicatorColor = indicator.defaultColors[5];
          
        var frame = 4000;
        var firstTick = true;
        indicator.setBounds(980, 80, 253, 150);
          
        // Add Passenger Class along the y axis
        var y = indicator.addCategoryAxis("y", "Pclass");
        y.addOrderRule("Pclass", "desc");
          
        // Use Survived for bar size and hide the axis
        var x = indicator.addPctAxis("x", "survived");
          x.hidden = true;
          
        // Add the bars to the indicator and add event handlers
        var s = indicator.addSeries(null, dimple.plot.bar);
        s.getTooltipText = function(e){
          return ["Passenger Class : " + e.cy];
        };
          
        // On Click of the indicator bar
        s.addEventHandler("click", function (e) {
          // Pause the animation
          story.pauseAnimation();
  
          // If it is already selected resume the animation
          // otherwise pause and move to the selected Pclass
          if (e.yValue === story.getFrameValue()) {
            story.startAnimation();
          } 
          else {
            story.goToFrame(e.yValue);
            story.pauseAnimation();
          }
        });
          
        // Draw the side chart
        indicator.draw();
          
        // Remove the title from the y axis
        y.titleShape.remove();
          
        // Remove the lines from the y axis
        y.shapes.selectAll("line,path").remove();
       
        // Move the y axis text inside the plot area
        y.shapes.selectAll("text")
        .style("text-anchor", "start")
        .style("font-size", "18px")
        .style("text-align", "center")
        .style("font-weight", "bold")
        .attr("transform", "translate(15, 0.3)");
        svg.selectAll("title_text")
        .data(["Click one of the below tabs to select,",
          "pause and resume between classes."
        ])
        .enter()
        .append("text")
        .attr("x", 980)
        .attr("y", function (d, i) { 
          return 50 + i * 13; 
        })
        .style("font-family", "arial")
        .style("font-size", "12px")
        .style("color", "Red")
        .text(function (d) { 
          return d; 
        });
          
        // Manually set the bar colors
        s.shapes
        .attr("rx", 5)
        .attr("ry", 5)
        .style("fill", function (d) { 
          return (d.y === 1 ? indicatorColor.fill : defaultColor.fill) 
        })
        .style("stroke", function (d) { 
          return (d.y === 1 ? indicatorColor.stroke : defaultColor.stroke) 
        })
        .style("opacity", 0.7);
          
        // Draw the main chart
        var bar = new dimple.chart(svg, data);
        bar.setBounds(100, 120, 850, 400);
          
        var x = bar.addCategoryAxis("x", ["sex","age_group"]);
        x.addOrderRule("sex");
        x.addGroupOrderRule(["Children [0-18]", 
          "Adults [19-40]", 
          "Middle-Aged [41-60]", 
          "Seniors [61+]"
        ]);
        x.fontSize = "13px";
        x.fontFamily = "Arial";
        var y = bar.addMeasureAxis("y","survival_rate");
        y.ticks = 20;
        y.overrideMax = 100;
        y.showGridlines = false;
        y.title = "Survival Rate per class in (%)";
        y.fontSize = "13px";
        y.fontFamily = "helvetica";
        var b = bar.addSeries(['age_group'], dimple.plot.bar);
        b.addOrderRule(["Children [0-18]", 
          "Adults [19-40]", 
          "Middle-Aged [41-60]", 
          "Seniors [61+]"
        ]);
        bar.addLegend(100, 75, 650, 60);
          
        // Adding a title to the plot
        svg.append('text')
        .attr("x", 550)
        .attr("y", 30)
        .style("text-anchor", "middle")
        .style("font-family", "arial")
        .style("font-weight", "bold")
        .style("font-size", "20px")
        .text("Survival Rate of the Passengers of Titanic");
        svg.selectAll("title_text")
        .data(["Age bands of the Passengers of Titanic."])
        .enter()
        .append("text")
        .attr("x", 100)
        .attr("y", 65)
        .style("font-family", "helvetica")
        .style("font-size", "12px")
        .style("color", "Black")
        .text(function (d) { 
          return d; 
        });
        var counter = 1;
          
        // Add a storyboard to the main chart and set the tick event
        var story = bar.setStoryboard("Pclass", function onTick(e) {
          counter += 1;
          if(counter == 5){
            story.pauseAnimation();
          }
          if (!firstTick) {
            // Color all shapes the same
            s.shapes
              .transition()
              .duration(frame / 2)
              .style("fill", function (d) { 
                return (d.y === e ? indicatorColor.fill : defaultColor.fill) 
              })
              .style("stroke", function (d) { 
                return (d.y === e ? indicatorColor.stroke : defaultColor.stroke) 
              });
          }
          firstTick = false;
        });
  
        // Change the frame duration
        story.frameDuration = frame;
        
        // Order the storyboard by Pclass
        story.addOrderRule("Pclass");
        bar.ease = 'bounce';
        bar.draw(500);
          
        // Orphan the legends as they are consistent but by default they
        // will refresh on tick
        bar.legends = [];
      });
    </script>
</body>
</html>

<!--
```python
# Log into the EC2 instance created from a local terminal
ssh -i "~/.ssh/RandomKey.pem" ubuntu@ec2 -54-165-250-39.compute -1. amazonaws.com
```
![alt text][figure_1]

```python
# Upload the dataset to the instance from a local terminal   
scp -i ~/.ssh/RandomKey.pem ~/path_to_datafile/RC_2015 -01.bz2 ubuntu@ec2 -54-165-250-39.compute -1.amazonaws.com:~/data/RC_2015 -01. bz2
```
![alt text][figure_2]

Install dependencies to the instance in order to wrangle the data from distance using the server's processing power. Firstly we need to download Anaconda to the instance.

```python
# Download Anaconda to the server from a server terminal
wget https://repo.continuum.io/archive/Anaconda2-4.2.0-Linux-x86_64. sh
```
![alt text][figure_3]

```python
# Install Anaconda to the instance from a server terminal
bash Anaconda2-4.2.0-Linux-x86_64.sh
```
![alt text][figure_4]


Settle a server **ipython notebook** for remote handling python reports and querying data.

```python
# Open ipython in server environment and do the following command
ipython

# It will prompt a python interactive window that works in the bash environment
# Then create a password by typing the below commands
from IPython.lib import passwd passwd ()

# You will be prompted to enter and verify a password 
# (You should remember it. This will be the password to log to the remote ipython notebook)
# When done copy the generated sha1 key
```
![alt text][figure_5]


Locate the **ipython_notebook_config.py** file in the .jupyter directory of the server and paste the key in the appropriate field along with the rest of the uncommented lines.
```python
# If you don’t already have a ipython_notebook_config.py file create one using the below command 
jupyter notebook --generate -config
```
![alt text][figure_6]

Now the connection is established. 

```python
# Write the below command to launch ipython
ipython notebook
```

You will be prompted to open a browser. You should write    
*https://[ip adress of the server]:[port]*

![alt text][figure_7]

## Step 2 
-----

To be continued..
-->
