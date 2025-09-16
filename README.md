# Mall Analytics Dashboard

A single-page web application frontend built with Tailwind CSS to visualize people movement, product interactions, and activity heatmaps in a shopping mall. This project is a realistic and interactive prototype of a modern analytics dashboard.

---

## Live Demo

The live dashboard is automatically deployed via GitHub Actions and can be viewed here:
**[https://krishthick.github.io/analytics-gemini-repo/](https://krishthick.github.io/analytics-gemini-repo/)**

---

## Features

- **Tabbed Interface:** The UI is split into a main `Dashboard` and a `Floor Plan` view.
- **Modern Dark UI:** A visually appealing and professional dark theme with colorful accents and card borders.
- **Interactive Heatmap:** On the Floor Plan tab, a pseudo-3D SVG floor plan features interactive tooltips showing detailed stats for each zone.
- **Simulated Upload UI:** Includes a UI mock-up for a feature to upload a 3D model of the floor plan.
- **Upgraded Charts:** The Zone Activity data is now a bar chart showing both people count and average dwell time.
- **Detailed Lists:** The Camera Status and Top Products sections are now detailed lists with categories and statuses.
- **Animated Stats:** Key metrics animate on load, giving the dashboard a live feel.
- **Responsive Design:** The layout is fully responsive and optimized for desktop and tablet use.

## How to Use

Navigate between the **Dashboard** and **Floor Plan** tabs to see the different views. On the floor plan, hover your mouse over the colored zones to see detailed tooltips with live data.

--- 

## How to Add Your Own Data

This is a frontend-only prototype. All data is hard-coded inside a single `<script>` tag at the bottom of the `public/index.html` file. To add your own data, you only need to edit the `dashboardData` object.

```javascript
// --- Data Store ---
const dashboardData = {
    stats: {
        totalPeople: 1357,
        currentPeople: 489,
        avgDwellTime: '28m',
        hotZones: 2,
    },
    zoneData: {
        'zone-a': { name: 'Zone A', people: 220, dwell: '15m' },
        'zone-b': { name: 'Zone B', people: 300, dwell: '18m' },
        // ... more zones
    }
};
```
- **To change the main stat cards:** Edit the values in the `stats` object.
- **To change heatmap, tooltips, and charts:** Edit the `name`, `people`, and `dwell` values for each zone in the `zoneData` object. The bar chart and tooltips will update automatically.

--- 

## Technical Details

- **Frontend:** HTML, Tailwind CSS
- **Charts:** Chart.js
- **Graphics & Interactivity:** Inline SVG and vanilla JavaScript for tabs, tooltips, and animations.
- **Deployment:** Automated via GitHub Actions to GitHub Pages.

### Local Development

1.  **Clone the repository.**
2.  **Install dependencies:** `npm install`
3.  **Build and Watch CSS:** `npm run watch:css`
4.  **Serve the Website:** Navigate to the `public/` directory and run `python3 -m http.server 8080`.