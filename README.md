

## Youtube Video Link 
link: https://youtu.be/FJ44qmE5odc?si=LNDahcjQCvGgM01x

## SVG Path Scroll Animation

This script animates an SVG path based on the scroll position of the page. As the user scrolls down, the path progressively reveals itself.

### How It Works

1. **Select the SVG Path and Calculate Its Length**:
    ```javascript
    let path = document.querySelector("path");
    let pathLength = path.getTotalLength();
    ```

2. **Set Initial Styles for the Path**:
    ```javascript
    path.style.strokeDasharray = pathLength + " " + pathLength;
    path.style.strokeDashoffset = pathLength;
    ```

3. **Add Scroll Event Listener**:
    ```javascript
    window.addEventListener("scroll", () => {
        // Calculate the scroll percentage
        var scrollPercentage = (document.documentElement.scrollTop + document.body.scrollTop) / (document.documentElement.scrollHeight - document.documentElement.clientHeight);

        // Calculate the draw length
        var drawLength = pathLength * scrollPercentage;

        // Update the stroke-dashoffset to draw the path
        path.style.strokeDashoffset = pathLength - drawLength;
    });
    ```

### Explanation

- **Path Selection and Length Calculation**:
    - The script selects the first `<path>` element in the SVG using `document.querySelector("path")`.
    - It then calculates the total length of the path using `path.getTotalLength()`.

- **Setting Initial Path Styles**:
    - The `stroke-dasharray` property is set to twice the path length, creating a dashed line that is initially hidden.
    - The `stroke-dashoffset` property is set to the full path length, hiding the entire path.

- **Scroll Event Listener**:
    - An event listener is added to the window object to listen for scroll events.
    - The scroll percentage is calculated as the ratio of the current scroll position to the total scrollable height.
    - The draw length is calculated by multiplying the path length by the scroll percentage.
    - The `stroke-dashoffset` is updated to reveal the path proportionally as the user scrolls.

### Usage

1. **Include the SVG in Your HTML**:
    ```html
    <svg width="100" height="100">
        <path d="M10 10 H 90 V 90 H 10 Z" stroke="black" fill="transparent"/>
    </svg>
    ```

2. **Add the JavaScript to Your HTML**:
    ```html
    <script>
        let path = document.querySelector("path");
        let pathLength = path.getTotalLength();

        path.style.strokeDasharray = pathLength + " " + pathLength;
        path.style.strokeDashoffset = pathLength;

        window.addEventListener("scroll", () => {
            var scrollPercentage = (document.documentElement.scrollTop + document.body.scrollTop) / (document.documentElement.scrollHeight - document.documentElement.clientHeight);
            var drawLength = pathLength * scrollPercentage;
            path.style.strokeDashoffset = pathLength - drawLength;
        });
    </script>
    ```

### Demo

To see the effect in action, create a long enough HTML document to allow scrolling and include the SVG and JavaScript as shown above. As you scroll down the page, the SVG path will gradually be revealed.


