# ✈️ Kayak Flight Scraper

This is a web-based flight scraping tool that gathers the cheapest round-trip or multi-destination flights from [Kayak](https://www.kayak.com) (USA and Canada domains). Built using Flask, Selenium, and Undetected ChromeDriver, it offers a user-friendly interface for travel agencies or individuals to automate flight data collection.

---

## 🌐 Features

- 🔐 **OTP-secured Login** (via email)
- 🇺🇸🇨🇦 Supports flight searches for **USA** and **Canada**
- 🔁 **Return** and **Multi-Destination** flight modes
- 📅 Select date ranges and stay durations
- 🧠 Scrapes using multiple threads with human-like behavior to bypass bot detection
- 📦 Generates downloadable **Excel (.xlsx)** results
- 🛑 Option to **force-stop scraping** and get partial results

---

## 🛠️ Tech Stack

- **Backend**: Flask
- **Frontend**: HTML, CSS, Vanilla JS
- **Automation**: Selenium with undetected-chromedriver
- **Data Handling**: Pandas, OpenPyXL
- **Email OTP**: smtplib + Gmail

---

## 🔧 Installation

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/kayak-flight-scraper.git
cd kayak-flight-scraper
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

> Note: Chrome browser and [ChromeDriver](https://sites.google.com/a/chromium.org/chromedriver/) are required.

### 3. Configure Gmail (OTP)

Allow **"Less secure app access"** or generate an **App Password** for the Gmail account used in `app.py` under `send_otp_email`.

---

## 🚀 Running the App

```bash
python app.py
```

Visit: `http://localhost:5000`

---

## 📁 Project Structure

```bash
├── app.py                 # Main Flask app with scraping logic
├── requirements.txt       # Python dependencies
├── templates/
│   ├── index.html         # Flight search form
│   ├── login.html         # OTP login screen
│   ├── results.html       # Display and download results
│   └── loading.html       # Loading overlay
├── static/
│   ├── Orbis Logo.png     # Logo image
│   └── loading_animation.gif # Loading animation
└── README.md              # Project documentation
```

---

## 📌 Notes

- The scraper uses threading to accelerate scraping across multiple dates.
- If CAPTCHA blocks occur, the tool attempts automated recovery and retry.
- Uses a local Chrome extension (`buster`) to assist in CAPTCHA solving. You must update `buster_extension_path` in `setup_driver()` to your machine’s location.
- Uses US and Canadian airports hardcoded into the interface.

---

## 🔐 Security

- OTP is emailed before accessing the search interface.
- OTPs are stored temporarily in memory and cleared post-verification.

---

## 📤 Output

Excel files are saved locally and served for download. Each includes:

- Date
- Departure & Arrival Airports
- Airline
- Price
- Departure & Arrival Times
- Duration of Stay
