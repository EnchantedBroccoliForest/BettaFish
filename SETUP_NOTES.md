# BettaFish Setup Notes

## Configuration Steps Completed

### Database Configuration
- Initialized PostgreSQL 16 database in local directory: `pg_data/`
- Created database: `bettafish`
- Created user: `bettafish` with password: `bettafish`
- Database is running on localhost:5432

### Environment Configuration
- Created `.env` file from `.env.example`
- Configured database connection for local PostgreSQL
- Database settings:
  - DB_HOST=localhost
  - DB_PORT=5432
  - DB_USER=bettafish
  - DB_PASSWORD=bettafish
  - DB_NAME=bettafish
  - DB_DIALECT=postgresql

### Dependencies Installed
- All Python dependencies from requirements.txt
- Playwright browser (Chromium)
- Key packages: Flask, Streamlit, OpenAI, PostgreSQL drivers, etc.

### Application Status
- BettaFish is running on http://0.0.0.0:5000
- PostgreSQL database server is running
- Application logs are in `logs/app.log`

## Important Notes

### LLM API Configuration
The `.env` file contains placeholder API keys for various LLM services. To use BettaFish fully, you need to:

1. **Insight Agent** - Recommended: Kimi (https://platform.moonshot.cn/)
2. **Media Agent** - Recommended: Gemini 2.5 Pro
3. **Query Agent** - Recommended: DeepSeek (https://platform.deepseek.com/)
4. **Report Agent** - Recommended: Gemini 2.5 Pro
5. **MindSpider Agent** - Recommended: DeepSeek
6. **Forum Host** - Recommended: Qwen Plus
7. **Keyword Optimizer** - Recommended: Qwen Plus
8. **Tavily API** - For web search (https://www.tavily.com/)
9. **Bocha API** - For multimodal search (https://open.bochaai.com/)

Edit the `.env` file and replace `your_api_key_here` with your actual API keys.

### Database Management
- To start PostgreSQL: `su - claude -c '/usr/lib/postgresql/16/bin/pg_ctl -D /home/user/BettaFish/pg_data -l /home/user/BettaFish/pg_data/logfile start'`
- To stop PostgreSQL: `su - claude -c '/usr/lib/postgresql/16/bin/pg_ctl -D /home/user/BettaFish/pg_data stop'`
- To check status: `su - claude -c '/usr/lib/postgresql/16/bin/pg_ctl -D /home/user/BettaFish/pg_data status'`

### Application Management
- To start BettaFish: `python app.py` (or run in background: `nohup python app.py > logs/app.log 2>&1 &`)
- To stop: Find process with `ps aux | grep "python app.py"` and kill it
- Access the web interface at: http://localhost:5000

## Next Steps

1. Configure your LLM API keys in `.env`
2. Access the application at http://localhost:5000
3. Follow the on-screen instructions to start using BettaFish
4. For crawler functionality, see `MindSpider/README.md`

## Troubleshooting

- If database connection fails, ensure PostgreSQL is running
- If packages are missing, run: `pip install -r requirements.txt`
- Check logs in `logs/app.log` for application errors
- Check `pg_data/logfile` for database errors
