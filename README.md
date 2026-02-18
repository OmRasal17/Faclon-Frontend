# Angular Custom Chart Component

Welcome to the Faclon Frontend Assignment project.

This repository features a custom, reusable Angular component (`<io-chart>`) designed to render Line, Column, and Pie charts. The core philosophy behind this project was to build a robust charting solution without relying on any external libraries like D3.js or Chart.js, demonstrating pure Angular capabilities and direct SVG manipulation.

## Features

- **Zero External Dependencies**: The chart is built entirely with standard Angular and SVG APIs.
- **Dynamic Chart Types**: You can switch between Line, Column, and Pie charts instantly just by changing the configuration object.
- **Responsive Design**: The charts use the SVG `viewBox` attribute, allowing them to scale perfectly to any container size.
- **Interactive Elements**:
  - Hover effects on bars, slices, and points to improve readability.
  - Tooltips that display exact values when interacting with data points.
- **Clean Architecture**:
  - Strict typing using TypeScript interfaces.
  - Styles are encapsulated within the component using SCSS.
  - Efficient change detection to ensure smooth performance.

## Installation

If you'd like to run this project locally, follow these steps:

1. **Clone the repository**
   ```bash
   git clone https://github.com/OmRasal17/Faclon-Frontend.git
   cd frontend-assignment
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Run the application**
   ```bash
   npm start
   ```
   Once the server starts, navigate to `http://localhost:4200/` in your browser.

## Usage Guide

To use the chart in your own Angular application, first import the `ChartComponent`.

**1. Import the Component**

In your standalone component or module:

```typescript
import { ChartComponent } from './chart/chart.component';

@Component({
  standalone: true,
  imports: [ChartComponent],
  // ...
})
export class AppComponent { ... }
```

**2. Add to Template**

Place the component tag in your HTML and pass the configuration options:

```html
<io-chart [chartOptions]="myChartOptions"></io-chart>
```

### Configuration Object

The component is controlled by a simple configuration object. Here is the TypeScript interface for reference:

```typescript
export interface ChartOptions {
  type: 'line' | 'column' | 'pie';
  title: string;
  series: ChartSeries[];
}

export interface ChartSeries {
  name: string;
  value: number;
  color: string;
}
```

### Examples

Here are some examples of how to configure different chart types:

**Line Chart**
Used for showing trends over time, like monthly sales.
```typescript
lineOptions: ChartOptions = {
  type: 'line',
  title: 'Monthly Sales',
  series: [
    { name: 'Jan', value: 100, color: '#FF5733' },
    { name: 'Feb', value: 150, color: '#33FF57' }
  ]
};
```

**Column Chart**
Great for comparing values across categories, like revenue by quarter.
```typescript
columnOptions: ChartOptions = {
  type: 'column',
  title: 'Revenue by Quarter',
  series: [
    { name: 'Q1', value: 500, color: '#3357FF' },
    { name: 'Q2', value: 750, color: '#FF33A1' }
  ]
};
```

**Pie Chart**
Ideal for showing proportional distribution, like market share.
```typescript
pieOptions: ChartOptions = {
  type: 'pie',
  title: 'Market Share',
  series: [
    { name: 'Product A', value: 40, color: '#FFC300' },
    { name: 'Product B', value: 60, color: '#DBFF33' }
  ]
};
```

## Project Structure

Here is a quick overview of the file structure to help you navigate the codebase:

```
src/
├── app/
│   ├── chart/               # The Reusable Chart Component
│   │   ├── chart.ts         # Logic: Data processing and SVG math
│   │   ├── chart.html       # View: SVG template and structural directives
│   │   ├── chart.scss       # Styles: Component-specific styling
│   │   └── chart.interface.ts # Types: TypeScript interfaces
│   └── app.component.ts     # Demo: Shows how to use the component
```

## Running Tests

This project includes unit tests to ensure the logic works as expected. You can run them with:

```bash
npm test
```

## Implementation Details

For those interested in how it works under the hood:

- **Column Chart**: We calculate the height of each bar relative to the maximum data value in the series.
- **Line Chart**: We map data points to X and Y coordinates within the SVG grid and generate a `polyline` string to connect them.
- **Pie Chart**: This was the tricky part! We convert data values into angles (radians) and use the SVG Arc command (`A`) to draw each slice.

### Styling
- We use **SCSS** for all styling needs, keeping the axes, labels, and legends looking sharp.
- **Animations** are handled with CSS `@keyframes` to create a smooth drawing effect for the line chart and hover transitions for the bars and slices.

## License

This project is open-sourced under the MIT License.



<img width="1919" height="1031" alt="Screenshot 2026-02-19 005108" src="https://github.com/user-attachments/assets/a1c15bc4-8600-41d2-bf2e-2ab5456f4446" />
<img width="1919" height="1028" alt="Screenshot 2026-02-19 005134" src="https://github.com/user-attachments/assets/1a334d7b-6e27-489d-b347-ca4428d73de5" />
