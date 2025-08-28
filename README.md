■ Detailed Documentation of the Approach
1. Introduction
This project was developed as part of the CrowdWisdomTrading Internship Assessment.
The assignment required designing a backend Python solution that could: 1. Scrape
prediction/gambling market data from multiple platforms. 2. Identify and unify products that
refer to the same real-world event. 3. Compare their prices across platforms. 4. Export the
results into a structured CSV file for analysis. The project demonstrates skills in data
scraping, data processing, fuzzy matching, CSV generation, and modular Python design. It
also simulates the use of a multi-agent system, as in CrewAI-based workflows.
2. Problem Statement
Prediction markets exist on different websites (e.g., Polymarket, Kalshi,
Prediction-Market). Each website may host similar or identical contracts, such as 'Trump
wins 2024' vs. 'Trump presidency 2024'. These mean the same but are priced
independently and worded differently. Challenges: • Data Collection: Extracting market
data from various websites, some with JavaScript rendering. • Product Matching:
Identifying whether differently worded contracts represent the same event. • Data
Unification: Combining data into one structured list. • Confidence Estimation: Deciding how
confident we are in product matching.
3. Design Approach
The solution follows a three-agent structure: • Agent 1: Data Collector – Scrapes names
(Polymarket) and uses mocked sample prices (Kalshi, Prediction-Market). • Agent 2:
Product Identifier – Uses fuzzy string matching (difflib) to unify similar products with
confidence levels. • Agent 3: Data Organizer – Creates a pandas DataFrame and exports
results to CSV. Tools used: requests, BeautifulSoup4, pandas, difflib, logging.
4. Workflow
1. Data Collection: Scrape Polymarket names, simulate Kalshi & Prediction-Market prices.
2. Product Identification: Apply fuzzy matching to unify markets. 3. Data Organization:
Build CSV with unified product list and confidence levels.
5. Sample Input & Output
Input Example (Collector output JSON): { 'polymarket': [{'name': 'Trump wins 2024', 'price':
null}, {'name': 'Bitcoin > 100k in 2025', 'price': null}], 'kalshi': [{'name': 'Trump wins 2024',
'price': 0.62}, {'name': 'Bitcoin > 100k in 2025', 'price': 0.42}], 'prediction-market': [{'name':
'Trump presidency 2024', 'price': 0.64}] } Output Example (CSV): Product | Confidence |
Polymarket | Kalshi | Prediction-Market Trump wins 2024 | High | None | 0.62 | 0.64 Bitcoin
> 100k in 2025 | Medium | None | 0.42 | NaN
6. Tools & Technologies
• Python 3.9+ • Libraries: requests, BeautifulSoup4, pandas, difflib, logging Why not
CrewAI/Browser-use? Heavy dependencies & async setup complexity. Simpler Python
tools were used to ensure guaranteed execution while maintaining agent-based design.
7. Workflow Diagram
DataCollector (scraping/mocking data) ↓ ProductIdentifier (fuzzy matching) ↓
DataOrganizer (CSV output)
8. Evaluation Against Requirements
✔ Working Output: Generates unified_markets.csv ✔ Agent-Based Design: Collector,
Identifier, Organizer ✔ Data Retrieval & Processing: Scraped + mocked ✔ CSV Output:
Structured and clear ✔ Logging: Debugging support ✔ Code Clarity: Modular and
maintainable
9. Limitations
• Dynamic Rendering: Polymarket & Kalshi prices need JavaScript rendering. • Sample
Data: Mock prices used for demonstration. • Matching Logic: Based on difflib, could be
enhanced with embeddings.
10. Future Enhancements
• Integrate Playwright/Browser-use for dynamic prices. • Add more platforms. • Use
embeddings for better product matching. • Add chatbot/RAG for querying. • Visualize
prices with graphs.
11. Conclusion
The project demonstrates the ability to design an agent-based pipeline for data scraping,
unification, and CSV export. It is modular, extendable, and meets assignment
requirements. It also shows awareness of limitations and future improvements, which can
be implemented for real-world deployment.
