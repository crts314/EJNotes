# EJ exrcices

## Chapter 14 - The Document Object Model

### Exercise 1 - Build a table

<h1>Mountains</h1>

<div id="mountains">

  <table id="mountainTable">
    <tr>
      <th>name</th>
      <th>height</th>
      <th>place</th>
    </tr>



  </table>

</div>

<script>
  const MOUNTAINS = [
    {name: "Kilimanjaro", height: 5895, place: "Tanzania"},
    {name: "Everest", height: "8848", place: "Nepal"},
    {name: "Mount Fuji", height: "3776", place: "Japan"},
    {name: "Vaalserberg", height: "323", place: "Netherlands"},
    {name: "Denali", height: "6168", place: "United States"},
    {name: "Popocatepetl", height: "5465", place: "Mexico"},
    {name: "Mont Blanc", height: "4808", place: "Italy/France"}
  ];

  // Input :
  //   - type: html tag of the main element we want to create
  //   - children: array of nodes that should be added to this main element
  //               (if the child is a string, first create a textNode)
  // Output :
  //   - new node corresponding to the main element with 
  //     children already appended to it.
  //  
  
  function elt(type, ...children) {
    let node = document.createElement(type);
    for (let child of children) {
      if (child instanceof HTMLElement) 
        node.appendChild(child);
      else
        node.appendChild(document.createTextNode(child));
    }
    return node;
  }  


  // Input : name , height , place of one mountain
  // Output : ElementNode corresponding to the html row for this mountain
  
  function addRow(name, height, place) {    
    return elt("tr", 
               elt("td", name), 
               elt("td", height),
               elt("td", place));
  }
  
  for (i = 0; i < MOUNTAINS.length; i++) {
    let name = MOUNTAINS[i].name;
    let height = MOUNTAINS[i].height;
    let place = MOUNTAINS[i].place;
    
    let row = addRow(name, height, place);
    let fc = document.getElementById("mountainTable").append(row);
  }
  
  /*
  let nodeRow = document.createElement("tr");
  let nodeCellName = document.createElement("td");
  let nodeCellHeight = document.createElement("td");
  let nodeCellPlace = document.createElement("td");
  let textName = document.createTextNode("Kilimanjaro");
  let textHeight = document.createTextNode("5895");
  let textPlace = document.createTextNode("Tanzania");
  
  nodeCellName.appendChild(textName);
  nodeCellPlace.appendChild(textPlace);
  nodeCellHeight.appendChild(textHeight);
  nodeRow.appendChild(nodeCellName);
  nodeRow.appendChild(nodeCellHeight);
  nodeRow.appendChild(nodeCellPlace);
  document.getElementById("mountainTable").appendChild(nodeRow);       
   */
  
  /*
  let myheader = document.createElement("h1");
  let textNode = document.createTextNode("hello");
  myheader.appendChild(textNode);
  document.body.appendChild(myheader); 
  */
</script>

### Exercise 2 - Elements by tag name

<h1>Heading with a <span>span</span> element.</h1>
<p>A paragraph with <span>one</span>, <span>two</span>
  spans.</p>

<script>
 

  
  function byTagName(node, tagName, array = []) {    
    if (node.nodeName.toLowerCase() == tagName.toLowerCase()) {
      array.push(node);
    }
    for (let element of node.children) {
      byTagName(element, tagName, array);
    }
    return array;
  }


  console.log(byTagName(document.body, "h1").length);
  // → 1
  console.log(byTagName(document.body, "span").length);
  // → 3
  let para = document.querySelector("p");
  console.log(byTagName(para, "span").length);
  // → 2
</script>

### Exercise 3 - The cat’s hat

<style>body { min-height: 200px }</style>
<img src="img/cat.png" id="cat" style="position: absolute">
<img src="img/hat.png" id="hat" style="position: absolute">

<script>
  let cat = document.querySelector("#cat");
  let hat = document.querySelector("#hat");

  let CatAngle = 0;
  let lastTime = null;
  function animate(time) {
    if (lastTime != null) CatAngle += (time - lastTime) * 0.001;
    let HatAngle = CatAngle + Math.PI;
    lastTime = time;
    cat.style.top = (Math.sin(CatAngle) * 40 + 40) + "px";
    cat.style.left = (Math.cos(CatAngle) * 200 + 230) + "px";
    hat.style.top = (Math.sin(HatAngle) * 40 + 40) + "px";
    hat.style.left = (Math.cos(HatAngle) * 200 + 230) + "px";
    
    // Your extensions here.

    requestAnimationFrame(animate);
  }
  requestAnimationFrame(animate);
</script>
