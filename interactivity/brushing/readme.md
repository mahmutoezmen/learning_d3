# Interactive Scatter Plot with Brushing

This is a JavaScript code that creates an interactive scatter plot with brushing functionality using the D3.js library. The scatter plot displays data from the Iris dataset and allows users to brush/select data points within a specified region.

## Prerequisites
- D3.js library (v4) is required. It is loaded from the following URL:
  ```
  <script src="https://d3js.org/d3.v4.js"></script>
  ```

## Usage
1. Include the D3.js library in your HTML file.
2. Create a `<div>` element with the `id` "dataviz_brushScatter" to contain the scatter plot.
3. Create another `<div>` element with the `id` "tableContainer" to display the brushed data in a table.
4. Define a CSS style for the selected circles:
   ```
   <style>
   .selected {
     opacity: 1 !important;
     stroke: black;
     stroke-width: 1px;
   }
   </style>
   ```
5. The JavaScript code starts with defining the dimensions and margins for the graph.
6. An SVG element is appended to the "dataviz_brushScatter" div to hold the scatter plot.
7. A table is created inside the "tableContainer" div to display the brushed data.
8. The dataset is read from a CSV file using the `d3.csv` function. In this example, the Iris dataset is loaded from the provided URL.
9. The X and Y axes are defined using `d3.scaleLinear` to map the data to the plot's dimensions.
10. Unique species names are extracted from the data.
11. A color scale is automatically generated using `d3.scaleOrdinal` and `d3.schemeCategory10` to assign colors to each species.
12. Data points (circles) are added to the scatter plot using the `svg.append('g').selectAll('circle')` pattern.
    - The `cx` and `cy` attributes determine the position of each circle based on the data values.
    - The `r` attribute sets the radius of each circle to 8 pixels.
    - The `fill` attribute sets the color of each circle based on the species using the color scale.
13. Brushing functionality is added to the scatter plot using `svg.call(d3.brush())`.
    - The `extent` specifies the initial brush area as the entire graph.
    - The `on("start brush", updateChart)` event triggers the `updateChart` function whenever the brush selection changes.
14. The `updateChart` function is called when brushing is performed. It:
    - Updates the class of each circle based on whether it falls within the brush selection, highlighting the selected circles.
    - Filters the data to include only the brushed points and updates the table using the `updateTable` function.
15. The `isBrushed` function determines whether a data point is inside the brush selection by comparing its coordinates to the brush extents.
16. The `updateTable` function is responsible for updating the table with the brushed data.
    - It first clears the existing table.
    - It appends the table header based on the columns of the data.
    - It appends table rows and cells to display the values of each data point.

That's it! With this code, you can create an interactive scatter plot with brushing functionality and display the brushed data in a table. Feel free to modify the code to fit your specific requirements.
