# GeoJSON Google Maps Visualizer

A modern web application that visualizes GeoJSON data from Google Sheets on interactive Google Maps.

## Features

- 🗺️ Interactive Google Maps integration
- 📊 Direct Google Sheets data import
- 🎨 Support for LineString and MultiLineString geometries
- 🌟 Modern, responsive UI design
- 🔍 Automatic map fitting and zoom
- 🎯 Color-coded feature types
- 📱 Mobile-friendly design

## Setup Instructions

### 1. Get Google Maps API Key

1. Go to the [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select an existing one
3. Enable the "Maps JavaScript API"
4. Create credentials (API Key)
5. Restrict the API key to your domain for security

### 2. Configure the Application

1. Open `index.html` in a text editor
2. Find the line with `YOUR_API_KEY` (near the bottom of the file)
3. Replace `YOUR_API_KEY` with your actual Google Maps API key:

```html
<script async defer 
        src="https://maps.googleapis.com/maps/api/js?key=YOUR_ACTUAL_API_KEY&callback=initMap">
</script>
```

### 3. Prepare Your Google Sheet

Your Google Sheet should contain GeoJSON data in the following formats:

**Option 1: Complete FeatureCollection**
```json
{"type":"FeatureCollection","features":[{"type":"Feature","properties":{},"geometry":{"coordinates":[[-76.9854599157113,38.90002868774647],[-76.98545927215686,38.899865470295936]],"type":"LineString"}}]}
```

**Option 2: Geometry Object**
```json
{"coordinates":[[[-76.98546122001986,38.89979177360672],[-76.98546077518466,38.89973762844829]],[[-76.98545989685424,38.899627559359715],[-76.98545963985472,38.899519951095385]]],"type":"MultiLineString"}
```

**Important**: Make sure your Google Sheet is publicly viewable:
1. Click "Share" in Google Sheets
2. Change access to "Anyone with the link can view"

### 4. Run the Application

1. Open `index.html` in a web browser
2. Enter your Google Sheets URL
3. Click "Load & Visualize Data"

## Supported Data Formats

The application supports:
- **LineString**: Single line paths
- **MultiLineString**: Multiple line paths
- **FeatureCollection**: Collections of features
- **Feature**: Individual GeoJSON features

## Color Coding

- 🔴 **Red**: LineString features
- 🔵 **Teal**: MultiLineString features  
- 🔷 **Blue**: Other feature types

## Browser Compatibility

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

## Security Notes

- Always restrict your Google Maps API key to specific domains
- Ensure your Google Sheets are only as public as necessary
- Consider implementing additional authentication for production use

## Troubleshooting

### "Failed to fetch data" Error
- Check that your Google Sheet is publicly accessible
- Verify the sheet URL is correct
- Ensure the sheet contains data

### Map Not Loading
- Verify your Google Maps API key is correct
- Check browser console for error messages
- Ensure Maps JavaScript API is enabled in Google Cloud Console

### GeoJSON Not Displaying
- Verify your GeoJSON format is valid
- Check that coordinates are in [longitude, latitude] format
- Ensure the data is in the correct cells

## Example Sheet Structure

| Column A | Column B |
|----------|----------|
| GeoJSON Data | More GeoJSON Data |
| `{"type":"FeatureCollection",...}` | `{"coordinates":[...],"type":"MultiLineString"}` |

The application will parse all cells in the sheet looking for valid GeoJSON data.
