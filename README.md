# InteractiveData

This is a simple web application that allows users to interactively visualize data. The application uses the Chart.js library to create a line chart. The data is represented as a JSON object. The application uses the Anime.js library to create animations.

## HOSTTED LINK:-


## Code Explanation

The code for the application is located in the `index.js` file. The code is divided into three parts:

1. The first part of the code imports the necessary libraries.
2. The second part of the code creates the line chart.
3. The third part of the code creates the animations.

### Importing the Libraries

The first part of the code imports the necessary libraries. The following libraries are imported:

- Chart.js
- Anime.js

## HTML

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Interactive Data Visualization</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div class="chart-container">
      <canvas id="myChart"></canvas>
    </div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/3.7.0/chart.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/animejs/3.2.1/anime.min.js"></script>
    <script src="index.js"></script>
  </body>
</html>

```

## CSS

```
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.chart-container {
  max-width: 600px;
  margin: 0 auto;
}



```

## JS

```
const data = {
  labels: [
    "Monday",
    "Tuesday",
    "Wednesday",
    "Thursday",
    "Friday",
    "Saturday",
    "Sunday",
  ],
  datasets: [
    {
      label: "Monthly Presents",
      backgroundColor: "rgba(75, 192, 192, 0.2)",
      borderColor: "rgba(75, 192, 192, 1)",
      borderWidth: 1,
      data: [65, 59, 80, 81, 56, 40, 30],
    },
  ],
};
const config = {
  type: "bar",
  data: data,
  options: {
    responsive: true,
    plugins: {
      title: {
        display: true,
        text: "Monthly Students Data",
      },
    },
  },
};
const ctx = document.getElementById("myChart").getContext("2d");
const myChart = new Chart(ctx, config);
myChart.options.plugins.tooltip = {
  callbacks: {
    label: function (context) {
      return `Sales: ${context.parsed.y}`;
    },
  },
};
const chartAnimation = anime({
  targets: myChart.data.datasets[0].data,
  easing: "linear",
  delay: anime.stagger(200),
  duration: 1000,
  loop: true,
  direction: "alternate",
  update: function (anim) {
    myChart.update();
  },
});

```
