# Huttflix

A custom Jellyfin theme that replaces the default blue accent colors with elegant red tones. Originally created for a private Jellyfin instance, this theme provides a clean, refined aesthetic while maintaining full compatibility with Jellyfin's interface.

## Features

### Core Features
- **Red Accent Colors**: Replaces all blue UI elements (buttons, links, tabs, progress bars) with red tones
- **Custom Logo Support**: Easy logo replacement via CSS variables - no need to modify Jellyfin's installation files
- **Editor's Choice Plugin Support**: Full styling integration for the Editor's Choice plugin
- **Consistent Design**: Carefully styled components maintain visual harmony across the entire interface
- **Accessibility-Focused**: Maintains proper contrast ratios and includes visible focus indicators for keyboard navigation

### Styled Elements
- Navigation sidebar and header buttons
- Primary action buttons (Play, Resume, Submit)
- Tabs and segmented controls
- Form elements (inputs, checkboxes, toggles, dropdowns)
- Media cards and overlay buttons
- Progress bars and sliders
- Video player controls
- Badges, counters, and indicators
- Custom scrollbars
- Dialog boxes and popups
- Filter chips and search results

### Optional Features
Easily enabled by uncommenting CSS sections:
- Darker background for enhanced contrast
- Larger play icons on media cards
- Stronger backdrop blur effects

## Installation

### Method 1: Direct Paste (Recommended)

1. Open your Jellyfin **Admin Dashboard**
2. Navigate to **Dashboard → General** (v10.10+) / **Dashboard → Branding** (v10.11+)
3. Scroll down to the **Custom CSS** field
4. Copy the entire contents of [`huttflix.css`](https://raw.githubusercontent.com/hutt/huttflix-theme/refs/heads/main/huttflix.css)
5. Paste the CSS code into the Custom CSS field
6. Click **Save**
7. Delete your cache and reload your browser with **Ctrl+F5** (or **Cmd+Shift+R** on Mac)

### Method 2: Import via URL

1. Open your Jellyfin **Admin Dashboard**
2. Navigate to **Dashboard → General**
3. Scroll down to the **Custom CSS** field
4. Paste the following import statement:

```css
@import url('https://raw.githubusercontent.com/hutt/huttflix-theme/refs/heads/main/huttflix.css');
```

5. Click **Save**
6. Reload your browser with **Ctrl+F5** (or **Cmd+Shift+R** on Mac)

> [!NOTE]
> Method 1 is recommended as it doesn't rely on external resources and ensures your theme continues working even if the repository changes.

## Customization

### Changing Colors

All colors are defined as CSS variables at the top of the file. To customize:

1. Locate the `:root` section (around line 14)
2. Modify the color variables:

```css
:root {
    --accent-red: #ff000d;              /* Primary red for hover & active states */
    --accent-dark-red: #850007;         /* Dark red for buttons & highlights */
    --accent-darker-red: #6a0006;       /* Darkest red for active states */
    /* ... */
}
```

### Custom Logos

One of the key advantages of this theme is **CSS-based logo replacement**. Unlike traditional methods that require replacing image files in Jellyfin's installation directory (which get overwritten after each update), this theme uses CSS variables to override logos dynamically.

#### Benefits:
- **Update-Proof**: Your custom logos persist through Jellyfin updates
- **Easy Management**: Change logos by editing three CSS variables
- **No File System Access**: Works entirely through the Jellyfin admin interface

#### Setup Instructions:

1. Prepare your logo files:
   - **Light Logo**: PNG with transparent background (~300x80px) for dark backgrounds
   - **Dark Logo**: PNG with transparent background (~300x80px) for light backgrounds
   - **Icon**: PNG with transparent background (512x512px, square) for favicon

2. Upload your logos to a web-accessible location (web server, CDN, or GitHub)

3. Update the logo variables in the CSS (around line 44):

```css
:root {
    --logo-light: url('https://yourdomain.com/path/to/banner-light.png');
    --logo-dark: url('https://yourdomain.com/path/to/banner-dark.png');
    --logo-icon: url('https://yourdomain.com/path/to/icon-transparent.png');
}
```

4. Save and reload (Ctrl+F5)

Your custom logos will now appear in:
- Login screen
- Header/navigation bar
- Sidebar drawer
- Loading screen
- Browser favicon (where supported)

### Enabling Optional Features

The theme includes optional features that can be enabled by uncommenting specific sections at the end of the CSS file:

#### Darker Background

For enhanced contrast, uncomment lines ~1120-1126:

```css
body {
    background-color: #141414 !important;
}

.backgroundContainer {
    background-color: #141414 !important;
}
```

#### Larger Play Icons

Make play icons on media cards more prominent, uncomment lines ~1131-1135:

```css
.cardOverlayButton-icon {
    font-size: 3em !important;
}
```

#### Stronger Backdrop Blur

Increase blur effect on dialogs and popups, uncomment lines ~1140-1144:

```css
.dialogBackdrop {
    backdrop-filter: blur(12px) !important;
    -webkit-backdrop-filter: blur(12px) !important;
}
```

## Compatibility

- **Jellyfin Version**: 10.10.x and 10.11.1+
- **Platforms**: Web (Desktop), Android, iOS, TV apps - works on all platforms that support the default Jellyfin web interface
- **Browsers**: All modern browsers (Chrome, Firefox, Safari, Edge)
- **Plugins**: Fully compatible with Editor's Choice plugin

## Troubleshooting

### Theme not applying

- Clear browser cache and reload with **Ctrl+F5** (Windows/Linux) or **Cmd+Shift+R** (Mac)
- Verify the CSS was saved correctly in Dashboard → General → Custom CSS
- Check browser console (F12) for any CSS errors

### Custom logos not showing

- Ensure logo URLs are publicly accessible (test by opening URL directly in browser)
- Verify URLs use `https://` (not `http://`)
- Check that image files are valid PNG/SVG formats
- Confirm files are not blocked by CORS policies

### Colors not changing

- Make sure you're editing the variables in the `:root` section
- Verify there are no syntax errors in your custom color values
- Use valid CSS color formats (hex, rgb, rgba)

### Elements still blue

- Some third-party plugins may use their own styles
- Check if browser extensions are interfering with styles
- Ensure you're using a compatible Jellyfin version

## Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/hutt/huttflix-theme/issues).

## License

This project is licensed under the [GPL-3.0 License](LICENSE).

## Author

**[@hutt](https://github.com/hutt/)**

***

## Acknowledgments

Built for Jellyfin - The Free Software Media System  
[jellyfin.org](https://jellyfin.org)
