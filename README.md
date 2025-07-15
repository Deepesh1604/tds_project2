# TDS Data Analyst Agent

A powerful web-based data analysis agent that can scrape, analyze, and visualize data from various sources including Wikipedia tables and cloud databases

## 🚀 Features

- **Web Scraping**: Automatically extract data from Wikipedia tables and other web sources
- **Data Analysis**: Perform statistical calculations, correlations, and regression analysis
- **Visualization**: Generate scatter plots, bar charts, and regression lines as base64 images
- **SQL Queries**: Simulate DuckDB-style queries on cloud datasets
- **REST API**: Clean JSON-based API for integration with external systems

## 🛠️ Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/tds-data-analyst-agent.git
cd tds-data-analyst-agent

# Install dependencies
npm install

# Create environment file
cp .env.example .env

# Start the server
npm start
```

## 🌐 API Usage

### Main Endpoint
```http
POST /api/analyze
Content-Type: application/json

{
  "question": "Your data analysis question here"
}
```

### Example Questions

1. **Wikipedia Analysis**:
```json
{
  "question": "Scrape the list of highest grossing films from Wikipedia at: https://en.wikipedia.org/wiki/List_of_highest-grossing_films\n\nAnswer these questions:\n1. How many $2 bn movies were released before 2020?\n2. Which is the earliest film that grossed over $1.5 bn?\n3. What's the correlation between Rank and Peak?\n4. Draw a scatterplot of Rank vs Peak with dotted red regression line."
}
```

2. **Court Data Analysis**:
```json
{
  "question": "Analyze the Indian high court judgment dataset and answer:\n1. Which high court disposed the most cases from 2019-2022?\n2. What's the regression slope of registration to decision date delay by year in court=33_10?\n3. Plot year vs days of delay as scatterplot with regression line."
}
```

## 📊 Supported Operations

### Data Sources
- Wikipedia tables and lists
- Cloud databases (DuckDB simulation)
- CSV files and structured data
- Web APIs and JSON endpoints

### Analysis Types
- Statistical correlations
- Regression analysis
- Time series analysis
- Data aggregation and grouping
- Trend analysis

### Visualizations
- Scatter plots with regression lines
- Bar charts and histograms
- Time series plots
- Box plots and distributions
- All charts exported as base64 PNG/SVG under 100KB

## 🏗️ Architecture

```
src/
├── analyzers/          # Question-specific analyzers
│   ├── wikipediaAnalyzer.js
│   ├── courtDataAnalyzer.js
│   └── genericAnalyzer.js
├── utils/              # Utility functions
│   ├── scraper.js      # Web scraping utilities
│   ├── statistics.js   # Statistical calculations
│   └── visualization.js # Chart generation
└── routes/
    └── api.js          # API route handlers
```

## 🚀 Deployment

### Local Development
```bash
npm run dev  # Uses nodemon for auto-restart
```

### Production Deployment

#### Heroku
```bash
heroku create your-app-name
git push heroku main
```

#### Vercel
```bash
npm install -g vercel
vercel deploy
```

#### Railway
```bash
railway login
railway init
railway up
```

#### Docker
```bash
docker build -t tds-agent .
docker run -p 3000:3000 tds-agent
```

## 🔧 Configuration

### Environment Variables
```env
PORT=3000
NODE_ENV=production
CORS_ORIGIN=*
DATABASE_URL=your_database_connection_string
API_KEY=your_api_key
```

### Custom Analyzers
Add new analyzers in `src/analyzers/` and register them in `server.js`:

```javascript
const customAnalyzer = require('./src/analyzers/customAnalyzer');

// In the route handler
if (question.includes('custom pattern')) {
    result = await customAnalyzer.analyze(question);
}
```

## 🧪 Testing

```bash
# Run tests
npm test

# Test specific analyzer
node tests/wikipediaAnalyzer.test.js

# Test API endpoint
curl -X POST http://localhost:3000/api/analyze \
  -H "Content-Type: application/json" \
  -d '{"question": "Test question"}'
```

## 📈 Performance

- Handles concurrent requests efficiently
- Caches scraped data for 1 hour
- Optimized chart generation (< 100KB images)
- Rate limiting to prevent abuse
- Graceful error handling

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔗 Links

- [Live Demo](https://your-deployment-url.com)
- [API Documentation](https://your-deployment-url.com/docs)
- [GitHub Repository](https://github.com/yourusername/tds-data-analyst-agent)

## 🐛 Known Issues

- Wikipedia scraping may fail due to rate limiting
- Chart generation requires sufficient memory for large datasets
- Some complex SQL queries are simulated rather than executed

## 🚧 Roadmap

- [ ] Real DuckDB integration
- [ ] Support for more data sources
- [ ] Advanced ML analytics
- [ ] Interactive dashboards
- [ ] User authentication
- [ ] Data caching layer
