---
title:  "Australia's Tennis Data - a Visual data story"
date:   2018-09-16 15:04:23
categories:  
tags: [Projects]
outside_link: "N"
link: "jadhosn.github.io/projects/tennis-vis/index.html"
---



<script src="https://d3js.org/d3.v5.js"></script>
<script>
//width and height
var width = 800;
var height = 600;
var padding = 40;


d3.csv('../projects/tennis-vis/data.csv')
    .then(function(data) {

        var xScale = d3.scaleLinear()
            .domain(d3.extent(data, function(d) { return +d.WinPercentage; }))
            .range([0, width]);

        var yScale = d3.scaleLinear()
            .domain(d3.extent(data, function(d) { return +d.TotalGames; }))
            .range([height,0]);

        var xAxis = d3.axisBottom().scale(xScale).ticks(20);

        var yAxis = d3.axisLeft().scale(yScale).ticks(20);

        var color = d3.scaleOrdinal()
            .range(["#1b70fc", "#faff16", "#d50527", "#158940", "#f898fd", "#24c9d7", "#cb9b64", "#866888", "#22e67a", "#e509ae", "#9dabfa", "#437e8a", "#b21bff", "#ff7b91", "#94aa05", "#ac5906", "#82a68d", "#fe6616", "#7a7352", "#f9bc0f", "#b65d66", "#07a2e6", "#c091ae", "#8a91a7", "#88fc07", "#ea42fe", "#9e8010", "#10b437", "#c281fe", "#f92b75", "#07c99d", "#a946aa", "#bfd544", "#16977e", "#ff6ac8", "#a88178", "#5776a9", "#678007", "#fa9316", "#85c070", "#6aa2a9", "#989e5d", "#fe9169", "#cd714a", "#6ed014", "#c5639c", "#c23271", "#698ffc", "#678275", "#c5a121", "#a978ba", "#ee534e", "#d24506", "#59c3fa", "#ca7b0a", "#6f7385", "#9a634a", "#48aa6f", "#ad9ad0", "#d7908c", "#6a8a53", "#8c46fc", "#8f5ab8", "#fd1105", "#7ea7cf", "#d77cd1", "#a9804b", "#0688b4", "#6a9f3e", "#ee8fba", "#a67389", "#9e8cfe", "#bd443c", "#6d63ff", "#d110d5", "#798cc3", "#df5f83", "#b1b853", "#bb59d8", "#1d960c", "#867ba8", "#18acc9", "#25b3a7", "#f3db1d", "#938c6d", "#936a24", "#a964fb", "#92e460", "#a05787", "#9c87a0", "#20c773", "#8b696d", "#78762d", "#e154c6", "#40835f", "#d73656", "#1afd5c", "#c4f546", "#3d88d8", "#bd3896", "#1397a3", "#f940a5", "#66aeff", "#d097e7", "#fe6ef9", "#d86507", "#8b900a", "#d47270", "#e8ac48", "#cf7c97", "#cebb11", "#718a90", "#e78139", "#ff7463", "#bea1fd"])
        //colors taken from https://jnnnnn.blogspot.com/2017/02/distinct-colours-2.html

        var shrink = d3.scaleSqrt()
            .domain(d3.extent(data, function(d) { return +d.wins; }))
            .range([10,35]);

        var tooltip = d3.select("div#example")
            .append('div')
            .attr("class",'tooltip')
            .style('opacity',0);

        var svg = d3.select("div#example")
            .append("svg")
            // .classed("svg-container", true)
            .attr("width", width)
            .attr("height", height)
            // .attr('class', 'chart')
            .attr("viewBox", "0 0 900 700")
            //.attr("preserveAspectRatio", "xMinYMin meet")
            .append("g")
            .attr("transform", "translate(" + padding + "," + padding + ")");

        svg.selectAll(null)
            .data(data)
            .enter()
            .append("circle")
            .attr("class",function(d,i){
                return "p"+d.countrynb;
            })
            .attr("cx", function(d) {
                return xScale(d.WinPercentage);
            })
            .attr("cy", function(d) {
                return yScale(d.TotalGames);
            })
            .attr("r", function(d){
                return shrink(d.wins);
            })
            .attr("fill", function(d){
                return color(d.countrynb);
            })
            .on('mouseover', function (d, i) {
                d3.selectAll("circle")
                    .filter(function(d1){
                       return d1.countrynb != d.countrynb;
                    })
                    .attr("opacity",0.05)

                tooltip.transition()
                    .duration(200)
                    .style("opacity", .9);

                tooltip	.html("Country: " +d.country1 + "<br/>" + d.player1)
                     // .style("bottom", xScale(d.WinPercentage) + "px")
                     // .style("left", yScale(d.TotalGames) + "px");

            })
            .on('mouseout', function (d,i) {
                // svg.selectAll('circle.p'+d.countrynb)
                //     .attr('fill', function(d){
                //         return color(d.countrynb);
                //     })
                d3.selectAll("circle")
                    .filter(function(d1){
                        return d1.countrynb !=d.countrynb;
                    })
                    .attr("opacity",1)
                tooltip.transition()
                    .duration(200)
                    .style("opacity", 0);

            })
            .on("click", function (d,i) {
                // d3.select("svg")
                //     .style("opacity",0);
                update(i);
            })

        svg.append('text')
            .attr("transform","translate("+(width-100)/2+","+(height+padding+650)/2+")")
            .text("Percentage of winning")

        svg.append('text')
            .attr("transform","translate("+0+","+0+")")
            .text("Total # of games")

        svg.append("g")
            .attr("class", "x axis")
            .attr("transform", "translate(0," + height + ")")
            .call(xAxis);

        svg.append("g")
            .attr("class", "y axis")
            .call(yAxis);

        var r = Math.min(width, height)/2;

        var svg2 = d3.select("div#example")
            .append("svg")
            .attr("width", width)
            .attr("height", height)
            .attr("viewBox", "0 0 900 700")
            .append("g")
            .attr("transform", "translate(" + 300 + "," + 300 + ")");

        function update(k)
        {
            console.log(k);

            //remove previous pie chart
            svg2.selectAll("*").remove();

            var categories = [];
            categories.push(data[k].wins);
            categories.push(data[k].losses);

            var pie2 = d3.pie()
                .value(function(d,i)
                {
                    return categories[i];
                });

            svg2.selectAll("null")
                .data(pie2(categories))
                .enter()
                .append("g")
                .append("path")
                .attr("fill", function(d,i) {return color(i); })
                .attr("d", d3.arc()
                    .outerRadius(r)
                    .innerRadius(0));

            svg2.append('rect')
                .attr('x',350)
                .attr('y',0)
                .attr('width',20)
                .attr('height',20)
                .style('fill',color(0));

            svg2.append('text')
                .attr("transform","translate("+376+","+(11)+")")
                .text("Number of games won")

            svg2.append('rect')
                .attr('x',380)
                .attr('y',30)
                .attr('width',20)
                .attr('height',20)
                .style('fill',color(1));

            svg2.append('text')
                .attr("transform","translate("+406+","+(46)+")")
                .text("Number of games lost")

        }

    })
</script>
<div id="example"></div>