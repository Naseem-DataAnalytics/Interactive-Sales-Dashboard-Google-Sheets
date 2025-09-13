# 🚀 Interactive Sales & Operations Dashboard | Google Sheets

[![Live Dashboard](https://img.shields.io/badge/🔗-Live%20Dashboard-blue)](https://docs.google.com/spreadsheets/d/1uYhdP-HLEO9rGaw8a_adH9PUFRhoJjzh5_HuPwkFbCU/edit?usp=sharing)

---

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
- **50+ Analyst Hours Saved Annually** – Replaced repetitive manual reporting with full automation.  
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
- Built with advanced **`QUERY` functions** acting as a SQL-like engine inside Google Sheets.  
- Automated reporting via **Google Apps Script** with time-driven triggers.  
- Programmatic metric calculation + automated email distribution.  

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

### 📸 Dashboard Preview

![Dashboard Screenshot](link-to-screenshot.png)

*(Click “Live Dashboard” above to explore interactivity)*  

#### 🛠 How to Use

1. Open the [Live Dashboard](https://docs.google.com/spreadsheets/d/1uYhdP-HLEO9rGaw8a_adH9PUFRhoJjzh5_HuPwkFbCU/edit?usp=sharing).  
2. Use the dropdown filter to switch regions.  
3. KPIs and charts update instantly.  
4. (For replication) Copy the sheet → enable Apps Script trigger → edit email recipient.  

#### 🔮 Extensions & Scalability

Analytical Extensions → Extend into YoY growth, profitability ratios, predictive sales forecasting.

Enterprise Scalability → Migrate backend to BigQuery + Looker Studio for large datasets.

#### 🛠 Skills Demonstrated
**Skills:** Data Analytics | Dashboard Design | SQL (QUERY) | Google Apps Script | Automation | Business Problem-Solving




