# 🚀Automated Sales & Operations Dashboard (9K+ rows → Instant Insights)| Google Sheets

[![Live Dashboard](https://img.shields.io/badge/🔗-Live%20Dashboard-blue)](https://docs.google.com/spreadsheets/d/1uYhdP-HLEO9rGaw8a_adH9PUFRhoJjzh5_HuPwkFbCU/edit?usp=sharing)

---
**Transformed a static 9K+ row dataset into a self-service reporting tool that saves 50+ analyst hours annually and enables faster regional decision-making.
Built end-to-end with Google Sheets (QUERY) and Apps Script automation, replacing repetitive manual reporting with a scalable, interactive dashboard.**

## 📌 Overview  

Most sales teams waste hours on manual reporting.  
This project eliminates that bottleneck by turning a static **9,000+ row dataset** into an **interactive, automated dashboard** that empowers instant decision-making.  

It demonstrates **end-to-end data analytics skills**:  
- Problem framing  
- Data transformation  
- Visualization design  
- Workflow automation  

✅ **Result** → A scalable reporting tool that saves ~1 hour/week per analyst (~50+ hours/year) while empowering managers with **instant, self-service insights**.  

**Skills:** Data Analytics | Dashboard Design | SQL (QUERY) | Google Apps Script | Automation | Business Problem-Solving  


---

## 📈 Business Impact  
- **~50+ analyst hours/year saved (~$X,000 in productivity gains)** → Manual reporting eliminated.  
- **Faster decisions** → Managers instantly compare regional performance and reallocate resources.  
- **Single source of truth** → Centralized sales data aligns all teams on consistent metrics.  


---

## ✨ Key Features  
- **Interactive Regional Filter** → Managers drill down to their region without analyst support.  
- **Real-Time KPIs** → Always up-to-date metrics (e.g., *Total Sales*, *Total Profit*).  
- **Dynamic Visualizations** → Charts automatically redraw to reflect filters and trends.  
- **“No-Touch” Email Reports** → Automated weekly updates delivered without manual effort.  

---

## 💻 Technical Highlights  
- **SQL-like analytics with `QUERY`** → Database-style queries directly inside Google Sheets.  
- **Lightweight ETL with Apps Script** → Automated transformations with time-driven triggers.  
- **Programmatic KPI calculations** → Metrics updated dynamically for dashboards + email reports.  
- **Automated distribution** → Reports delivered directly to inboxes.  


<details>
<summary>📂 Tech Appendix (Click to Expand)</summary>

### QUERY Function Examples
```sql
-- Total Sales
=QUERY('Raw Data'!A:U, "SELECT SUM(R) WHERE M = '"&B1&"' LABEL SUM(R) ''")

-- Total Profit
=QUERY('Raw Data'!A:U, "SELECT SUM(U) WHERE M = '"&B1&"' LABEL SUM(U) ''")

-- Dynamic Chart Data
=QUERY('Raw Data'!A:U, "SELECT YEAR(C), SUM(R) 
 WHERE M = '"&B1&"' 
 GROUP BY YEAR(C) 
 ORDER BY YEAR(C) 
 LABEL YEAR(C) 'Year', SUM(R) 'Total Sales'")
```
### Google Apps Script for Automation
```
/**
 * Calculates total sales for a given region
 * and sends a summary report via email.
 */
function sendSalesReport(regionName = "Central") {
  const SHEET_NAME = "Raw Data";
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(SHEET_NAME);
  const data = sheet.getDataRange().getValues();
  let regionSales = 0;

  for (let i = 1; i < data.length; i++) { // skip header row
    const row = data[i];
    const region = row[12]; // Column M
    const sales = Number(row[17]) || 0; // Column R
    if (region === regionName) {
      regionSales += sales;
    }
  }

  const recipient = "your_email@example.com";
  const subject = `Automated Weekly Sales Report: ${regionName} Region`;
  const body = `This is your automated weekly report.\n\n` +
               `Total sales for the ${regionName} region are: $${regionSales.toFixed(2)}`;

  MailApp.sendEmail(recipient, subject, body);
}

```
</details>

---

### 📸 Dashboard Preview

![Dashboard Screenshot](https://raw.githubusercontent.com/Naseem-DataAnalytics/Interactive-Sales-Dashboard-Google-Sheets/main/Dashboard%20Screenshot.png)

*(Click “Live Dashboard” above to explore interactivity)*  

---

#### 🛠 How to Use

1. Open the [Live Dashboard](https://docs.google.com/spreadsheets/d/1uYhdP-HLEO9rGaw8a_adH9PUFRhoJjzh5_HuPwkFbCU/edit?usp=sharing).  
2. Use the dropdown filter to switch regions.  
3. KPIs and charts update instantly.  
4. (For replication) Copy the sheet → enable Apps Script trigger → edit email recipient.

---   

#### 🔮 Extensions & Scalability
Framework designed to scale into advanced analytics (YoY growth, profitability ratios, predictive forecasting) and enterprise-level backends (BigQuery + Looker Studio).

---
#### 🧑‍💻 Skills Demonstrated  
- **Spreadsheet Engineering** → Designed interactive dashboards using Google Sheets.  
- **SQL-like Querying** → Used QUERY function to perform advanced analytics inside Sheets.  
- **Automation Scripting** → Built workflows with Google Apps Script triggers.  
- **ETL & Data Processing** → Created lightweight pipelines for cleaning and transforming raw data.  
- **Business Communication** → Automated email reports to stakeholders with actionable insights.  






