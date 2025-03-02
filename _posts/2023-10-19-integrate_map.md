---
layout: post-map
title:  "Can we integrate a map into the blog?"
date:   2023-10-19 06:00:00 -0500
categories: software-development
---
### Commentary  
The map below is made possible by a combination of technologies that involve the use of Python, LeafletJS library, and Jekyll static site generator.  
Python was used as the programming language to connect to REST APIs that contain relevant GeoJSON information.  
LeafletJS was used as the mapping library to display the basemap as well as objects. OpenStreetMap was used for basemap.  
The LeafletJS code (HTML code block) was then embedded into a "post" written in the markdown format. The Jekyll SSG knows how to convert the HTML code-block so that a browser can render it to display the geographic information of interest.  
<div id="map"></div>

<script>
         // Starter code to show OSM tiles on a map.  
         var map = L.map('map').setView([39.983334, -82.983330], 11);
         
         L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
            maxZoom: 13,
            attribution: '&copy; Map data from <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
         }).addTo(map);

         // Add ZipCode
         var geoJSONZipCode = new L.GeoJSON.AJAX(["https://www.mohitmandokhot.com/_data/43235.json"])
         geoJSONZipCode.addTo(map)
         
         // Interactivity enabled code
         var popup = L.popup();
         function onMapClick(e) {
            popup
               .setLatLng(e.latlng)
               .setContent("You clicked the map at " + e.latlng.toString())
               .openOn(map);
         }
         map.on('click', onMapClick);

</script>  

