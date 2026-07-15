# 📊 Google Sheets + Gemini AI Sales Analyzer

Transform natural language queries into instant database calculations within Google Sheets using Google Apps Script and the **Gemini 2.5 Flash API**.

---

## 🌟 Features

* **Natural Language Processing:** Type human questions like *"How much profit did we make from Office Supplies in Texas?"* in cell `B2`.
* **Automated Data Extraction:** Gemini extracts parameters (Customer, State, Category) and identifies the target metric (`Sales` or `Profit`).
* **Dynamic Calculations:** Reads structured data starting from row 6 and aggregates matching rows in real time.
* **Instant Feedback:** Displays formatted total metrics directly in cell `F2`.

---

## 🚀 Getting Started

### 1. Prerequisites
* A Google Account with access to [Google Sheets](https://sheets.google.com).
* A Google AI Studio API Key (Get one at [Google AI Studio](https://aistudio.google.com/)).

### 2. Installation & Setup
1. Open your Google Sheet dataset.
2. Ensure your headers are placed on **Row 6** (e.g., `Customer Name`, `State`, `Category`, `Sales`, `Profit`).
3. Click on **Extensions > Apps Script**.
4. Paste the provided script into `Code.gs`.
5. Replace `API_KEY` with your actual Gemini API key.

### 3. Setting Up the Installable Trigger
Because the script calls an external API, a simple `onEdit` trigger won't suffice:
1. In Apps Script, click on the **Triggers** icon (clock on the left menu).
2. Click **+ Add Trigger** (bottom right).
3. Select `onEdit` as the function to run.
4. Set event source to **From spreadsheet**.
5. Set event type to **On edit**.
6. Save and authorize permissions.

### Sample Data
You can download the sample dataset used in this project here: [sales_data.csv](./sales_data.csv)

## 🛠️ How It Works

1. **Cell Monitor:** Modifying cell `B2` triggers the script.
2. **AI Parameter Extraction:** Gemini 2.5 Flash receives the query and returns a raw JSON payload containing the detected filters and target metric.
3. **Array Search:** Apps Script loops through the dataset starting at row 7, filters rows matching the extracted criteria, and sums the specified metric column.
4. **Output:** The formatted result is written directly to cell `F2`.

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
