# Gaze Calculator - Advanced Eye Tracking Analysis Dashboard

A web-based dashboard for analyzing and visualizing eye tracking data with advanced metrics and real-time filtering capabilities.

## Features

- Real-time data processing and visualization
- Interactive charts for eye movement, pupil dilation, and head tracking
- Advanced statistical analysis
- Confidence-based filtering
- Dark/light mode support
- Responsive design
- CSV data import support

## Getting Started

### Prerequisites

No installation required! This is a pure HTML/JavaScript application that runs in your browser.

Required browser features:

- Modern web browser with JavaScript enabled
- Support for HTML5 Canvas
- File API support for CSV uploads

### Quick Start

1. Clone this repository:

```bash
git clone https://github.com/yourusername/Gaze-Calculator.git
```

2. Open `index.html` in your web browser

3. Upload your eye tracking CSV data and start analyzing!

## Data Format

The dashboard expects CSV files with the following columns (in order):

```csv
timestamp,time_24h,x,y,confidence,pupilD,docX,docY,HeadX,HeadY,HeadZ,HeadYaw,HeadPitch,HeadRoll
1740171837807,2025-02-21 15:03:57,497.180,648.234,0.86,4.9,497.180,648.234,0.0,-7.0,45.0,0.0,9.0,0.0
```

### Column Descriptions

| Column | Description | Required | Format |
|--------|-------------|----------|--------|
| timestamp | Unix timestamp in milliseconds | Yes | Number |
| time_24h | Human-readable timestamp | Yes | YYYY-MM-DD HH:mm:ss |
| x | Horizontal gaze position | Yes | Float |
| y | Vertical gaze position | Yes | Float |
| confidence | Gaze tracking confidence | Yes | Float (0-1) |
| pupilD | Pupil diameter | No | Float or empty |
| docX | Document X coordinate | Yes | Float |
| docY | Document Y coordinate | Yes | Float |
| HeadX | Head X position | No | Float or empty |
| HeadY | Head Y position | No | Float or empty |
| HeadZ | Head Z position | No | Float or empty |
| HeadYaw | Head yaw angle | No | Float or empty |
| HeadPitch | Head pitch angle | No | Float or empty |
| HeadRoll | Head roll angle | No | Float or empty |

### Data Requirements

- Essential fields (must have valid values): timestamp, x, y
- Numeric fields can be empty (will be treated as null/0 depending on the field)
- Confidence values should be between 0 and 1
- CSV should not include a header row

## Features in Detail

### 1. Data Processing

- Automatic CSV parsing and validation
- Handles missing/invalid data gracefully
- Real-time data cleaning and normalization
- Support for large datasets

### 2. Visualization

#### Eye Movement Trajectory

- Scatter plot of gaze positions
- Confidence-based point opacity
- Real-time updates with filtering

#### Pupil Dilation

- Time series plot of pupil diameter
- Handles missing pupil data
- Automatic scaling

#### Head Movement

- 3D head position tracking
- Cumulative displacement calculation
- Angular movement visualization

#### Saccade Detection

- Velocity-based saccade detection
- Configurable threshold
- Binary classification visualization

### 3. Statistics

The dashboard computes the following metrics:

**Basic Metrics:**

- Total data points
- Valid pupil data points
- Average confidence
- Pupil diameter mean and standard deviation
- Gaze dispersion (X/Y)
- Head position means
- Head angle variances

**Advanced Metrics:**

- Saccade velocities
- Fixation durations
- Head displacement
- Pupil diameter derivatives

### 4. Filtering

- Confidence threshold filtering
- Real-time updates
- Maintains data integrity

## API Documentation

### JavaScript Functions

#### Data Processing

```javascript
processFile()
```

Handles CSV file upload and initial processing.

```javascript
cleanData(data)
```

Cleans and validates raw data.

#### Statistics

```javascript
computeBasicStats(data)
```

Computes basic and advanced statistics.

```javascript
computeSaccadeVelocities(data, velocityThreshold = 30)
```

Calculates saccade velocities.

```javascript
computeFixationDurations(data, dispersionThreshold = 20, minDuration = 100)
```

Detects fixations and calculates durations.

#### Visualization

```javascript
renderCharts()
```

Renders all visualization charts.

```javascript
createChart(id, type, labels, datasets)
```

Creates/updates individual charts.

## Future Expansions

Planned features and improvements:

1. **Data Export**
   - Export processed data
   - Export statistics as CSV/JSON
   - Chart image export

2. **Advanced Analysis**
   - Area of Interest (AOI) analysis
   - Scan path visualization
   - Heat map generation
   - Machine learning integration

3. **User Interface**
   - Custom chart configurations
   - More filtering options
   - Batch processing
   - Real-time data streaming

4. **Data Format Support**
   - Support for other eye tracking formats
   - Custom column mapping
   - Multiple file merge

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Contact

Your Name - [@yourusername](https://twitter.com/yourusername)

Project Link: [https://github.com/yourusername/Gaze-Calculator](https://github.com/yourusername/Gaze-Calculator)

## Acknowledgments

- Chart.js for visualization
- Papa Parse for CSV parsing
- Contributors and testers
