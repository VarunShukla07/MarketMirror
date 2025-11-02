# 📊 End-to-End Data Engineering Pipeline: Stock Market Analytics

## 🧠 Project Overview
This project demonstrates an end-to-end **data engineering pipeline** built on **Azure** to automate the ingestion, transformation, and visualization of stock market data.  
The system fetches stock prices from an external API, processes them using Databricks (PySpark), stores curated data in **Snowflake**, and visualizes key financial trends in **Tableau**.

---

## 🏗️ Architecture

<img width="2119" height="855" alt="image" src="https://github.com/user-attachments/assets/2d739a03-9959-4de7-9e54-3bcff44c59df" />


### 🔹 Tools & Technologies
- **Azure Data Factory (ADF)** – Orchestration and API data ingestion  
- **Azure Data Lake Storage Gen2 (ADLS)** – Centralized data storage (Bronze/Silver layers)  
- **Azure Databricks (PySpark)** – Data transformation and cleaning  
- **Snowflake** – Data warehousing (Gold layer)  
- **Tableau** – Data visualization and analytics dashboard  
- **GitHub** – Version control and CI/CD integration  

---

## 🔄 Data Flow

| Step | Layer | Tool | Description |
|------|--------|------|-------------|
| **1. Config Setup** | - | CSV file (`symbols.csv`) | Contains all stock symbols (AAPL, GOOG, TSLA, MSFT, etc.) |
| **2. Ingestion** | **Bronze** | Azure Data Factory | Reads `symbols.csv`, calls API for each symbol, and stores raw JSON data in ADLS |
| **3. Transformation** | **Silver** | Databricks (PySpark) | Flattens nested JSON, renames columns, and writes cleaned Parquet data to ADLS |
| **4. Loading** | **Gold** | ADF + Snowflake | Loads curated data from ADLS into Snowflake tables |
| **5. Visualization** | **Dashboard** | Tableau | Connects to Snowflake and visualizes stock insights |

---

## 🧱 Project ScreenShot

**ADF PIPELINE FLOW** :
<img width="1906" height="584" alt="image" src="https://github.com/user-attachments/assets/e7c9622f-5735-4b8d-a74c-c390030c6fe3" />

---

## ⚙️ Setup Instructions

1. **Clone the Repository**
   ```bash
   git clone https://github.com/<your-username>/stock-market-pipeline.git
   cd stock-market-pipeline


2. **Import ADF Pipelines**

   * In Azure Data Factory → *Manage → ARM Template → Import*
   * Upload from `adf_arm_templates/`

3. **Upload Databricks Notebooks**

   * Import `.ipynb` or `.dbc` files from `notebooks/`

4. **Configure Linked Services**

   * Connect **ADLS**, **Snowflake**, and **API** credentials (store secrets in Key Vault)

5. **Run Pipeline**

   * Trigger the main pipeline to fetch and transform stock data
   * Verify results in Snowflake and Tableau

---

## 📈 Tableau Dashboard

1. **Stock Price with Moving Averages** – Displayed short-term and long-term trends in stock movement.
<img width="4424" height="1198" alt="Stock Price with Moving Averages" src="https://github.com/user-attachments/assets/5065a550-bce7-4eec-8a9e-b7f56cb1035f" />

2. **Volume & Price Activity (Dual-Axis Chart)** – Showed correlation between stock price and trading volume.
<img width="4584" height="1472" alt="image" src="https://github.com/user-attachments/assets/a374e7ba-aafd-4b7b-9877-4a01b45007b3" />

3. **Returns & Performance Trends** – Visualized returns over time to evaluate stock performance.
<img width="5102" height="1472" alt="image" src="https://github.com/user-attachments/assets/8b823b24-32d5-4f04-be6d-ac5b816bb146" />

---

## 🧩 Key Learnings

* End-to-end orchestration using **ADF + Databricks + Snowflake**
* JSON flattening and schema normalization in **PySpark**
* Integrating cloud data pipelines with **Tableau** for analytics
* Understanding of **Bronze–Silver–Gold** layered data architecture

---

## 🪪 License

This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.
