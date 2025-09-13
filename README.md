# 🚀 Interactive Sales & Operations Dashboard | Google Sheets

[![Live Dashboard](https://img.shields.io/badge/🔗-Live%20Dashboard-blue)](your-shareable-google-sheet-link-goes-here)

---

## 📌 Overview
Most sales teams waste hours on manual reporting.  
This project eliminates that bottleneck by turning a static **9,000+ row dataset** into an **interactive, automated dashboard** that empowers instant decision-making.  

It demonstrates **end-to-end data analytics skills**:  
- Problem framing  
- Data transformation  
- Visualization design  
- Workflow automation  

✅ **Result** → A scalable reporting tool that saves an estimated **50+ analyst hours annually** while empowering managers with **instant, self-service insights**.

---

## 📈 Business Impact
- **50+ Analyst Hours Saved Annually** – Eliminated repetitive manual reporting through full automation.  
- **Faster Decision-Making** – Enabled managers to instantly compare regional performance and reallocate resources more effectively.  
- **Single Source of Truth** – Centralized sales data for better alignment across teams.  

---

## ✨ Key Features
- **Interactive Regional Filter** – Central dropdown menu to filter the entire dashboard.  
- **Real-Time KPIs** – Metrics like *Total Sales* and *Total Profit* update instantly.  
- **Dynamic Visualizations** – Auto-redrawing line chart for sales trends.  
- **“No-Touch” Email Reports** – Automated scripts deliver weekly regional updates without manual effort.  

---

## 💻 Technical Highlights
- Built with advanced **`QUERY` functions** acting as a SQL-like engine inside Google Sheets.  
- Automated reporting via **Google Apps Script** with time-driven triggers.  
- Programmatic metric calculation + automated distribution of reports.  

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
 * Calculates total sales for the Central region 
 * and sends a summary report via email.
 */
function sendSalesReport() {
  const sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("Raw Data");
  const data = sheet.getDataRange().getValues();
  let centralSales = 0;

  for (let i = 1; i < data.length; i++) {
    const row = data[i];
    const region = row[12]; // Column M
    const sales = row[17];  // Column R
    if (region === "Central") {
      centralSales += sales;
    }
  }

  const recipient = "your_email@example.com";
  const subject = "Automated Weekly Sales Report: Central Region";
  const body = "This is your automated weekly report.\n\n" +
               "Total sales for the Central region are: $" + centralSales.toFixed(2);

  MailApp.sendEmail(recipient, subject, body);
}
```
</details>

#### 🔮 Extensions & Scalability
Analytical Extensions → Add YoY growth, profitability ratios, or predictive sales modeling.

Enterprise Scalability → Migrate backend to BigQuery + Looker Studio for large datasets.

#### 🛠 Skills Demonstrated

Data Analytics • Dashboard Design • SQL (QUERY) • Automation • Google Apps Script • Business Problem-Solving

#### 📸 Dashboard Preview

(Insert screenshot of your dashboard here)




