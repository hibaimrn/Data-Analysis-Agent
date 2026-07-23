# Datastack — Talk to Your Data

A web-based AI-powered data analysis agent that lets you ask natural language questions about your CSV data and get instant answers with visualizations.

## Overview

Datastack is a single-file HTML application that combines CSV data handling with OpenAI's language models to enable intuitive data exploration. Upload a CSV file, ask questions in plain English, and get automated analysis, tables, and charts—all without writing code.

## Features

✨ **Natural Language Analysis**
- Ask questions about your data in plain English
- AI agent interprets your query and generates JavaScript to analyze your data
- No SQL or coding knowledge required

📊 **Rich Visualizations**
- Automatic chart generation (bar, line, pie charts)
- Interactive tables with scrolling for large datasets
- Key Performance Indicators (KPIs) dashboard

📁 **CSV Support**
- Upload CSV files up to your browser's memory limit
- Automatic schema detection with column type inference
- Supports text, numeric, and date columns

🎨 **Modern UI**
- Dark theme with teal and clay accents
- Responsive design (desktop and mobile)
- Smooth animations and micro-interactions
- Professional typography (Fraunces, Space Grotesk, JetBrains Mono)

🔒 **Privacy-Focused**
- Client-side data processing
- Your data never leaves your browser except for API calls to OpenAI
- No backend server required

## Getting Started

### Prerequisites

- OpenAI API key (for GPT-4 or compatible model)
- Modern web browser (Chrome, Firefox, Safari, Edge)
- CSV file to analyze

### Setup

1. **Open the Application**
   - Save `data_analysis_agent.html` to your computer
   - Open in any modern web browser (double-click or drag to browser)

2. **Configure API Key**
   - Click the **Setup** section at the top
   - Paste your OpenAI API key in the "API Key" field
   - Choose your model (default: `gpt-4-turbo`)
   - *(Recommended: Store key in browser LocalStorage for convenience)*

3. **Upload Your Data**
   - Click **Choose CSV File**
   - Select a CSV from your computer
   - View the detected schema (columns, data types)
   - System automatically profiles your data

4. **Ask Questions**
   - Type your question in the chat input
   - Example: _"What's the total revenue by region?"_
   - Example: _"Show me sales trend over time"_
   - Example: _"Calculate average customer value"_

5. **View Results**
   - AI generates analysis code and executes it on your data
   - Results display as:
     - **Summary statement** (key insight)
     - **Table** (detailed data)
     - **Chart** (if applicable)
     - **Generated code** (transparency)

## How It Works

### Data Flow

```
CSV Upload → Schema Detection → User Question
                                      ↓
                              OpenAI API Call
                                      ↓
                          AI Generates Analysis Code
                                      ↓
                          JavaScript Execution
                                      ↓
                        Results + Chart Rendering
                                      ↓
                          Chat Display + History
```

### AI Analysis Process

1. **System Prompt**: Instructs the model to generate JavaScript that processes your data
2. **Context**: Schema information and sample data are sent to OpenAI
3. **Code Generation**: Model returns JavaScript function code
4. **Execution**: Code runs in your browser against the uploaded data
5. **Visualization**: Results are formatted as tables, KPIs, and charts

## Usage Examples

### Example 1: Sales Summary
**Question:** "What are total sales by region?"

**Expected Result:**
- Table showing regions and totals
- Bar chart comparing regions
- Summary statement with highest/lowest region

### Example 2: Trend Analysis
**Question:** "Show me monthly revenue trends for the last year"

**Expected Result:**
- Line chart showing monthly progression
- Summary with growth percentage
- Table of monthly values

### Example 3: Statistical Summary
**Question:** "What's the average order value and how many orders above average?"

**Expected Result:**
- Summary with calculated metrics
- Table of above-average orders
- Summary statistics

## Interface Guide

### Setup Panel
- **API Key**: Your OpenAI API key (required)
- **Model**: Model selection dropdown (defaults to gpt-4-turbo)
- **CSV File Upload**: Select data file
- **Schema View**: Auto-generated column information with type indicators
  - 🟢 Teal dot = numeric data
  - 🟠 Clay dot = text data
  - 🟡 Gold dot = date data

### Chat Area
- **User Messages** (clay-colored): Your questions
- **Agent Messages** (teal-colored): AI responses with analysis
- **Answer Pill**: Marks where the actual answer begins
- **Generated Code**: Shows the JavaScript executed on your data

### Dashboard
- **KPIs**: Key metrics displayed prominently
- **Chart Cards**: Visual representations of data
- **Results Table**: Detailed data output (max 25 rows visible)

## Configuration

### API Key Storage
The app supports storing your API key in browser LocalStorage for convenience between sessions. Click the **Save** checkbox to enable.

**⚠️ Security Note:** Only enable LocalStorage on trusted devices. Store your API key securely.

### Model Selection
Common options:
- `gpt-4-turbo` - Latest, most capable (recommended)
- `gpt-4` - Stable, reliable
- `gpt-3.5-turbo` - Faster, cheaper

## Data Specifications

### Supported Formats
- CSV files with headers
- Comma, semicolon, or tab-separated values
- UTF-8 encoding
- Up to ~100MB (browser dependent)

### Data Type Detection
- **Numbers**: Integers, decimals, percentages
- **Text**: String fields, categories
- **Dates**: ISO format (YYYY-MM-DD), common formats
- **Empty**: Null, undefined, or empty cells

### Column Requirements
- Header row (first row) must contain column names
- No special characters in column names (replaced with underscores)
- Consistent data types per column (recommended)

## Advanced Features

### Chart Types
The AI agent can generate:
- **Bar charts**: Comparisons across categories
- **Line charts**: Time series and trends
- **Pie charts**: Proportional composition
- **None**: When data isn't suitable for visualization

### Result Formats

Results are returned as JavaScript objects with this structure:

```json
{
  "summary": "Key insight about the data",
  "table": [
    { "column1": "value", "column2": 123 },
    { "column1": "value", "column2": 456 }
  ],
  "chart": {
    "type": "bar",
    "title": "Chart Title",
    "labels": ["Category A", "Category B"],
    "values": [100, 200]
  }
}
```

### Generated Code
All analysis code is shown in the interface. You can:
- Review the generated logic
- Learn how questions were interpreted
- Audit data processing
- Copy code for external use

## Troubleshooting

### "API Error" Message
- Verify your OpenAI API key is correct
- Check you have API credits available
- Ensure your IP isn't rate-limited

### "Code Execution Error"
- Try rephrasing your question more specifically
- Check your CSV has consistent data types
- Ensure column names don't have special characters
- Try with a simpler question first

### Chart Not Rendering
- Verify the AI generated numeric labels and values
- Check that your data actually matches what you asked
- Reload the page and try again

### Performance Issues
- Large CSVs (>50MB) may be slow
- Try asking simpler questions first
- Close other browser tabs
- Use a supported modern browser

## Technical Stack

### Frontend
- **HTML5**: Semantic markup
- **CSS3**: Custom properties, flexbox, grid, animations
- **JavaScript**: Vanilla ES6+ (no frameworks)

### Libraries
- **PapaParse** (v5.4.1): CSV parsing
- **Chart.js** (v4.4.1): Data visualization
- **Google Fonts**: Typography (Fraunces, Space Grotesk, JetBrains Mono)

### External Services
- **OpenAI API**: Model inference for code generation

## Browser Compatibility

✅ **Fully Supported:**
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

⚠️ **Partial Support:**
- Mobile browsers (optimized, works well)
- Older browsers (CSS variables required)

## Privacy & Security

- **Client-side Processing**: CSV data stays in your browser
- **API Calls Only**: Only API key and analyzed queries sent to OpenAI
- **No Tracking**: No analytics or telemetry
- **HTTPS**: Use over secure connection in production

⚠️ **Important**: Treat your OpenAI API key like a password. Never share it or commit it to version control.

## Limitations

- Single CSV file per session (reload to switch)
- No data persistence between sessions (data cleared on refresh)
- Chart generation depends on AI interpretation accuracy
- Large datasets (>1M rows) may cause browser slowness
- Some complex queries may need rephrasing

## Tips for Best Results

1. **Clear Column Names**: Use simple, descriptive names without special characters
2. **Consistent Data**: Keep each column to one data type (all numbers or all text)
3. **Be Specific**: "Revenue by region in Q4 2023" > "Show revenue"
4. **Check Generated Code**: Review the JavaScript to see how your question was interpreted
5. **Iterative Analysis**: Ask follow-up questions to refine results

## Examples by Data Type

### E-commerce Data
- "What products had the most orders last month?"
- "Average order value by customer segment"
- "Top 10 best-selling SKUs"

### Financial Data
- "Calculate ROI for each marketing channel"
- "Monthly cash flow forecast"
- "Budget vs actual spending by department"

### Survey Data
- "How many respondents chose option A?"
- "Satisfaction score distribution"
- "Cross-tabulation of demographics vs responses"

## Future Enhancements

Potential features for future versions:
- Multi-file dataset joining
- Data export (JSON, Excel)
- Query history/persistence
- Custom chart styling
- Real-time data source connections
- Collaborative analysis sharing

## Support

For issues or questions:
1. Check the Troubleshooting section above
2. Review the generated code for clues
3. Try rephrasing your question
4. Verify your CSV format and data types
5. Ensure your OpenAI API key is valid and has credits

## License

This application is provided as-is. Ensure compliance with OpenAI's terms of service when using the API.

## Credits

Built with:
- OpenAI GPT-4/3.5 Turbo
- Chart.js visualization library
- PapaParse CSV parser
- Google Fonts typography

---

**Version**: 1.0  
**Last Updated**: July 2026  
**Status**: Active
