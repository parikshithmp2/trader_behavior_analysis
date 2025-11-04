## Overview  
This project analyzes how **market sentiment** affects **trader performance** in crypto markets.  
Using historical trading data and sentiment indices, it reveals behavioral trends and helps identify patterns during high fear or high greed periods.


##  Dataset Description  

### **Bitcoin Market Sentiment Dataset**
| Column | Description |
|--------|--------------|
| Date | Date of sentiment index |
| Classification | Market sentiment (Fear / Greed) |

### **Hyperliquid Trader Dataset**
| Column | Description |
|--------|--------------|
| account | Trader account ID |
| symbol | Crypto symbol (e.g., BTCUSDT) |
| execution price | Price of trade |
| size | Trade size |
| side | Buy/Sell |
| time | Execution time |
| closedPnL | Profit or Loss for trade |
| leverage | Leverage used |
| ... | Additional trading metadata |


##  Data Processing Steps  

 **Data Loading & Cleaning**
- Loaded both datasets with pandas  
- Converted timestamps using `pd.to_datetime(dayfirst=True)`  
- Cleaned invalid or missing timestamps  

 **Feature Engineering**
- Extracted `date` field for joining  
- Merged trades and sentiment datasets on date  
- Created new metrics (average PnL, win ratio, leverage stats per day)

 **Exploratory Analysis**
- Grouped trades by sentiment category  
- Visualized PnL distributions, trade volume, and leverage trends  
- Compared performance between *Fear* and *Greed* days  

 **Statistical Analysis**
- Applied **Mann–Whitney U Test** to test if trader PnL differs significantly between Fear vs Greed periods  
- Null hypothesis rejected → trader performance **is sentiment-dependent**


##  Key Insights  

 **Higher Greed → higher trade volume but lower average PnL**  
 **Fear phases → fewer trades but more disciplined (higher median PnL)**  
 **Statistical test confirms behavioral shift** (p-value < 0.05)


##  Technologies Used
- **Python 3.11**
- **Pandas, Numpy, Seaborn, Matplotlib, Scipy**
- **Jupyter Notebook**


##  How to Run Locally  

```bash
# Clone the repository
git clone https://github.com/parikshithmp2/trader_behavior_analysis.git

# Navigate to folder
cd trader_behavior_analysis

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter Notebook
jupyter notebook trader_behavior_analysis.ipynb
