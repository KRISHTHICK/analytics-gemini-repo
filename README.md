# Mall Analytics Dashboard

A single-page web application frontend built with Tailwind CSS to visualize people movement, product interactions, and activity heatmaps in a shopping mall. This project is designed to be a realistic and interactive prototype of a modern analytics dashboard.

---

## Live Demo

The live dashboard is automatically deployed via GitHub Actions and can be viewed here:
**[https://krishthick.github.io/analytics-gemini-repo/](https://krishthick.github.io/analytics-gemini-repo/)**

---

## Features

- **Modern Dark UI:** A visually appealing and professional dark theme with colorful accents.
- **Interactive Heatmap:** A pseudo-3D SVG floor plan with interactive tooltips showing detailed stats for each zone.
- **Animated Stats:** Key metrics animate on load, giving the dashboard a live feel.
- **Vibrant Charts:** A clean and colorful donut chart visualizes activity across different zones.
- **Responsive Design:** The layout is fully responsive and optimized for desktop and tablet use.
- **Automated Deployment:** The project is automatically built and deployed to GitHub Pages using a GitHub Actions workflow.

## Dashboard Sections Explained

- **Real-time Stats:** Four main cards with colorful icons and top borders provide a snapshot of key metrics. The numbers animate on load.
- **Activity Heatmap:** An interactive SVG floor plan where hovering over a zone reveals a tooltip with specific data like people count and average dwell time.
- **Top Products:** A list of top-selling items with clean, uniform icons and a colorful top border.
- **Zone Activity:** A donut chart that visualizes the distribution of people across the mall's zones.

--- 

## How to Add Your Own Data (Input)

This is a frontend-only prototype. All data is hard-coded inside a `<script>` tag at the bottom of the `public/index.html` file. To add your own data, you only need to edit the `heatmapData` object.

### Editing All Dashboard Data

All the data for the heatmap, tooltips, and charts is controlled by a single JavaScript object. Find the `<script>` tag and edit the `heatmapData` object:

```javascript
// --- Data Store ---
const heatmapData = {
    'zone-a': { name: 'Zone A', people: 220, dwell: '15m' },
    'zone-b': { name: 'Zone B', people: 300, dwell: '18m' },
    'zone-c': { name: 'Zone C', people: 80, dwell: '7m' },
    'food-court': { name: 'Food Court', people: 400, dwell: '25m' },
    'main-hall': { name: 'Main Hall', people: 150, dwell: '12m' },
};
```
- **To change tooltip data:** Edit the `people` and `dwell` values for each zone.
- **To change the donut chart:** The chart automatically uses the `name` and `people` values from this object.
- **To change the heatmap colors:** The colors are hard-coded in the SVG, but this data object is what *should* drive them in a real application.

--- 

## Technical Details

- **Frontend:** HTML, Tailwind CSS
- **Charts:** Chart.js
- **Graphics & Interactivity:** Inline SVG and vanilla JavaScript for tooltips and animations.
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