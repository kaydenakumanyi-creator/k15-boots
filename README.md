<html lang="en">

<head>

<meta charset="UTF-8">

<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 40px 20px;
  font-family: Arial, Helvetica, sans-serif;
  background: transparent;
  color: #222;
}

.comparison-container {
  max-width: 1000px;
  margin: auto;
}


/* ================================
   SEARCH AREA
================================ */

.boot-selection {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  margin-bottom: 25px;
}

.boot-selector {
  position: relative;
}

.boot-selector h3 {
  margin: 0 0 10px;
  font-size: 16px;
  font-weight: 600;
  color: #333;
}

.search-wrapper {
  position: relative;
}

.boot-search {
  width: 100%;
  padding: 15px 17px;
  border: 1px solid #ddd;
  border-radius: 13px;
  background: #f7f7f7;
  font-size: 15px;
  outline: none;

  transition:
    border 0.2s ease,
    box-shadow 0.2s ease,
    background 0.2s ease;
}

.boot-search:focus {
  background: white;
  border-color: #999;

  box-shadow:
    0 0 0 3px rgba(0,0,0,0.05);
}


/* ================================
   SUGGESTIONS
================================ */

.suggestions {
  position: absolute;

  top: calc(100% + 7px);

  left: 0;
  right: 0;

  background: white;

  border-radius: 14px;

  border: 1px solid #e5e5e5;

  box-shadow:
    0 12px 35px rgba(0,0,0,0.14);

  overflow: hidden;

  z-index: 100;

  display: none;

  max-height: 350px;

  overflow-y: auto;
}

.suggestions.show {
  display: block;
}

.suggestion {
  display: flex;
  align-items: center;

  gap: 14px;

  padding: 12px 14px;

  cursor: pointer;

  transition:
    background 0.15s ease;
}

.suggestion:hover {
  background: #f3f3f3;
}

.suggestion img {
  width: 65px;
  height: 50px;

  object-fit: contain;

  border-radius: 8px;

  background: #f7f7f7;
}

.suggestion-info {
  display: flex;
  flex-direction: column;

  gap: 4px;
}

.suggestion-name {
  font-size: 14px;
  font-weight: 600;
}

.suggestion-brand {
  font-size: 12px;
  color: #888;
}


/* ================================
   SELECTED BOOT
================================ */

.selected-boot {
  display: none;

  margin-top: 10px;

  padding: 10px;

  border-radius: 13px;

  background: #f5f5f5;

  align-items: center;

  gap: 12px;
}

.selected-boot.show {
  display: flex;
}

.selected-boot img {
  width: 70px;
  height: 55px;

  object-fit: contain;

  background: white;

  border-radius: 8px;
}

.selected-info {
  flex: 1;
}

.selected-name {
  font-weight: 600;
  font-size: 14px;
}

.selected-brand {
  color: #888;
  font-size: 12px;
  margin-top: 4px;
}

.remove-boot {
  border: none;
  background: transparent;

  cursor: pointer;

  font-size: 18px;

  color: #999;
}

.remove-boot:hover {
  color: #333;
}


/* ================================
   COMPARE BUTTON
================================ */

.compare-container {
  width: 100%;

  display: flex;
  justify-content: center;

  margin: 20px 0 35px;
}

.compare-button {
  position: relative;

  overflow: hidden;

  border:
    1px solid rgba(255,255,255,0.15);

  outline: none;

  cursor: pointer;

  color: white;

  background:
    linear-gradient(
      145deg,
      #3b3f43,
      #17191b
    );

  padding:
    15px 36px;

  font-size: 16px;

  font-weight: 600;

  border-radius: 13px;

  box-shadow:
    0 6px 20px rgba(0,0,0,0.25),
    0 0 18px rgba(255,255,255,0.08);

  transition:
    transform 0.25s ease,
    box-shadow 0.25s ease,
    border-color 0.25s ease;
}

.compare-button::before {
  content: "";

  position: absolute;

  width: 150px;
  height: 150px;

  left: var(--mouse-x, 50%);
  top: var(--mouse-y, 50%);

  transform:
    translate(-50%, -50%);

  background:
    radial-gradient(
      circle,
      rgba(255,255,255,0.45),
      rgba(255,255,255,0.15) 30%,
      transparent 70%
    );

  opacity: 0;

  pointer-events: none;
}

.compare-button:hover::before {
  opacity: 1;
}

.compare-button:hover {
  transform: translateY(-2px);

  border-color:
    rgba(255,255,255,0.45);

  box-shadow:
    0 8px 25px rgba(0,0,0,0.3),
    0 0 8px rgba(255,255,255,0.25),
    0 0 22px rgba(255,255,255,0.25),
    0 0 45px rgba(255,255,255,0.12);
}

.compare-button.neon {
  animation:
    neonPulse 0.7s ease-out;
}

@keyframes neonPulse {

  0% {
    box-shadow:
      0 0 5px rgba(255,255,255,0.2);
  }

  40% {
    box-shadow:
      0 0 8px rgba(255,255,255,0.7),
      0 0 20px rgba(255,255,255,0.6),
      0 0 40px rgba(255,255,255,0.4);
  }

  100% {
    box-shadow:
      0 0 0 rgba(255,255,255,0);
  }

}


/* ================================
   RESULTS
================================ */

.comparison-result {
  display: none;

  margin-top: 20px;

  animation:
    fadeIn 0.4s ease;
}

.comparison-result.show {
  display: block;
}

@keyframes fadeIn {

  from {
    opacity: 0;
    transform: translateY(10px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }

}


/* ================================
   BOOT CARDS
================================ */

.boots {
  display: grid;

  grid-template-columns:
    1fr 1fr;

  gap: 20px;
}

.boot-card {
  background: white;

  border:
    1px solid #e5e5e5;

  border-radius: 18px;

  padding: 25px;

  box-shadow:
    0 5px 20px rgba(0,0,0,0.07);
}

.boot-card h2 {
  margin-top: 0;

  font-size: 22px;

  color: #333;
}

.result-image {
  width: 100%;

  height: 180px;

  object-fit: contain;

  margin-bottom: 10px;
}

.stat {
  display: flex;

  justify-content:
    space-between;

  padding: 13px 0;

  border-bottom:
    1px solid #eee;

  font-size: 15px;
}

.stat:last-child {
  border-bottom: none;
}

.stat-name {
  color: #777;
}

.stat-value {
  font-weight: 600;
  color: #333;

  text-align: right;

  max-width: 60%;
}

.winner {
  margin-top: 20px;

  padding: 15px;

  background: #f1f1f1;

  border-radius: 12px;

  text-align: center;

  font-weight: 600;
}


/* ================================
   MOBILE
================================ */

@media (max-width: 700px) {

  .boot-selection,
  .boots {
    grid-template-columns: 1fr;
  }

}

</style>

</head>


<body>


<div class="comparison-container">


  <div class="boot-selection">


    <div class="boot-selector">

      <h3>Boot 1</h3>

      <div class="search-wrapper">

        <input
          type="text"
          class="boot-search"
          id="search1"
          placeholder="Search for a boot..."
          autocomplete="off"
        >

        <div
          class="suggestions"
          id="suggestions1">
        </div>

      </div>

      <div
        class="selected-boot"
        id="selected1">
      </div>

    </div>


    <div class="boot-selector">

      <h3>Boot 2</h3>

      <div class="search-wrapper">

        <input
          type="text"
          class="boot-search"
          id="search2"
          placeholder="Search for a boot..."
          autocomplete="off"
        >

        <div
          class="suggestions"
          id="suggestions2">
        </div>

      </div>

      <div
        class="selected-boot"
        id="selected2">
      </div>

    </div>

  </div>


  <div class="compare-container">

    <button
      class="compare-button"
      id="compareButton">

      Compare Boots

    </button>

  </div>


  <div
    class="comparison-result"
    id="comparisonResult">


    <div class="boots">


      <div class="boot-card">

        <img
          class="result-image"
          id="resultImage1"
          src=""
          alt=""
        >

        <h2 id="resultBoot1">
          Boot 1
        </h2>


        <div class="stat">
          <span class="stat-name">Speed</span>
          <span class="stat-value" id="speed1">—</span>
        </div>

        <div class="stat">
          <span class="stat-name">Control</span>
          <span class="stat-value" id="control1">—</span>
        </div>

        <div class="stat">
          <span class="stat-name">Comfort</span>
          <span class="stat-value" id="comfort1">—</span>
        </div>

        <div class="stat">
          <span class="stat-name">Weight</span>
          <span class="stat-value" id="weight1">—</span>
        </div>

        <div class="stat">
          <span class="stat-name">Price</span>
          <span class="stat-value" id="price1">—</span>
        </div>

        <div class="stat">
          <span class="stat-name">Surface</span>
          <span class="stat-value" id="surface1">—</span>
        </div>

        <div class="stat">
          <span class="stat-name">Technology</span>
          <span class="stat-value" id="technology1">—</span>
        </div>

      </div>


      <div class="boot-card">

        <img
          class="result-image"
          id="resultImage2"
          src=""
          alt=""
        >

        <h2 id="resultBoot2">
          Boot 2
        </h2>


        <div class="stat">
          <span class="stat-name">Speed</span>
          <span class="stat-value" id="speed2">—</span>
        </div>

        <div class="stat">
          <span class="stat-name">Control</span>
          <span class="stat-value" id="control2">—</span>
        </div>

        <div class="stat">
          <span class="stat-name">Comfort</span>
          <span class="stat-value" id="comfort2">—</span>
        </div>

        <div class="stat">
          <span class="stat-name">Weight</span>
          <span class="stat-value" id="weight2">—</span>
        </div>

        <div class="stat">
          <span class="stat-name">Price</span>
          <span class="stat-value" id="price2">—</span>
        </div>

        <div class="stat">
          <span class="stat-name">Surface</span>
          <span class="stat-value" id="surface2">—</span>
        </div>

        <div class="stat">
          <span class="stat-name">Technology</span>
          <span class="stat-value" id="technology2">—</span>
        </div>

      </div>

    </div>


    <div
      class="winner"
      id="winner">

      ⚡ Compare your boots side-by-side

    </div>

  </div>

</div>


<script>

const boots = [

  {
    name:
      "Nike Mercurial Superfly 11 Elite FG",

    brand:
      "Nike Mercurial",

    image:
      "https://static.nike.com/a/images/t_web_pdp_535_v2/f_auto,u_9ddf04c7-2a9a-4d76-add1-d15af8f0263d,c_scale,fl_relative,w_1.0,h_1.0,fl_layer_apply/29dc7821-c782-4603-94d0-09334c0870ea/ZM+SUPERFLY+11+ELITE+FG.png",

    speed:
      "10/10",

    control:
      "8.5/10",

    comfort:
      "8.5/10",

    weight:
      "Approx. 170g",

    price:
      "£264.99",

    surface:
      "Firm Ground",

    technology:
      "Air Zoom + ZoomX + FlyWeave Ultra"

  },


  {
    name:
      "Nike Mercurial Vapor 17 Elite FG",

    brand:
      "Nike Mercurial",

    image:
      "",

    speed:
      "10/10",

    control:
      "8.5/10",

    comfort:
      "8/10",

    weight:
      "Lightweight",

    price:
      "£254.99",

    surface:
      "Firm Ground",

    technology:
      "Flylite plate + AtomKnit"

  },


  {
    name:
      "Nike Phantom Elite",

    brand:
      "Nike Phantom",

    image:
      "",

    speed:
      "8.5/10",

    control:
      "10/10",

    comfort:
      "9/10",

    weight:
      "Approx. 200g",

    price:
      "Elite price varies",

    surface:
      "Firm Ground",

    technology:
      "Gripknit + Cyclone 360"

  },


  {
    name:
      "Nike Phantom Academy",

    brand:
      "Nike Phantom",

    image:
      "",

    speed:
      "8/10",

    control:
      "8.5/10",

    comfort:
      "8.5/10",

    weight:
      "Varies",

    price:
      "Academy price varies",

    surface:
      "Firm Ground",

    technology:
      "NikeSkin + textured touch area"

  },


  {
    name:
      "Nike Tiempo Elite",

    brand:
      "Nike Tiempo",

    image:
      "",

    speed:
      "8/10",

    control:
      "9.5/10",

    comfort:
      "10/10",

    weight:
      "Approx. 200g",

    price:
      "Elite price varies",

    surface:
      "Firm Ground",

    technology:
      "FlyTouch Plus + flexible plate"

  },


  {
    name:
      "Nike Tiempo Academy",

    brand:
      "Nike Tiempo",

    image:
      "",

    speed:
      "7.5/10",

    control:
      "8.5/10",

    comfort:
      "9/10",

    weight:
      "Varies",

    price:
      "Academy price varies",

    surface:
      "Firm Ground",

    technology:
      "Synthetic upper + padded touch"

  },


  {
    name:
      "adidas X Elite FG",

    brand:
      "adidas X",

    image:
      "",

    speed:
      "9.5/10",

    control:
      "8.5/10",

    comfort:
      "8/10",

    weight:
      "Lightweight",

    price:
      "Elite price varies",

    surface:
      "Firm Ground",

    technology:
      "Speedskin + lightweight Speedframe"

  },


  {
    name:
      "PUMA FUTURE 9 Ultimate FG",

    brand:
      "PUMA FUTURE",

    image:
      "",

    speed:
      "8.5/10",

    control:
      "9.5/10",

    comfort:
      "9.5/10",

    weight:
      "Lightweight",

    price:
      "£220",

    surface:
      "Firm Ground",

    technology:
      "FUZIONPODS + 3D grip zones + FLEXGILITY"

  }

];


let selectedBoot1 = null;

let selectedBoot2 = null;


function showSuggestions(
  searchInput,
  suggestionsBox,
  selectionNumber
) {

  const search =
    searchInput.value
      .toLowerCase()
      .trim();


  suggestionsBox.innerHTML = "";


  const matches =
    boots.filter(
      boot =>

        boot.name
          .toLowerCase()
          .includes(search)

        ||

        boot.brand
          .toLowerCase()
          .includes(search)
    );


  if (matches.length === 0) {

    suggestionsBox.innerHTML = `

      <div style="
        padding:18px;
        text-align:center;
        color:#888;
        font-size:14px;
      ">

        No boots found

      </div>

    `;

    suggestionsBox.classList.add("show");

    return;
  }


  matches.forEach(
    boot => {

      const item =
        document.createElement("div");


      item.className =
        "suggestion";


      item.innerHTML = `

        ${
          boot.image

          ?

          `<img
             src="${boot.image}"
             alt="${boot.name}"
           >`

          :

          `<div style="
             width:65px;
             height:50px;
             border-radius:8px;
             background:#f1f1f1;
             display:flex;
             align-items:center;
             justify-content:center;
             font-size:10px;
             color:#999;
             text-align:center;
           ">
             Image<br>coming soon
           </div>`
        }

        <div class="suggestion-info">

          <div class="suggestion-name">
            ${boot.name}
          </div>

          <div class="suggestion-brand">
            ${boot.brand}
          </div>

        </div>

      `;


      item.addEventListener(
        "click",
        function() {

          selectBoot(
            boot,
            selectionNumber
          );

        }
      );


      suggestionsBox
        .appendChild(item);

    }
  );


  suggestionsBox.classList.add("show");

}


function selectBoot(
  boot,
  selectionNumber
) {

  if (selectionNumber === 1) {

    selectedBoot1 = boot;

    document
      .getElementById("search1")
      .value = "";

    document
      .getElementById("suggestions1")
      .classList
      .remove("show");

    showSelectedBoot(
      boot,
      "selected1"
    );

  }


  if (selectionNumber === 2) {

    selectedBoot2 = boot;

    document
      .getElementById("search2")
      .value = "";

    document
      .getElementById("suggestions2")
      .classList
      .remove("show");

    showSelectedBoot(
      boot,
      "selected2"
    );

  }

}


function showSelectedBoot(
  boot,
  elementId
) {

  const element =
    document.getElementById(
      elementId
    );


  element.innerHTML = `

    ${
      boot.image

      ?

      `<img
         src="${boot.image}"
         alt="${boot.name}"
       >`

      :

      `<div style="
         width:70px;
         height:55px;
         border-radius:8px;
         background:#fff;
         display:flex;
         align-items:center;
         justify-content:center;
         font-size:10px;
         color:#999;
         text-align:center;
       ">
         Image<br>coming soon
       </div>`
    }


    <div class="selected-info">

      <div class="selected-name">
        ${boot.name}
      </div>

      <div class="selected-brand">
        ${boot.brand}
      </div>

    </div>


    <button
      class="remove-boot"
      onclick="removeBoot('${elementId}')">

      ×

    </button>

  `;


  element.classList.add("show");

}


function removeBoot(
  elementId
) {

  const element =
    document.getElementById(
      elementId
    );


  element.innerHTML = "";

  element.classList.remove("show");


  if (
    elementId === "selected1"
  ) {

    selectedBoot1 = null;

  }


  if (
    elementId === "selected2"
  ) {

    selectedBoot2 = null;

  }

}


document
  .getElementById("search1")
  .addEventListener(
    "input",
    function() {

      showSuggestions(
        this,

        document.getElementById(
          "suggestions1"
        ),

        1
      );

    }
  );


document
  .getElementById("search2")
  .addEventListener(
    "input",
    function() {

      showSuggestions(
        this,

        document.getElementById(
          "suggestions2"
        ),

        2
      );

    }
  );


document
  .getElementById("search1")
  .addEventListener(
    "focus",
    function() {

      showSuggestions(
        this,

        document.getElementById(
          "suggestions1"
        ),

        1
      );

    }
  );


document
  .getElementById("search2")
  .addEventListener(
    "focus",
    function() {

      showSuggestions(
        this,

        document.getElementById(
          "suggestions2"
        ),

        2
      );

    }
  );


const compareButton =
  document.getElementById(
    "compareButton"
  );


compareButton.addEventListener(
  "mousemove",
  function(event) {

    const rect =
      compareButton
        .getBoundingClientRect();


    const x =
      event.clientX -
      rect.left;


    const y =
      event.clientY -
      rect.top;


    compareButton.style.setProperty(
      "--mouse-x",
      x + "px"
    );


    compareButton.style.setProperty(
      "--mouse-y",
      y + "px"
    );

  }
);


compareButton.addEventListener(
  "click",
  function() {

    compareButton
      .classList
      .remove("neon");


    void compareButton.offsetWidth;


    compareButton
      .classList
      .add("neon");


    if (
      !selectedBoot1 ||
      !selectedBoot2
    ) {

      alert(
        "Please select two boots first."
      );

      return;

    }


    updateResult(
      selectedBoot1,
      1
    );


    updateResult(
      selectedBoot2,
      2
    );


    document
      .getElementById(
        "comparisonResult"
      )
      .classList
      .add("show");


    document
      .getElementById(
        "winner"
      )
      .textContent =

      "⚡ " +
      selectedBoot1.name +
      " vs " +
      selectedBoot2.name;

  }
);


function updateResult(
  boot,
  number
) {

  const image =
    document.getElementById(
      "resultImage" + number
    );


  if (boot.image) {

    image.src =
      boot.image;

    image.style.display =
      "block";

  }

  else {

    image.removeAttribute(
      "src"
    );

    image.style.display =
      "none";

  }


  document
    .getElementById(
      "resultBoot" + number
    )
    .textContent =
    boot.name;


  document
    .getElementById(
      "speed" + number
    )
    .textContent =
    boot.speed;


  document
    .getElementById(
      "control" + number
    )
    .textContent =
    boot.control;


  document
    .getElementById(
      "comfort" + number
    )
    .textContent =
    boot.comfort;


  document
    .getElementById(
      "weight" + number
    )
    .textContent =
    boot.weight;


  document
    .getElementById(
      "price" + number
    )
    .textContent =
    boot.price;


  document
    .getElementById(
      "surface" + number
    )
    .textContent =
    boot.surface;


  document
    .getElementById(
      "technology" + number
    )
    .textContent =
    boot.technology;

}


document.addEventListener(
  "click",
  function(event) {

    if (
      !event.target.closest(
        ".boot-selector"
      )
    ) {

      document
        .getElementById(
          "suggestions1"
        )
        .classList
        .remove("show");


      document
        .getElementById(
          "suggestions2"
        )
        .classList
        .remove("show");

    }

  }
);

</script>

</body>

</html>
