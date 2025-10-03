# SCSS Flexbox Mixins

A comprehensive collection of SCSS mixins for flexbox layouts that makes styling flexible layouts quick and easy.

## Installation

```bash
npm install sass-flexbox-mixins
```

## Usage

Import the mixins in your SCSS file:

```scss
@use 'sass-flexbox-mixins' as flex;
```

Or if you're using older SCSS syntax:

```scss
@import '~sass-flexbox-mixins';
```

## Available Mixins

### Basic Flexbox

#### `@mixin flex($direction, $wrap)`
Sets up basic flexbox with optional direction and wrap.

```scss
.container {
  @include flex(row, wrap);
}
```

### Alignment Mixins

#### `@mixin flex-center`
Centers content both horizontally and vertically.

```scss
.hero {
  @include flex-center;
}
```

#### `@mixin flex-center-vertical`
Centers content vertically only.

```scss
.sidebar {
  @include flex-center-vertical;
}
```

#### `@mixin flex-center-horizontal`
Centers content horizontally only.

```scss
.header {
  @include flex-center-horizontal;
}
```

#### `@mixin flex-between`
Distributes items with space between them.

```scss
.navbar {
  @include flex-between;
}
```

#### `@mixin flex-around`
Distributes items with space around them.

```scss
.gallery {
  @include flex-around;
}
```

#### `@mixin flex-evenly`
Distributes items with equal space around them.

```scss
.footer-links {
  @include flex-evenly;
}
```

### Flex Item Utilities

#### `@mixin flex-item($grow, $shrink, $basis)`
Sets flex grow, shrink, and basis properties.

```scss
.main-content {
  @include flex-item(1, 1, 0);
}
```

#### `@mixin flex-grow($value)`
Sets flex-grow property.

```scss
.expanding-section {
  @include flex-grow(2);
}
```

#### `@mixin flex-shrink($value)`
Sets flex-shrink property.

```scss
.fixed-sidebar {
  @include flex-shrink(0);
}
```

#### `@mixin flex-basis($value)`
Sets flex-basis property.

```scss
.column {
  @include flex-basis(300px);
}
```

### Layout Mixins

#### `@mixin flex-column($align, $justify)`
Creates a flex column layout.

```scss
.sidebar {
  @include flex-column(center, flex-start);
}
```

#### `@mixin flex-row($align, $justify)`
Creates a flex row layout.

```scss
.header {
  @include flex-row(center, space-between);
}
```

### Responsive Utilities

#### `@mixin flex-responsive($mobile-direction, $desktop-direction, $breakpoint)`
Creates responsive flex layouts.

```scss
.responsive-container {
  @include flex-responsive(column, row, 768px);
}
```

### Advanced Utilities

#### `@mixin flex-gap($gap)`
Adds gap between flex items with fallback for older browsers.

```scss
.card-grid {
  @include flex-gap(1rem);
}
```

#### `@mixin flex-order($order)`
Sets the order of a flex item.

```scss
.last-item {
  @include flex-order(-1); // Makes it appear first
}
```

#### `@mixin flex-align($align-items, $align-content, $justify-content)`
Advanced alignment control.

```scss
.complex-layout {
  @include flex-align(center, space-between, flex-end);
}
```

#### `@mixin align-self($value)`
Aligns individual flex items.

```scss
.special-item {
  @include align-self(flex-end);
}
```

## Examples

### Navigation Bar
```scss
.navbar {
  @include flex-between;
  padding: 1rem;
  
  .logo {
    @include flex-shrink(0);
  }
  
  .nav-links {
    @include flex(row, nowrap);
    @include flex-gap(2rem);
  }
}
```

### Card Layout
```scss
.card-container {
  @include flex(row, wrap);
  @include flex-gap(1rem);
  
  .card {
    @include flex-basis(300px);
    @include flex-grow(1);
  }
}
```

### Responsive Sidebar Layout
```scss
.layout {
  @include flex-responsive(column, row, 768px);
  min-height: 100vh;
  
  .sidebar {
    @include flex-basis(250px);
    @include flex-shrink(0);
  }
  
  .main-content {
    @include flex-grow(1);
  }
}
```

## Browser Support

This package supports all modern browsers that support flexbox:
- Chrome 29+
- Firefox 28+
- Safari 9+
- Edge 12+
- iOS Safari 9+
- Android Browser 4.4+

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

MIT License - see LICENSE file for details.