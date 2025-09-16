
# Mall Analytics Dashboard

A single-page web application frontend built with Tailwind CSS to visualize people movement, product interactions, and activity heatmaps in a shopping mall. This project is designed to be a realistic prototype of a modern analytics dashboard.

---

## Live Demo

The live dashboard is automatically deployed via GitHub Actions and can be viewed here:
**[https://krishthick.github.io/analytics-gemini-repo/](https://krishthick.github.io/analytics-gemini-repo/)**

---

## Dashboard Sections Explained

This dashboard provides a real-time overview of mall activity through several key sections:

### 1. Real-time Stats
These are the four main cards at the top providing an immediate, icon-driven snapshot of the mall's status. The numbers animate on load to give a feeling of a live-updating dashboard.
- **Total People:** A cumulative count of all unique individuals detected over a period.
- **Avg. Dwell Time:** The average amount of time a person spends in the mall.
- **Hot Zones:** The number of zones currently experiencing high levels of activity.
- **Cameras Online:** The operational status of the camera network.

### 2. Activity Heatmap
This section displays a clean, professional SVG floor plan. The heatmap is rendered as colored, semi-transparent zones directly on the map, which is a more realistic approach for data visualization than a simple image overlay.
- **Blue:** Low activity.
- **Yellow:** Medium activity.
- **Red:** High activity (hotspot).

### 3. Top Products
This card lists the products that are receiving the most interactions. Product images have been replaced with clean SVG icons for a more uniform and modern UI.

### 4. Zone Activity
This donut chart breaks down the distribution of people across different defined zones in the mall. The chart is interactive and has an updated, more vibrant color scheme.

--- 

## How to Add Your Own Data (Input)

Currently, this is a frontend-only prototype. All data is hard-coded as placeholders inside the `public/index.html` file. To add your own data, you need to edit this file.

### Editing Real-time Stats & Animated Counters
Find the `<script>` tag at the bottom of the page. The animated counters are controlled here. Change the end values (e.g., `1234` or `3`) to update the display.
```javascript
document.addEventListener('DOMContentLoaded', () => {
    animateValue(document.getElementById('total-people'), 0, 1234, 1500); // EDIT 1234
    animateValue(document.getElementById('hot-zones'), 0, 3, 1500); // EDIT 3
    document.getElementById('dwell-time').innerHTML = '23m'; // EDIT '23m'
});
```

### Editing the Heatmap
Inside the `<!-- Heatmap -->` section, the heatmap is an SVG layer. You can change the `fill` color of each `<rect>` inside the `<g id="heatmap-layer">` to reflect your data. For example, change `fill-red-500` to `fill-blue-500`.
```html
<g id="heatmap-layer" class="opacity-70">
    <rect x="5" y="45" width="50" height="50" class="fill-red-500" /> <!-- Hot Zone -->
    <rect x="65" y="5" width="80" height="50" class="fill-yellow-500" /> <!-- Medium Zone -->
    <rect x="65" y="65" width="130" height="30" class="fill-blue-500/50" /> <!-- Low Zone -->
</g>
```

### Editing Zone Activity Chart
In the `<script>` tag at the bottom, edit the `labels` and `data` arrays to match your zones and people counts:
```javascript
const zoneActivityChart = new Chart(zoneActivityCtx, {
    type: 'doughnut',
    data: {
        labels: ['Zone A', 'Zone B', 'Food Court'], // EDIT ZONE NAMES HERE
        datasets: [{
            label: 'Activity',
            data: [220, 300, 400], // EDIT PEOPLE COUNTS HERE
            // ...
        }]
    },
    // ...
});
```

---

## Technical Details

- **Frontend:** HTML, Tailwind CSS
- **Charts:** Chart.js
- **Graphics:** Inline SVG for icons and floor plan.
- **Animations:** Basic JavaScript for animated counters.
- **Deployment:** Automated via GitHub Actions to GitHub Pages.

### Local Development

To run this project on your local machine:

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/KRISHTHICK/analytics-gemini-repo.git
    cd analytics-gemini-repo
    ```

2.  **Install dependencies:**
    ```bash
    npm install
    ```

3.  **Build and Watch CSS:**
    To automatically rebuild the CSS when you make changes, run:
    ```bash
    npm run watch:css
    ```

4.  **Serve the Website:**
    In a separate terminal, navigate to the `public/` directory and run a simple web server:
    ```bash
    cd public
    python3 -m http.server 8080
    ```
    You can then view the dashboard at `http://localhost:8080`.
