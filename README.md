# Angular Custom Chart Component

A robust, dependency-free Angular chart component `<io-chart>` that renders **Line**, **Column**, and **Pie** charts using pure SVG. Built for the Frontend Intern Assignment.

![License](https://img.shields.io/badge/license-MIT-blue.svg) ![Angular](https://img.shields.io/badge/Angular-v17+-dd0031.svg)

## 🚀 Features

- **Zero External Dependencies**: Implementation uses standard Angular and SVG APIs. No D3.js or Chart.js.
- **Dynamic Rendering**: Switches between chart types instantly based on configuration.
- **Responsive Design**: Uses SVG `viewBox` attribute to scale automatically to any container size.
- **Interactive Elements**:
  - Hover effects on bars, slices, and points.
  - Tooltips displaying name and value.
- **Clean Architecture**:
  - Strong typing with TypeScript interfaces.
  - Isolated SCSS styling with encapsulation.
  - Efficient ChangeDetection via `OnChanges`.

## 🛠️ Installation

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
   Navigate to `http://localhost:4200/`.

## 📖 Usage

Import `ChartComponent` in your standalone component or module:

```typescript
import { ChartComponent } from './chart/chart.component';

@Component({
  standalone: true,
  imports: [ChartComponent],
  // ...
})
export class AppComponent { ... }
```

Use the component in your template:

```html
<io-chart [chartOptions]="myChartOptions"></io-chart>
```

### Configuration Object

The component accepts a `ChartOptions` object:

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

**Line Chart**
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

## 📂 Project Structure

```
src/
├── app/
│   ├── chart/               # Reusable Chart Component
│   │   ├── chart.ts         # Component Logic (Maths & SVG path generation)
│   │   ├── chart.html       # SVG Template & Directives
│   │   ├── chart.scss       # Component Styling
│   │   └── chart.interface.ts # TypeScript Interfaces
│   └── app.component.ts     # Demo Usage
```

## 🧪 Running Tests

Run unit tests to verify logic:

```bash
npm test
```

## 📐 Implementation Details

### Maths & Logic
- **Column Chart**: Calculates bar height relative to the maximum data value.
- **Line Chart**: Maps data points to X,Y coordinates and generates an SVG polyline string.
- **Pie Chart**: Converts values to angles/radians and generates SVG Arc paths (`A` command).

### Styling
- **SCSS** is used for styling axes, labels, and legends.
- **Animations** use CSS `@keyframes` for drawing lines and transitions for hover states.

## 📝 License

This project is licensed under the MIT License.
