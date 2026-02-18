# Angular Custom Chart Component

A reusable, dependency-free Angular chart component `<io-chart>` supporting Line, Column, and Pie charts using SVG.
Built for the Frontend Intern Assignment.

## Features
- **Zero External Dependencies**: Pure Angular + SVG.
- **Dynamic Chart Types**: Switches between Line, Column, and Pie based on configuration.
- **Responsive**: Scales automatically to container width.
- **Interactive**: Hover effects for better UX.

## Usage

```html
<io-chart [chartOptions]="myOptions"></io-chart>
```

```typescript
const myOptions: ChartOptions = {
  type: 'line', // or 'column', 'pie'
  title: 'My Chart',
  series: [
    { name: 'Item A', value: 10, color: 'red' },
    { name: 'Item B', value: 20, color: 'blue' }
  ]
};
```

## Running the Project

To start a local development server:

```bash
npm start
```
Navigate to `http://localhost:4200/`.

## Running Tests

```bash
ng test
```
