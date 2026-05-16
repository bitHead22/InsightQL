![demo](./assets/demo.png)

# InsightQL - Talk to your Database 🤖

A powerful AI-powered database query tool that translates natural language questions into SQL queries using **Groq AI** and **LangChain**. This application allows users to interact with their MySQL databases using plain English, making database operations accessible to non-technical users.

## Features ✨

- 🗄️ **Natural Language Processing**: Ask database questions in plain English
- 🤖 **AI-Powered SQL Generation**: Uses Groq AI (Mixtral-8x7b-32768) to convert questions to SQL
- 📊 **Interactive Results**: View query results in clean, sortable DataFrames
- 📝 **Business Insights**: Get AI-generated explanations of query results
- 🔍 **SQL Preview**: Review generated SQL queries before execution
- ⚙️ **Easy Configuration**: Simple setup with API keys and connection strings
- 🔒 **Secure Connections**: SSL-enabled MySQL database connections
- 🎯 **Example Questions**: Quick-start templates for common queries

## Tech Stack 🛠️

- **Frontend**: Streamlit
- **LLM Framework**: LangChain
- **AI Provider**: Groq (Mixtral-8x7b-32768)
- **Database**: MySQL
- **Package Manager**: uv
- **Language**: Python 3.11+

## Prerequisites 🛠️

- Python 3.11 or higher
- [Groq API key](https://console.groq.com) (free tier available)
- MySQL database (local or remote)

## Installation 📥

1. **Clone the repository:**

   ```bash
   git clone https://github.com/bitHead22/InsightQL.git
   ```

2. **Create a `.env` file in the project root with your Groq API key:**

   ```env
   GROQ_API_KEY=your_groq_api_key_here
   ```

   Get your free Groq API key from: https://console.groq.com

3. **Install dependencies using uv:**

   ```bash
   uv sync
   ```

   If you don't have uv installed, install it from: https://docs.astral.sh/uv/

## Usage 🚀

1. **Start the Streamlit application:**

   ```bash
   uv run streamlit run app.py
   ```

2. **Open your browser** - Navigate to: `http://localhost:8502` (or the URL shown in your terminal)

3. **Configure in the sidebar:**
   - Your Groq API key is automatically loaded from `.env`
   - Enter your MySQL connection string in the format:
     ```
     mysql://username:password@host:port/database
     ```

4. **Ask questions in plain English:**

   Examples:
   - "What are the product categories we have?"
   - "Show me all products with their prices"
   - "How many orders do we have?"
   - "What are the top 5 most expensive products?"
   - "Show me users and their order counts"
   - "List all orders from the last month"

5. **Review and execute:**
   - The generated SQL query is shown for your review
   - Click "Execute Query" to run it
   - Get AI-powered explanations of the results

## Database Connection 🔗

### Connection String Format

```
mysql://username:password@hostname:port/database_name
```

**Example:**
```
mysql://root:password123@localhost:3306/ecommerce
```

### Supported Operations 📊

#### Query Types

- **SELECT queries**: Data retrieval and analysis
- **Complex JOINs**: Multi-table queries with relationships
- **Aggregations**: COUNT, SUM, AVG, MIN, MAX operations
- **Filtering**: WHERE clauses and complex conditions
- **Sorting**: ORDER BY operations
- **Limiting**: LIMIT clauses for large datasets

#### Example Questions

- "Show me all users who made purchases"
- "What's the total revenue from completed orders?"
- "Which products are out of stock?"
- "Find the most popular product categories"
- "Show me top 10 customers by spending"
- "List orders by date with customer details"

## Configuration & Setup 🔧

### Environment Variables

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key
```

### Database Setup

Ensure your MySQL database is accessible and contains the following schema:

```
- category (id, uuid, name, description, date_created, date_updated)
- product (id, uuid, name, description, price, stock_quantity, category_id, date_created, date_updated)
- product_category (id, product_id, category_id)
- user (id, uuid, name, email, address, date_created, date_updated)
- order (id, uuid, user_id, total_amount, status, order_date, date_created, date_updated)
- order_item (id, order_id, product_id, quantity, unit_price, date_created, date_updated)
```

## Project Structure 📁

```
talk_to_db/
├── app.py                 # Main Streamlit application
├── database.py            # Database connection and query execution
├── ai_services.py         # Groq AI integration and SQL generation
├── pyproject.toml         # Project dependencies
├── .env.example           # Environment variables template
├── .gitignore             # Git ignore rules
├── README.md              # This file
└── assets/
    ├── demo.png           # Demo screenshot
    ├── langchain.png      # LangChain logo
    └── gibson.svg         # Branding asset
```

## Architecture 🏗️

### Modular Design

- **UI Layer** (`app.py`): Streamlit interface and user interactions
- **Database Layer** (`database.py`): MySQL connection management and secure query execution
- **AI Layer** (`ai_services.py`): LangChain + Groq AI integration for natural language to SQL translation and result explanation

### Key Components

1. **Connection String Parser**: Safely parses and validates MySQL connection strings
2. **SQL Translator**: Uses Groq AI + LangChain to convert natural language to SQL queries
3. **Query Executor**: Safely executes SQL queries with error handling
4. **Result Explainer**: Generates human-readable explanations of query results
5. **Session Management**: Maintains query history and state

## Example Workflow 🔄

1. **Ask a Question**: "What are the top 5 most expensive products?"
2. **AI Generates SQL**: `SELECT id, name, price FROM product ORDER BY price DESC LIMIT 5`
3. **Review SQL**: Check the generated query for accuracy
4. **Execute Query**: Run the query on your database
5. **View Results**: See results in a formatted table
6. **Get Explanation**: AI provides business insights about the results

## Troubleshooting 🔧

### Common Issues

**Module not found errors:**
```bash
uv sync
uv run streamlit run app.py
```

**Port already in use:**
```bash
uv run streamlit run app.py --server.port 8503
```

**API Key not recognized:**
- Verify `.env` file is in the correct directory
- Check Groq API key is valid and active
- Restart the Streamlit app after updating `.env`

## Performance Notes ⚡

- Groq's free tier is generous with rate limits
- Responses are typically generated within 1-2 seconds
- Best performance with simple, well-structured questions

## Contributing 🤝

Contributions are welcome! Please feel free to:
- Submit issues for bugs or feature requests
- Create pull requests with improvements
- Improve documentation

## License 📄

This project is licensed under the MIT License - see the LICENSE file for details.

## Support 💬

For issues, questions, or suggestions:
- Open an issue on GitHub
- Check existing documentation
- Review Groq API limits at https://console.groq.com
