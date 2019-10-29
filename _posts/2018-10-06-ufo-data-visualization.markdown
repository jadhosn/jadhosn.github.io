---
title:  "UFO Sightings - a Visual data story"
date:   2018-10-06 15:04:23
categories:  
tags: [Project]
outside_link: "N"
link:
---
<head>
    <style>

        .states :hover {
            fill: red;
        }

        .state-borders {
            fill: none;
            stroke: #000000;
            stroke-width: 0.5px;
        }
        .bar{
            fill: blue;
        }

    </style>
</head>
<svg width="1000" height="600" id="svg1"></svg>
<svg width="960" height="600" id="svg2"></svg>
<script src="https://d3js.org/d3.v4.min.js"></script>
<script src="https://d3js.org/topojson.v2.min.js"></script>
<script>
var path = d3.geoPath();

let color = d3.scaleOrdinal(d3.schemeCategory10)
    .domain([1,2,3,4,5,6])
    .range(["#e5e5ff","#ccccff","#9999ff","#3232ff","#0000b2","#000033"]);

var svg = d3.select("#svg1");


d3.csv('../../projects/ufo-vis/ufo-data.csv', function(data) {


    d3.json("https://d3js.org/us-10m.v1.json", function (error, us) {
        if (error) throw error;

        svg.append("g")
            .attr("class", "states")
            .selectAll("path")
            .data(topojson.feature(us, us.objects.states).features)
            .enter().append("path")
            .attr("d", path)
            .attr("fill", function (d,i) {
                index = Number(d.id)
                return color(data[index-1].clr);
            })
            .on('click', function(d,i){
                svg2.selectAll("*")
                    .remove()
                update(Number(d.id)-1);
            })
            .on('mouseover', function(d,i){
                index = Number(d.id)
                console.log(data[index-1].state, data[index-1].clr)
                return document.getElementById('state').innerHTML=data[index-1].state;
            })

        svg.append("path")
            .attr("class", "state-borders")
            .attr("d", path(topojson.mesh(us, us.objects.states, function(a, b) { return a !== b; })));

        svg.append('rect')
            .attr('y',200)
            .attr('x',910)
            .attr('width',20)
            .attr('height',20)
            .style('fill',color(6));

        svg.append('rect')
            .attr('y',220)
            .attr('x',910)
            .attr('width',20)
            .attr('height',20)
            .style('fill',color(5));

        svg.append('rect')
            .attr('y',240)
            .attr('x',910)
            .attr('width',20)
            .attr('height',20)
            .style('fill',color(4));

        svg.append('rect')
            .attr('y',260)
            .attr('x',910)
            .attr('width',20)
            .attr('height',20)
            .style('fill',color(3));

        svg.append('rect')
            .attr('y',280)
            .attr('x',910)
            .attr('width',20)
            .attr('height',20)
            .style('fill',color(2));

        svg.append('rect')
            .attr('y',300)
            .attr('x',910)
            .attr('width',20)
            .attr('height',20)
            .style('fill',color(1));

        svg.append('text')
            .attr("transform","translate("+931+","+(215)+")")
            .text("3000+")

        svg.append('text')
            .attr("transform","translate("+931+","+(235)+")")
            .text("1400-3000")

        svg.append('text')
            .attr("transform","translate("+931+","+(255)+")")
            .text("1200-1400")

        svg.append('text')
            .attr("transform","translate("+931+","+(275)+")")
            .text("800-1200")

        svg.append('text')
            .attr("transform","translate("+931+","+(295)+")")
            .text("450-800")

        svg.append('text')
            .attr("transform","translate("+931+","+(315)+")")
            .text("0-450")

        var padding = 200;
        var width = 600-padding;
        var height = 500-padding;


        var x = d3.scaleBand()
            .range([0, width])
            .padding(0.1);

        var y = d3.scaleLinear()
            .range([height,0]);

        var svg2 = d3.select("#svg2")
            .append('g')
            .attr("transform", "translate(" + 100 + "," + 100 + ")");

        var xAxis = d3.axisBottom(x);

        var yAxis = d3.axisLeft(y);


        function update(i) {

            var points = [];

            points.push(data[i].Y2001);
            points.push(data[i].Y2002);
            points.push(data[i].Y2003);
            points.push(data[i].Y2004);
            points.push(data[i].Y2005);
            points.push(data[i].Y2006);
            points.push(data[i].Y2007);
            points.push(data[i].Y2008);
            points.push(data[i].Y2009);
            points.push(data[i].Y2010);
            points.push(data[i].Y2011);
            points.push(data[i].Y2012);

            x.domain(
                points.map(function(d,i){
                return 2001+i;
            }));

            y.domain(d3.extent(points, function(d) { return +d; }))

            svg2.append("g")
                .attr("class", "x axis")
                .attr("transform", "translate(0," + height + ")")
                .call(xAxis);

            svg2.append("g")
                .attr("class", "y axis")
                .call(yAxis);

            svg2.selectAll("bar")
                .data(points)
                .enter()
                .append("rect")
                .attr("class","bar")
                .attr('y', function(d,i){
                    return y(d);
                })
                .attr("x",function(d,i){
                    return x(2001+i);
                })
                .attr("height", function(d) { return height - y(d); })
                .attr("width", (width/12)-5);

            svg2.append("text")
                .attr("transform","translate("+0+","+0+")")
                .text("count")


            svg2.append("text")
                .attr("transform","translate("+403+","+(312)+")")
                .text("year")

        }
    });

});
</script>
<div id="example"></div>

