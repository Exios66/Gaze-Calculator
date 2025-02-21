# Technical Documentation

This document provides detailed technical information about the Gaze Calculator implementation.

## Architecture

The application is built as a single-page web application using vanilla JavaScript. The main components are:

1. **Data Processing Pipeline**
   - CSV parsing (Papa Parse)
   - Data cleaning and validation
   - Statistical computations

2. **Visualization Layer**
   - Chart.js for all visualizations
   - Custom chart configurations
   - Real-time updates

3. **User Interface**
   - HTML5 components
   - CSS3 with CSS Variables for theming
   - Responsive design

## Data Processing Details

### CSV Parsing

```javascript
Papa.parse(file, {
  header: false,
  dynamicTyping: false,
  skipEmptyLines: true,
  complete: function (results) {
    // Processing logic
  }
});
```

The parser is configured to:

- Skip empty lines
- Handle headerless CSV files
- Preserve string values for proper numeric conversion

### Data Cleaning

The `cleanData()` function performs the following operations:

1. Validates essential fields (timestamp, x, y)
2. Converts timestamps to Date objects
3. Parses numeric values with proper error handling
4. Handles missing values:
   - pupilD: null when missing
   - Head tracking: 0 when missing
   - Other fields: appropriate defaults

### Statistical Computations

Key statistical functions:

```javascript
mean(arr) // Arithmetic mean
variance(arr) // Population variance
standardDeviation(arr) // Standard deviation
derivative(arr, data) // Time-based derivative
```

Advanced metrics:

- Saccade velocity calculation
- Fixation duration analysis
- Head movement tracking
- Pupil dilation analysis

## Visualization Implementation

### Chart Types and Configurations

1. **Eye Movement (Scatter)**
   - X/Y coordinate plotting
   - Confidence-based opacity
   - Real-time updates

2. **Pupil Dilation (Line)**
   - Time series visualization
   - Null value handling
   - Automatic scaling

3. **Head Movement (Line)**
   - 3D position tracking
   - Cumulative displacement
   - Angular visualization

4. **Saccade Detection (Bar)**
   - Binary classification
   - Velocity thresholding
   - Time-based visualization

### Chart.js Configuration

```javascript
new Chart(ctx, {
  type: 'scatter|line|bar',
  data: {
    labels: timestamps,
    datasets: [{
      // Dataset configuration
    }]
  },
  options: {
    responsive: true,
    maintainAspectRatio: false,
    scales: { y: { beginAtZero: true } }
  }
});
```

## Performance Considerations

### Data Processing

- Efficient array operations
- Minimal object creation
- Cached computations where possible
- Incremental updates

### Memory Management

- Chart destruction before recreation
- Proper event listener cleanup
- Efficient data structure usage

### Rendering Optimization

- RequestAnimationFrame for animations
- Debounced chart updates
- Efficient DOM manipulation

## Error Handling

1. **Data Validation**
   - Type checking
   - Range validation
   - Missing value handling

2. **User Input**
   - File type validation
   - Size limits
   - Format verification

3. **Processing Errors**
   - Try-catch blocks
   - Error logging
   - User feedback

## Browser Compatibility

Tested and supported in:

- Chrome 80+
- Firefox 75+
- Safari 13+
- Edge 80+

Required features:

- File API
- Canvas API
- CSS Variables
- ES6+ JavaScript

## Development Guidelines

### Code Style

- Use ES6+ features
- Clear function naming
- Comprehensive error handling
- Performance-conscious coding

### Testing

Manual testing procedures:

1. Data loading
2. Visualization accuracy
3. Statistical computations
4. Error handling
5. Browser compatibility

### Documentation

- JSDoc comments for functions
- Clear variable naming
- Inline comments for complex logic
- Regular documentation updates

## Future Technical Considerations

### Planned Optimizations

1. **Data Processing**
   - Web Worker implementation
   - Streaming data support
   - Batch processing

2. **Visualization**
   - WebGL rendering
   - Custom shader support
   - Advanced animation

3. **Architecture**
   - Module bundling
   - TypeScript migration
   - Component architecture

### Scalability

- Large dataset handling
- Real-time processing
- Memory optimization
- Performance profiling

## API Extensions

### Planned Endpoints

1. **Data Processing**

   ```javascript
   processCustomFormat(data, format)
   exportProcessedData(format)
   ```

2. **Analysis**

   ```javascript
   analyzeAOI(coordinates)
   generateHeatmap(data)
   ```

3. **Visualization**

   ```javascript
   createCustomChart(config)
   exportChartImage(format)
   ```

## Contributing Code

### Setup

1. Fork repository
2. Install dependencies
3. Set up development environment

### Development Process

1. Create feature branch
2. Implement changes
3. Test thoroughly
4. Submit pull request

### Code Review

- Performance review
- Security check
- Style consistency
- Documentation review
