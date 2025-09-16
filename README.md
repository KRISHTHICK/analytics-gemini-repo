
# Mall Analytics Dashboard

A single-page web application frontend built with Tailwind CSS to visualize people movement, product interactions, and activity heatmaps in a shopping mall.

---

## Live Demo

Once deployed, the live dashboard can be viewed here:
**[https://krishthick.github.io/analytics-gemini-repo/](https://krishthick.github.io/analytics-gemini-repo/)**

---

## Dashboard Sections Explained

This dashboard provides a real-time overview of mall activity through several key sections:

### 1. Real-time Stats
These are the four main cards at the top providing an immediate snapshot of the mall's status:
- **Total People Detected:** A cumulative count of all unique individuals detected over a period (e.g., 24 hours).
- **Current People in Mall:** A live count of the number of people currently inside the mall.
- **Average Dwell Time:** The average amount of time a person spends in the mall.
- **Hot Zones:** The number of zones currently experiencing high levels of activity.

### 2. Activity Heatmap
This section displays a visual overlay on the mall floor plan. The colors indicate foot traffic intensity:
- **Cool colors (blue/green):** Low activity areas.
- **Warm colors (yellow/red):** High activity areas where people are moving or congregating most.

### 3. Top Products
This card lists the products that are receiving the most interactions. An "interaction" could be a customer picking up the product, looking at it, or purchasing it. It shows:
- Product thumbnail image.
- Product name.
- The total number of interactions.

### 4. Zone Activity
This donut chart breaks down the distribution of people across different defined zones in the mall (e.g., Zone A, Food Court). It helps identify which areas are most popular.

### 5. Camera Status
This card shows the operational status of the camera network, displaying the number of active cameras out of the total number installed.

--- 

## How to Add Your Own Data (Input)

Currently, this is a frontend-only prototype. All data is hard-coded as placeholders inside the `public/index.html` file. To add your own data, you need to edit this file.

### Editing Real-time Stats
Find the following HTML block and change the numbers inside the `<p>` tags:
```html
<!-- Stats Cards -->
<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
    <div class="bg-gray-800 p-6 rounded-lg">
        <h3 class="text-gray-400">Total People Detected</h3>
        <p class="text-4xl font-bold">1,234</p> <!-- EDIT THIS -->
    </div>
    <!-- ... more cards ... -->
</div>
```

### Editing Top Products
Find the "Top Products" section. Each product is a `<div>`. You can edit the image `src`, product name, and interaction count:
```html
<!-- Top Products -->
<div class="flex items-center">
    <img src="https://i.imgur.com/your-image.png" alt="Product" class="w-16 h-16 rounded-md mr-4"> <!-- EDIT IMAGE URL -->
    <div>
        <p class="font-bold">Your Product Name</p> <!-- EDIT NAME -->
        <p class="text-gray-400">Interactions: 150</p> <!-- EDIT COUNT -->
    </div>
</div>
```

### Editing Zone Activity Chart
Scroll to the bottom of `public/index.html` to find the `<script>` tag. You can edit the `labels` and `data` arrays to match your zones and people counts:
```javascript
<script>
    const zoneActivityCtx = document.getElementById('zone-activity-chart').getContext('2d');
    const zoneActivityChart = new Chart(zoneActivityCtx, {
        type: 'doughnut',
        data: {
            labels: ['Zone A', 'Zone B', 'Food Court'], // EDIT ZONE NAMES HERE
            datasets: [{
                label: 'Activity',
                data: [300, 150, 450], // EDIT PEOPLE COUNTS HERE
                // ... styles
            }]
        },
        // ... options
    });
</script>
```

---

## Technical Details

- **Frontend:** HTML, Tailwind CSS
- **Charts:** Chart.js
- **Animations:** Framer Motion (included but not heavily used in this version)
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
    To automatically rebuild the CSS when you make changes to the HTML or `tailwind.config.js`, run:
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
