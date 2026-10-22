# PulseGuard

**Predictive maintenance for EV charging networks.**

PulseGuard tells a charging operator which charger is about to break, roughly when, and which part is failing, so it can be fixed at night before a driver arrives to a dead charger. It turns 3–7 days of break-fix downtime into a 30-minute planned repair.

This repository is the working prototype of an MBA venture by **Harmonic Tribe**, Alliance School of Business, Alliance University.

> **Live demo:** `https://<your-github-username>.github.io/pulseguard/` (after enabling GitHub Pages, see below)

---

## The problem

- India has **52,718** public charging stations (Government data in Parliament, July 2026).
- Audits found **nearly half** of public chargers non-functional at some point (Business Standard, Feb 2024), and about **84%** of a Delhi sample not working (IEEFA).
- Chargers are fixed only after they fail, so each failure costs **3–7 days** of lost charging, emergency repair bills and driver trust.

**Root cause:** chargers already record the warning signs (temperature, fan speed, cable resistance, OCPP fault codes), but nobody reads that data, and nobody is paid for uptime.

## How PulseGuard works (DIKW)

| Stage | Question | What PulseGuard does |
| --- | --- | --- |
| **Data** | What do we observe? | Reads charger telemetry over OCPP 1.6J / 2.0.1, or a ₹8,000 sensor kit for older units |
| **Information** | What is happening? | Health score and trend for every charger and site |
| **Knowledge** | What does it mean? | Predicts which part will fail, about 48 hours ahead |
| **Wisdom** | What should we do? | Books a technician into an off-peak slot with the right spare part |

## What's in the prototype

**Marketing site:** product, problem statistics with sources, comparison with alternatives, ROI calculator, pricing, 30-day pilot program, pilot application form, FAQ.

**Sign-up and onboarding:** three steps covering company, charging network (city, sites, chargers, brands) and plan.

**Operator console:**

| Screen | Purpose |
| --- | --- |
| Overview | Live availability, 30-day uptime vs. 98% SLA, predicted failures, savings, live activity |
| Chargers | Searchable fleet table, live health; click a charger for telemetry charts and dispatch |
| Alerts | Predictions without a work order; acknowledge or dispatch |
| Work orders | Kanban board: Scheduled → En route → In progress → Resolved |
| Dispatch | Technician roster, tonight's schedule, spare parts |
| Sites | Health map per site |
| Reports | Before/after uptime, SLA by site, faults by component, CSV export |
| Billing | Plan, pilot countdown, upcoming invoices with GST |
| Settings | Company, notifications, charger integrations (OCPP, sensor kit, CMS partner) |

## Business model

| Plan | Price (per DC gun / month) | Includes |
| --- | --- | --- |
| Monitor | ₹900 | Predictions and dashboard; customer's own technicians repair |
| Protect | ₹4,500 | Monitor + quarterly visits, priority repair by our technicians, spares at cost |
| Uptime Guarantee | ₹6,500 | Protect + 98% uptime SLA with fee refund if missed |

Every plan starts with a **free 30-day pilot**. Pricing is value-based: on a typical 60 kW charger, break-fix costs about ₹1,48,800 a year; with Protect the total falls to about ₹1,09,760 including our fee, roughly **₹1.7 back for every ₹1** paid.

## Run it

No build step and no dependencies.

- **Locally:** download the repo and open `index.html` in a browser.
- **GitHub Pages:** Settings → Pages → Source: *Deploy from a branch* → Branch: `main`, folder `/ (root)` → Save. The site goes live at `https://<username>.github.io/<repo-name>/` within a minute or two.

Click **View live demo** to explore a sample fleet, or **Get started** to create your own workspace.

## Prototype limitations

- Charger telemetry, technicians, spare-parts stock and 30-day history are **simulated sample data**.
- In this standalone version, workspaces, work orders and pilot applications are saved in **your browser only** (localStorage).
- Not yet connected to real chargers: the next engineering step is an OCPP backend and a prediction model trained on real repair history.
- Prices, uptime and savings figures are planning estimates from our project report, to be validated in pilots.

## Tech

Single-file HTML, CSS and vanilla JavaScript. Charts are hand-drawn SVG. Fonts: Geist and Geist Mono (Google Fonts). Works in light and dark mode and on phones.
