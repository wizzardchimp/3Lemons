# 3Lemons — Daily Takings

New takings app (separate from BL) with:

- **Editable sites** (add / rename / remove) stored on Google Sheet **Rates** tab  
- **Per-category float** (Reels / Digital; never pool) with **carry-forward** when float &gt; gross  
- MGD (20%), supplier share, cash left calculated on **net** (gross − float taken)  
- History, monthly summary, last-21-days totals  
- Password gate (default: `robin`)

## Live

After Pages is enabled: `https://wizzardchimp.github.io/3Lemons/`

## Setup

### 1. Google Sheet
Create a spreadsheet with tabs (or let the script create them):
- **Data** — Date | Timestamp | JSON  
- **Rates** — ConfigJSON  
- **LoginLog** — optional  

### 2. Apps Script
1. Extensions → Apps Script  
2. Paste `Code.gs`  
3. Deploy → New deployment → Web app  
   - Execute as: Me  
   - Who has access: Anyone  
4. Copy the `/exec` URL  

### 3. App Settings
1. Open the site → log in (`3l26`)  
2. Settings → paste API URL → Save  
3. Add sites / categories / float amounts → **Save to Sheet**  

## Float rules
- `toRecover = floatRequired + floatOwed (carry-in)`  
- `floatTaken = min(gross, toRecover)`  
- `net = gross − floatTaken`  
- MGD / rate splits on **net** only  
- `floatOwedAfter` carries to the next collection for that **location + category**  
- Pool: no float (rent or 50/50 as configured)  

## Password
Change `APP_PASSWORD` in `index.html` if needed.
