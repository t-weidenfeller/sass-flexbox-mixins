# SCSS Flexbox Mixins

A modern collection of SCSS mixins for flexbox layouts with a clean, map-based API that makes styling flexible layouts quick and intuitive.

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

### 🎯 `@mixin flex()` - Complete Flex Container

The main mixin supporting all flex container properties with string-based values for better readability.

```scss
@mixin flex(
  $direction: "row",
  $wrap: "nowrap", 
  $justify-content: "start",
  $align-items: "stretch",
  $align-content: null,
  $gap: null,
  $row-gap: null,
  $column-gap: null
)
```

#### Parameters:
- **`$direction`**: `"row"` | `"row-reverse"` | `"column"` | `"column-reverse"`
- **`$wrap`**: `"nowrap"` | `"wrap"` | `"wrap-reverse"`
- **`$justify-content`**: `"start"` | `"center"` | `"end"` | `"space-between"` | `"space-around"` | `"space-evenly"`
- **`$align-items`**: `"start"` | `"center"` | `"end"` | `"stretch"` | `"baseline"`
- **`$align-content`**: `"start"` | `"center"` | `"end"` | `"stretch"` | `"space-between"` | `"space-around"` | `"space-evenly"`
- **`$gap`**, **`$row-gap`**, **`$column-gap`**: Any CSS length value

### 🎯 `@mixin flex-item()` - Complete Flex Item Control

Controls all flex item properties.

```scss
@mixin flex-item(
  $grow: null,
  $shrink: null,
  $basis: null,
  $align-self: null,
  $order: null
)
```

#### Parameters:
- **`$grow`**: Number (flex-grow value)
- **`$shrink`**: Number (flex-shrink value)
- **`$basis`**: CSS length or `auto`
- **`$align-self`**: `"auto"` | `"start"` | `"center"` | `"end"` | `"stretch"` | `"baseline"`
- **`$order`**: Number (visual order)

### 🎯 `@mixin flex-row()` - Row Shortcut

Quick setup for row layouts.

```scss
@mixin flex-row($justify-content: "start", $align-items: "stretch")
```

### 🎯 `@mixin flex-column()` - Column Shortcut

Quick setup for column layouts.

```scss
@mixin flex-column($justify-content: "center", $align-items: "stretch")
```

## Examples

### Basic Usage

```scss
// Simple centered container
.hero {
  @include flex.flex("row", "nowrap", "center", "center");
}

// Column layout
.sidebar {
  @include flex.flex-column();
}

// Row with space between
.navbar {
  @include flex.flex-row("space-between", "center");
}
```

### Advanced Layouts

```scss
// Grid-like layout with gaps
.card-grid {
  @include flex.flex(
    $direction: "row",
    $wrap: "wrap", 
    $justify-content: "start",
    $align-items: "stretch",
    $gap: 1rem
  );
  
  .card {
    @include flex.flex-item(
      $grow: 1,
      $basis: 300px
    );
  }
}

// Responsive navigation
.navbar {
  @include flex.flex-row("space-between", "center");
  
  .logo {
    @include flex.flex-item($shrink: 0);
  }
  
  .nav-links {
    @include flex.flex(
      $direction: "row",
      $gap: 2rem
    );
  }
  
  .user-menu {
    @include flex.flex-item($shrink: 0);
  }
}

// Sidebar layout
.app-layout {
  @include flex.flex-row();
  min-height: 100vh;
  
  .sidebar {
    @include flex.flex-column();
    @include flex.flex-item(
      $basis: 250px,
      $shrink: 0
    );
  }
  
  .main-content {
    @include flex.flex-item($grow: 1);
  }
}
```

### Real-World Components

```scss
// Card component
.card {
  @include flex.flex-column("space-between");
  
  .card-header {
    @include flex.flex-row("space-between", "center");
  }
  
  .card-content {
    @include flex.flex-item($grow: 1);
  }
  
  .card-footer {
    @include flex.flex-row("end", "center");
    @include flex.flex-item($shrink: 0);
  }
}

// Modal dialog
.modal {
  @include flex.flex("row", "nowrap", "center", "center");
  
  .modal-content {
    @include flex.flex-column();
    @include flex.flex-item($basis: 500px);
  }
}
```

## Key Features

✅ **String-based API** - Use intuitive strings like `"center"` instead of `flex-start`  
✅ **Smart defaults** - Sensible defaults for common use cases  
✅ **Complete coverage** - All flexbox properties supported  
✅ **Modern SCSS** - Uses `@use` and Sass maps for consistency  
✅ **Zero dependencies** - Pure SCSS, no external dependencies  
✅ **TypeScript-friendly** - Clear parameter types and values  

## Browser Support

Supports all modern browsers with flexbox support:
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