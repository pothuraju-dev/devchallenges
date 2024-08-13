# CSS Grid: Properties and Use Cases

## Introduction
CSS Grid is a powerful layout system that allows for two-dimensional layouts in CSS. It provides a way to create complex layouts with rows and columns, offering more flexibility and control compared to other CSS layout techniques.

## Basic Grid Container Properties

### 1. `display: grid`
- This property defines an element as a grid container.
- Example: `.container { display: grid; }`

### 2. `grid-template-rows` and `grid-template-columns`
- These properties define the size and number of rows and columns in the grid.
- They can use various units (px, %, fr, etc.) and functions like `repeat()`.
- Examples from the provided CSS:
  ```css
  grid-template-rows: repeat(4, 100px);
  grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
  ```
- The `repeat()` function is used to create multiple rows or columns of the same size.
- `auto-fit` and `minmax()` are used for responsive design, allowing columns to adjust based on available space.

### 3. `grid-template-areas`
- This property defines named grid areas, providing a visual representation of the layout.
- Example (commented out in the provided CSS):
  ```css
  grid-template-areas: 
    'header header'
    'main aside'
    'footer footer';
  ```

## Alignment Properties

### 1. `justify-items` and `align-items`
- These properties align grid items inside their cells.
- `justify-items` aligns items horizontally, `align-items` aligns vertically.
- Example (commented out): `justify-items: center; align-items: center;`

### 2. `justify-content` and `align-content`
- These properties align the entire grid within the grid container.
- Useful when the grid's total size is less than the container's size.
- Example (commented out): `justify-content: space-evenly; align-content: space-evenly;`

## Grid Item Properties

### 1. `grid-row` and `grid-column`
- These properties define an item's location and span within the grid.
- They are shorthand for `grid-row-start`, `grid-row-end`, `grid-column-start`, and `grid-column-end`.
- Example (commented out):
  ```css
  grid-row: 1/3;
  grid-column: 1/7;
  ```

### 2. `grid-area`
- This is a shorthand property for `grid-row-start`, `grid-column-start`, `grid-row-end`, and `grid-column-end`.
- It can also be used to assign an item to a named grid area.
- Examples (commented out):
  ```css
  grid-area: 2/4/4/6;
  grid-area: header;
  ```

### 3. `z-index`
- This property controls the stacking order of grid items.
- Useful when items overlap.
- Example (commented out): `z-index: 1;`

## Use Cases and Best Practices

1. **Responsive Layouts**: Use `auto-fit` and `minmax()` for flexible, responsive grids that adjust to different screen sizes.

2. **Complex Layouts**: Utilize `grid-template-areas` for creating complex layouts with named areas, making the structure more intuitive.

3. **Overlapping Elements**: Combine `grid-area` with `z-index` to create layouts with overlapping elements.

4. **Centering Content**: Use `justify-items` and `align-items` to easily center content within grid cells.

5. **Variable-sized Tracks**: Mix fixed sizes (like px) with flexible sizes (like fr) to create diverse layouts.

6. **Full-page Layouts**: Create full-page layouts using techniques like:
   ```css
   grid-template-rows: auto 1fr auto;
   ```
   This creates a header, expandable main content, and footer.

7. **Grid vs Flexbox**: Use Grid for two-dimensional layouts (rows and columns) and Flexbox for one-dimensional layouts (either row or column).

## Examples and Tasks

### Beginner Level

#### Example 1: Basic Grid Layout

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 100px 200px;
  gap: 10px;
}
```

This creates a 3x2 grid with equal-width columns and specified row heights.

#### Task 1: Create a Simple Photo Gallery
Create a responsive photo gallery with a 3x3 grid that adjusts to 2 columns on smaller screens.

```css
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1rem;
}

.gallery img {
  width: 100%;
  height: 200px;
  object-fit: cover;
}
```

### Intermediate Level

#### Example 2: Named Grid Areas

```css
.container {
  display: grid;
  grid-template-areas:
    "header header header"
    "sidebar main main"
    "footer footer footer";
  grid-template-columns: 200px 1fr 1fr;
  grid-template-rows: auto 1fr auto;
}

.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main { grid-area: main; }
.footer { grid-area: footer; }
```

This creates a layout with a header, sidebar, main content area, and footer.

#### Task 2: Create a Dashboard Layout
Design a dashboard layout with a header, sidebar, main content area, and two widget areas.

```css
.dashboard {
  display: grid;
  grid-template-areas:
    "header header header"
    "sidebar main widgets"
    "sidebar main widgets";
  grid-template-columns: 200px 1fr 250px;
  grid-template-rows: auto 1fr 1fr;
  height: 100vh;
}

.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.main { grid-area: main; }
.widgets { grid-area: widgets; }
```

### Advanced Level

#### Example 3: Complex Responsive Layout

```css
.container {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 20px;
}

.header {
  grid-column: 1 / -1;
}

.main {
  grid-column: 1 / span 8;
}

.sidebar {
  grid-column: 9 / -1;
}

@media (max-width: 768px) {
  .main,
  .sidebar {
    grid-column: 1 / -1;
  }
}
```

This creates a 12-column grid with a full-width header, main content spanning 8 columns, and a sidebar spanning 4 columns. On smaller screens, it stacks vertically.

#### Task 3: Create a Magazine-style Layout
Design a complex magazine-style layout with a mix of full-width, half-width, and quarter-width elements that reflow on different screen sizes.

```css
.magazine {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 1rem;
}

.hero { grid-column: 1 / -1; }
.feature-1 { grid-column: 1 / span 6; }
.feature-2 { grid-column: 7 / -1; }
.article-1, .article-2, .article-3 { grid-column: span 4; }

@media (max-width: 992px) {
  .feature-1, .feature-2 { grid-column: 1 / -1; }
  .article-1, .article-2, .article-3 { grid-column: span 6; }
}

@media (max-width: 576px) {
  .article-1, .article-2, .article-3 { grid-column: 1 / -1; }
}
```

### Expert Challenge

#### Task 4: Create a Dynamic Grid System
Develop a flexible grid system that allows for nested grids, custom span sizes, and automatically adjusts based on content and screen size.

```css
.grid {
  display: grid;
  grid-template-columns: repeat(var(--cols, 12), 1fr);
  gap: var(--gap, 1rem);
}

.col {
  grid-column: span var(--span, 1);
}

/* Example usage */
.container {
  --cols: 24;
  --gap: 0.5rem;
}

.wide-col {
  --span: 16;
}

@media (max-width: 1200px) {
  .container { --cols: 12; }
  .wide-col { --span: 8; }
}

@media (max-width: 768px) {
  .col { --span: 12; }
}
```

This system uses CSS custom properties to create a highly customizable and responsive grid. It allows for easy adjustment of column numbers, gap sizes, and individual column spans.

These examples and tasks provide a range of applications for CSS Grid, from simple layouts to complex, responsive designs. They demonstrate how Grid can be used to create flexible, powerful layouts that adapt to different screen sizes and content requirements.