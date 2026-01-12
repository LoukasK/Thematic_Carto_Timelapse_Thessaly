# Population Timelapse Animation Map with Municipal Boundaries

An interactive web-based cartographic visualization showing population change over time using MapLibre GL JS. Features animated proportional symbols with Flannery scaling, municipal boundary overlays, and comprehensive student documentation.

## Features

- **Time-series Animation**: Automated playback through multiple time periods (1991-2021) with play/pause controls
- **Proportional Symbols**: Population represented by circles using perceptually accurate Flannery scaling (exponent 0.57)
- **Municipal Boundaries**: Geographic context provided by administrative boundary overlays
- **Interactive Controls**: 
  - Year slider for manual navigation
  - Animation speed control (200-2000ms per frame)
  - Circle size adjustment (30-150px max radius)
  - Opacity control (0-100%)
- **Dynamic Legend**: Nested concentric circles showing four representative population values (1,000 / 10,000 / 50,000 / 100,000)
- **Basemap Switching**: Toggle between Light and Dark CartoDB basemaps
- **Rendering Order Optimization**: Circles sorted by size (largest first) ensuring smaller features remain visible when overlapping

## Technical Implementation

### Core Technologies
- **MapLibre GL JS 3.6.2**: Open-source vector tile mapping library
- **GeoJSON**: Population point data and polygon boundaries
- **SVG**: Dynamic legend generation

### Key Cartographic Principles
1. **Flannery Scaling**: Uses power exponent of 0.57 for perceptually accurate size representation
2. **Data-Driven Styling**: Circle sizes calculated across all time periods to maintain consistent visual scale
3. **Feature Sorting**: GeoJSON features sorted by population (descending) to prevent occlusion of smaller circles
4. **Temporal Continuity**: Min/max values calculated across entire time series for meaningful animation

### Data Requirements
- **Population Points**: GeoJSON with point geometries and multiple year columns (e.g., POP1991, POP2001, POP2011, POP2021)
- **Boundaries**: GeoJSON with polygon/multipolygon geometries representing administrative divisions
- **Coordinate System**: WGS84 (EPSG:4326)

## Student Customization

Extensively documented for educational use with clear modification points:

**🌍 Mandatory Changes:**
- Map center coordinates and zoom level
- GeoJSON file paths (population points and boundaries)
- Year column names in data
- Legend population thresholds and labels
- Map title, data source, and author information

**🗺️ Optional Styling:**
- Circle fill and stroke colors
- Boundary line appearance (color, width, opacity)
- Animation speed and default circle size
- Basemap options

## File Structure
```
├── index.html                          # Main application (single file)
├── data/
│   ├── dimoi_poipop_WGS.geojson       # Population point data
│   └── dimoi_oria_WGS.geojson         # Municipal boundaries
```

## Usage

1. **Update Data Configuration** (Lines ~285-340):
```javascript
   const YEAR_COLUMNS = ['POP1991', 'POP2001', 'POP2011', 'POP2021'];
   const YEARS = [1991, 2001, 2011, 2021];
   const DATA_PATH = 'data/dimoi_poipop_WGS.geojson';
   const BOUNDARIES_PATH = 'data/dimoi_oria_WGS.geojson';
```

2. **Set Map Center** (Lines ~342-365):
```javascript
   center: [22.4, 39.6],  // [longitude, latitude]
   zoom: 8
```

3. **Customize Legend** (Lines ~805-841):
```javascript
   const value1 = 1000;    // Adjust to match your data range
   const value2 = 10000;
   const value3 = 50000;
   const value4 = 100000;
```

4. Open `index.html` in a web browser (no build process required)

## Documentation Highlights
- **Inline Comments**: Over 500 lines of educational documentation explaining cartographic principles, code logic, and customization options
- **Line Number References**: Cross-references throughout code guide students to related sections
- **Color Blending Explanation**: Detailed notes on how overlapping transparent circles interact visually

## Educational Context
Designed for undergraduate/graduate cartography courses covering:
- Temporal data visualization
- Proportional symbol mapping
- Perceptual scaling theory (Flannery 1971)
- Interactive web cartography
- GeoJSON data handling

## Browser Compatibility
- Chrome/Edge 90+
- Firefox 88+
- Safari 14+
- Requires WebGL support

## Credits
Based on population data from the Hellenic Statistical Authority (ELSTAT). Developed as educational material for thematic cartography courses at the National Technical University of Athens (NTUA), Cartography Laboratory.

## License
Educational use. Please credit original authors when adapting for your own projects.
