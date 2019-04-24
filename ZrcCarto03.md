````javascript
/* table as JavaScript object*/
var cities = [
		{city:"Zurich", lat:47, lng:9, pop:402762},
		{city:"Tokyo", lat:36, lng:140, pop:9467490},
		{city:"New York", lat:43, lng:-75, pop:8537673},
		{city:"Sydney", lat:-33, lng:151, pop:5005400},
		{city:"Paris", lat:48, lng:2, pop:2206488},
		{city:"Moscow", lat:55, lng:37, pop:11503501},
		{city:"Mumbai", lat:18, lng:72, pop:12478447},
		{city:"London", lat:51, lng:0, pop:8787892},
		{city:"Brasilia", lat:-15, lng:-47, pop:2570160},
		{city:"Berlin", lat:52, lng:13, pop:3574830},
		{city:"Madrid", lat:40, lng:-42, pop:3182981},
		{city:"Shanghai", lat:31, lng:121, pop:23019148},
	]


	/* Write your sorting function here*/
  
  cities.sort((a,b) => a.pop - b.pop);

		
    
  createTable();
  
  function createTable(){
		var globalCounter = 0;
		var tbody = document.getElementById('tbody');
		var thead = document.getElementById('thead');
    
    let trNode = document.createElement("tr");
    thead.appendChild(trNode);
    
    let headers = ["City", "Latitude", "Longitude", "Population"];
    
    for (let i = 0; i< 4; i++ ) {
      let thNode = document.createElement("th");
      thNode.textContent = headers[i];
      trNode.appendChild(thNode);
    }
    
    let propNames = ["city", "lat", "lng", "pop"];
    
    for (let element of cities) {
      let trNode = document.createElement("tr");
      tbody.appendChild(trNode);
    
      for (let i = 0; i< 4; i++ ) {
        let tdNode = document.createElement("td");
        tdNode.textContent = element[propNames[i]];
        trNode.appendChild(tdNode);
      }      
    }
	}  

	function createTable2(){
		var globalCounter = 0;
		var tbody = document.getElementById('tbody');
		var thead = document.getElementById('thead');
		thead.innerHTML += "<tr><th>" + 'City' + "</th>" + "<th>" + 'Latitude' + "</th>" + "<th>" + 'Longitude' 		+ "</th>" + "<th>" + 'Population' + "</th></tr>"
		for (var i = 0; i < cities.length; i++) {
			var tr = "<tr>";
			tr += "<td>" + cities[i].city + "</td>" + "<td>" + cities[i].lat.toString() + "</td>" + "<td>" + 				cities[i].lng.toString() + "</td>" + "<td>" + cities[i].pop.toString() + "</td></tr>";
			tbody.innerHTML += tr;
		}
	}
````						  
						  
