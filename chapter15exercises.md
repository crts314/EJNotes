# EJ exrcices

## Chapter 15 - Handling Events

### Exercise 1 - Balloon

<p id="firstP">🎈</p>
<p id="secondP" style="display: none">💥</p>

<script>
  let size = 20;
  
  /*
  function setSize(s) {
    let para = document.body.querySelector("p");
    para.style.fontSize = s + "px";
  }
    
  setSize(size);
  */
  
  let para1 = document.getElementById("firstP");
  let para2 = document.getElementById("secondP");
  
  para1.style.fontSize = size + "px";
  
  window.addEventListener("keydown", event => {
    if (event.key == "ArrowUp") {  
      size = size + size / 10; 
      if (size > 5000) {
        para1.style.display = "none";
        para2.style.display = "block";
      }   
      else {
        para1.style.fontSize = size + "px";
      }
    }      
    event.preventDefault();
  });
  
  
  window.addEventListener("keydown", event => {
    if (event.key == "ArrowDown") {     
      size = size - size / 10; 
      para1.style.fontSize = size + "px";
    }
    event.preventDefault();
  });
  
   
  //attach this handler to window.
  
</script>

### Exercise 2 - Balloon

<style>
  .trail { /* className for the trail elements */
    position: absolute;
    height: 6px; width: 6px;
    border-radius: 3px;
    background: teal;
  }
  body {
    height: 300px;
  }
</style>

<script>
  window.addEventListener("mousemove", event => {
    let trail = document.createElement("div");
    trail.className = "trail";               
    trail.style.left = (event.clientX) + "px";
    trail.style.top = (event.clientY) + "px";
    document.body.appendChild(trail);  
   setTimeout(() => document.body.removeChild(trail), 100); 
  });
  
</script>
