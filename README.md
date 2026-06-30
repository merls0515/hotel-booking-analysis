# 🏨 Hotel Booking Performance Analysis
### TravClan Assignment | Business Intelligence Report 

[![Python](https://img.shields.io/badge/Python-3.9+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-2.0+-130654?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-3.7+-11557c?style=for-the-badge&logo=python&logoColor=white)](https://matplotlib.org/)
[![Seaborn](https://img.shields.io/badge/Seaborn-0.12+-4c8cbf?style=for-the-badge&logo=python&logoColor=white)](https://seaborn.pydata.org/)
[![Google Colab](https://img.shields.io/badge/Google%20Colab-Notebook-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white)](https://colab.research.google.com/)

---

## 📌 Project Overview

This project analyzes **30,000 hotel booking transactions** from an online travel platform specializing in hotel reservations. The goal is to identify cancellation drivers, booking patterns across channels/room types/star ratings, and provide data-backed business recommendations to reduce revenue loss.

> ### 🚨 Key Business Problem
> The platform loses **$146.8 million annually** due to a **20.23% cancellation rate**.  
> This analysis identifies root causes and recommends actionable strategies to recover revenue.

---

## 📊 Dataset Description

| Attribute | Details |
|-----------|---------|
| **Source** | `Hotel_bookings_final.csv` |
| **Records** | 30,000 bookings |
| **Time Period** | Full Year (January – December 2024) |
| **Features** | 24 columns |

<details>
<summary><b>📋 View Key Columns</b></summary>

<br>

| Column Name | Description |
|-------------|-------------|
| `customer_id` | Unique customer identifier |
| `property_id` | Unique hotel property identifier |
| `city` | Hotel location |
| `star_rating` | Hotel star rating (1–5) |
| `booking_date` | Date booking was made |
| `check_in_date` | Scheduled check-in date |
| `check_out_date` | Scheduled check-out date |
| `room_type` | Standard / Deluxe / Suite |
| `booking_channel` | Web / Mobile App / Travel Agent |
| `booking_value` | Total booking value ($) |
| `selling_price` | Final selling price ($) |
| `costprice` | Cost to platform ($) |
| `markup` | Profit margin ($) |
| `booking_status` | Completed / Cancelled |
| `payment_method` | PayPal / Credit Card / Debit Card / Bank Transfer |
| `refund_status` | Yes / No |
| `cashback` | Cashback amount ($) |
| `coupon_redeem` | Coupon discount amount ($) |

</details>

---

## 🔧 Features Engineered

| Feature | Description | Formula |
|---------|-------------|---------|
| `stay_length` | Duration of stay (days) | `check_out_date - check_in_date` |
| `lead_time` | Booking window (days) | `check_in_date - booking_date` |
| `is_cancelled` | Cancellation flag | `1 if Cancelled else 0` |
| `revenue_lost` | Revenue lost to cancellations | `booking_value if cancelled else 0` |
| `profit_margin` | Profit percentage | `(selling_price - costprice) / selling_price × 100` |
| `booking_month` | Month number | `booking_date.month` |
| `booking_month_name` | Month name | `booking_date.month_name()` |

---

## 📈 Key Findings

### 1. Overall Metrics

| Metric | Value |
|--------|-------|
| Total Bookings | 30,000 |
| Overall Cancellation Rate | **20.23%** |
| Total Revenue Lost | **$146,834,853** |
| Average Stay Length | 4 days |
| Average Lead Time | 30 days |
| Average Profit Margin | 23.6% |

### 2. Cancellation Drivers (Meaningful Only)

| Segment | ✅ Best Performer | ❌ Worst Performer | Gap |
|---------|------------------|-------------------|-----|
| **Booking Channel** | Web — 17.6% cancel | Travel Agent — 27.9% cancel | **10.3%** |
| **Room Type** | Deluxe — 16.0% cancel | Standard — 23.3% cancel | **7.3%** |
| **Seasonality** | April — 16.3% cancel | July — 30.3% cancel | **14.0%** |
| **Star Rating** | 4-star — 20.0% cancel | 5-star — 21.3% cancel | 1.3% |

### 3. What Does NOT Drive Cancellations

| Factor | Difference | Verdict |
|--------|-----------|---------|
| Lead Time | -0.2 days | ❌ Not a driver |
| Stay Length | 0 days | ❌ Not a driver |
| Payment Method | <1% variation | ❌ Not a driver |
| Coupon Usage | +0.7% | ❌ Not a driver |
| Cashback | +0.8% | ❌ Not a driver |

---

## 📊 Visualizations Generated

| Chart | Description |
|-------|-------------|
| `cancellation_analysis_charts.png` | Cancellation rates by channel, room type, payment method, coupon, cashback |
| `revenue_analysis.png` | Revenue distribution by channel, room type, star rating |
| `monthly_trend.png` | Monthly cancellation rate trend with baseline |

---

## 💡 Business Recommendations

<details open>
<summary><b>Recommendation 1 — Travel Agent Channel</b></summary>

| Current | Target | Potential Recovery |
|---------|--------|--------------------|
| 27.9% cancellation | 18.0% (Web rate) | **$8.78M** |

**Actions:**
- Introduce partial pre-payment requirements for Travel Agent bookings
- Tie commission structures to cancellation rate thresholds
- Require guest confirmation within 48 hours of booking

</details>

<details open>
<summary><b>Recommendation 2 — Standard Rooms</b></summary>

| Current | Target | Potential Recovery |
|---------|--------|--------------------|
| 23.3% cancellation | 16.0% (Deluxe rate) | **$34.27M** |

**Actions:**
- Offer paid upgrades from Standard to Deluxe at booking
- Bundle non-refundable add-ons (breakfast, parking)
- Require small deposit for peak season bookings

</details>

<details open>
<summary><b>Recommendation 3 — Peak Season (July)</b></summary>

| Current | Target | Potential Recovery |
|---------|--------|--------------------|
| 30.3% cancellation | 16.3% (April rate) | **$5.70M** |

**Actions:**
- Require higher pre-payment for July bookings
- Offer early-bird discounts (60+ days advance)
- Reduce Travel Agent inventory allocation during peak months

</details>

<details open>
<summary><b>Recommendation 4 — Channel Mix Optimization</b></summary>

- Increase Web channel allocation during peak months
- Create Web-exclusive rates (Web has 17.6% cancellation)
- Mobile App push notifications 72 hours before check-in

</details>

---

## 💰 Financial Impact

| Scenario | Potential Recovery |
|----------|--------------------|
| Travel Agent → Web rate | $8,781,933 |
| Standard → Deluxe rate | $34,269,953 |
| July → April rate | $5,699,459 |
| **Total Theoretical Recovery** | **$48,751,345** |

> ⚠️ *Represents theoretical maximum. Realistic first-year target: 20–30% ($10–15M)*

---

## 🎯 Recommendations Priority Matrix

| Priority | Recommendation | Effort | Impact |
|----------|---------------|--------|--------|
| 🔴 High | Travel Agent pre-payment requirement | Low | High |
| 🔴 High | Reduce Agent inventory in peak months | Medium | High |
| 🟡 Medium | Standard → Deluxe upgrade offers | Low | Medium |
| 🟡 Medium | Peak season pre-payment increase | Medium | Medium |
| 🟢 Low | Tiered cancellation for 5-star properties | High | Low |

---

## 📁 Repository Structure
hotel-booking-analysis/
│
├── 📓 Hotel_Booking_Analysis.ipynb     # Google Colab notebook with full code
├── 📂 data/
│   └── Hotel_bookings_final.csv        # Dataset (not included - add your own)
├── 📂 visualizations/
│   ├── cancellation_analysis_charts.png
│   ├── revenue_analysis.png
│   └── monthly_trend.png
├── 📂 report/
│   └── Hotel_Booking_Analysis_Report.pdf
├── 📄 README.md                        # This file
└── 📄 requirements.txt                 # Python dependencies

---

## 🚀 How to Run

### Option 1: Google Colab *(Recommended)*

1. Open [Google Colab](https://colab.research.google.com/)
2. Upload `Hotel_Booking_Analysis.ipynb`
3. Upload `Hotel_bookings_final.csv` to the Colab environment
4. Run cells sequentially

### Option 2: Local Jupyter Notebook

```bash
# Clone repository
git clone https://github.com/merls0515/hotel-booking-analysis.git
cd hotel-booking-analysis

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter
jupyter notebook Hotel_Booking_Analysis.ipynb
```

---

## 🛠️ Technologies Used

| Tool | Purpose |
|------|---------|
| Python 3.9+ | Core programming language |
| Pandas | Data manipulation & analysis |
| NumPy | Numerical computations |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualizations |
| Google Colab | Development environment |

### `requirements.txt`
pandas==2.0.3
numpy==1.24.3
matplotlib==3.7.1
seaborn==0.12.2

---

## 📝 Key Insights Summary

1. 💸 **$146.8M lost annually** to cancellations
2. 📉 **Travel Agent** channel has 10% higher cancellation than Web
3. 🛏️ **Standard rooms** cancel 7% more than Deluxe
4. 📅 **July** has 14% higher cancellation than April
5. 🌐 **Web channel** generates highest revenue ($444M) with lowest cancellation (17.6%)
6. ✅ Lead time, stay length, and payment method have **no meaningful impact** on cancellations

---

## 👤 Author

**Merlyn Victor**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/merlyn-victor-15391b2a6)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/merls0515)
[![Email](https://img.shields.io/badge/Email-Contact-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:merlyntvictor@gmail.com)

---

## 📧 Submission

> This project was submitted to **TravClan** as part of an assignment.
