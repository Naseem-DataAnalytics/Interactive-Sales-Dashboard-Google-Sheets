# 🚀 Automated Sales & Operations Dashboard | Google Sheets

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

---

## 📈 Business Impact
- **~50+ analyst hours/year saved (~$X,000 in productivity gains).** – Replaced repetitive manual reporting with full automation.  
- **Faster Decisions** – Managers instantly compare regional performance and reallocate resources.  
- **Single Source of Truth** – Centralized sales data aligns all teams on consistent metrics.  

---

## ✨ Key Features
- **Interactive Regional Filter** – Central dropdown to filter the entire dashboard.  
- **Real-Time KPIs** – Metrics like *Total Sales* and *Total Profit* update instantly.  
- **Dynamic Visualizations** – Auto-redrawing line chart for sales trends.  
- **“No-Touch” Email Reports** – Automated scripts deliver weekly updates without manual effort.  

---

## 💻 Technical Highlights
-Leveraged QUERY to replicate SQL-like analytics directly inside Sheets — no external database required.

-Automated workflows with Apps Script triggers, creating a lightweight ETL inside Google Sheets. 

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

### 📸 Dashboard Preview

![Dashboard Screenshot](https://raw.githubusercontent.com/Naseem-DataAnalytics/Interactive-Sales-Dashboard-Google-Sheets/main/Dashboard%20Screenshot.png)

*(Click “Live Dashboard” above to explore interactivity)*  

#### 🛠 How to Use

1. Open the [Live Dashboard](https://docs.google.com/spreadsheets/d/1uYhdP-HLEO9rGaw8a_adH9PUFRhoJjzh5_HuPwkFbCU/edit?usp=sharing).  
2. Use the dropdown filter to switch regions.  
3. KPIs and charts update instantly.  
4. (For replication) Copy the sheet → enable Apps Script trigger → edit email recipient.  

#### 🔮 Extensions & Scalability
Framework designed to scale into advanced analytics (YoY growth, profitability ratios, predictive forecasting) and enterprise-level backends (BigQuery + Looker Studio).

**Skills:** Data Analytics | Dashboard Design | SQL (QUERY) | Google Apps Script | Automation | Business Problem-Solving





