To build a truly robust agency-wide calendar, you need to look beyond just "seeing dates." For a BTL agency, the calendar is the **source of truth** that connects the financial side (budgets) with the operational side (field staff).

Here are the critical requirements and technical options for your "One Platform" calendar setup.

---

## 1. Core Calendar Requirements for BTL

A standard calendar (like Google) is a "flat" visualization. For your agency, you need a **multi-dimensional** calendar that handles the following:

- **Conflict Detection:** If a promoter is assigned to a mall in Moscow from 10:00–18:00, the system must "red-flag" any attempt to assign them to another activation simultaneously.
- **Capacity Planning:** The ability to see if you have enough staff for "Activation Wave A" (100 people) and "Activation Wave B" (50 people) running on the same weekend.
- **Geographical Grouping:** Viewing the calendar by city or region. You shouldn't have to scroll through 200 events to find the 5 happening in Kazan.
- **Budget Overlay (Admin Only):** A toggle that shows the "Cost vs. Revenue" for each day directly on the calendar bar.

---

## 2. Technical Implementation Options

If you move forward with **ERPNext (Frappe)** or a **Custom Go-based Solution**, you have three main ways to render this calendar:

### **A. The Frappe "Calendar View" (Easiest)**

In ERPNext, every DocType can have a `calendar_view.js` file.

- **How it works:** You map the fields (e.g., `start_date`, `end_date`, `subject`).
- **BTL Advantage:** You can use "Color Mapping" based on status. (e.g., Green = Staffed, Red = Understaffed, Grey = Completed).
- **Limitation:** It is a traditional grid. It can get "crowded" if you have 50+ events in one day.

### **B. The "Gantt" or "Timeline" View (Best for Scale)**

For an agency, a horizontal timeline (Gantt) is often better than a square calendar grid.

- **Requirement:** Your tech must support **Dynamic Loading**. As you scroll through months, it only fetches data for those months to stay fast.
- **Technology:** **Frappe Gantt** (an open-source library used by ERPNext) or **dhtmlxGantt** (if building a custom Go/JS app).

### **C. The "Map-Calendar" Hybrid**

Since BTL is location-based, the ultimate tool is a map that responds to a date slider.

- **Requirement:** Integration with **Mapbox** or **Leaflet.js**.
- **Use Case:** You move a slider to "Saturday," and the map shows pins for all 20 malls where promotions are live. Clicking a pin shows the staff assigned and their check-in status.

---

## 3. The "Budget Sync" Logic

To link the calendar to your budget without exposing it to everyone, you need a **Relational Schema**:

1. **Project Table:** Contains the "Master Budget" (Hidden from staff).
2. **Activation Table:** Contains the dates and staff (Visible to staff).
3. **Cost Table:** A "Child Table" that calculates `Hours worked * Hourly Rate`.

**Technical Implementation:**
In **ERPNext**, you use a **Virtual Field** or a **Server Script**. When a manager looks at the calendar, the script sums up the `Cost Table` in the background and displays a "Margin %" on the event tooltip. For a promoter, the script returns `null` for that field, so the UI simply shows an empty space or a "N/A."

---

## 4. Technology Comparison for Calendar Features

| Feature                    | **Google Calendar API**    | **Frappe/ERPNext**       | **PocketBase + FullCalendar** |
| -------------------------- | -------------------------- | ------------------------ | ----------------------------- |
| **Custom Fields**          | 🔴 Limited (metadata only) | 🟢 Infinite (native)     | 🟢 Infinite                   |
| **RBAC (Permissions)**     | 🔴 All-or-nothing          | 🟢 Field-level control   | 🟡 Role-based (custom logic)  |
| **Scaling (1000+ events)** | 🟢 High                    | 🟡 Medium (needs tuning) | 🟢 High                       |
| **BTL Specifics**          | 🔴 None                    | 🟢 Built-in Project Mgmt | ⚪ Build from scratch         |

---

### **Recommended Technical Stack for your Agency:**

- **Platform:** ERPNext (Frappe).
- **UI Library:** **FullCalendar.io** (integrated into Frappe). It is the industry standard for web calendars and handles drag-and-drop, time-zones, and event clicking perfectly.
- **Data Sync:** **Redis** for caching the calendar data so that the "Big Picture" view for the agency owner loads in under 1 second, even with 5,000 yearly events.

**Would you like me to create a "Developer Handover" document that specifies exactly how to configure the FullCalendar component within ERPNext to handle your BTL filters (City, Brand, Staffing Status)?**

---

### Brief 2

This summary is designed to serve as a **"System Context"** or **"Project Brief"** for future AI agents or developers tasked with setting up your agency's infrastructure.

---

## 🏗️ Project Brief: BTL Agency Management System (2026)

### **Core Objective**

To establish a unified management platform for a **Promotional (BTL) Agency** that provides a "Big Picture" view of all activations while strictly enforcing data privacy (specifically hiding budgets and margins from field staff/coordinators).

---

### **1. Primary Platform: ERPNext (on Frappe Framework)**

The conversation concluded that **ERPNext** is the superior choice over SaaS (Monday/Asana) or simple calendars due to its **granular permission levels** and open-source nature.

- **Architecture:** Metadata-driven. Uses **DocTypes** to define data structures, UI forms, and permissions simultaneously.
- **Permissions:** Utilizes **Role-Based Access Control (RBAC)** and **Field Masking** to show tasks/schedules to field staff while hiding sensitive financial columns.
- **Localization:** Fully supports **Russian UI**, with the ability to override standard terms (e.g., "Sales Order" $\rightarrow$ "Project Activation") via the Translation module.

---

### **2. Workflow & Field Ops: The Telegram Integration**

To manage a high-turnover field workforce without requiring app installs, the system will use **Telegram as the primary "Field Interface."**

- **Geofencing (Check-in):** \* **Logic:** Promoters send their "Live Location" or "Static Location" via Telegram.
- **Verification:** The system compares the incoming coordinates $(\text{actual\_lat}, \text{actual\_lng})$ against the stored "Trade Point" coordinates using the **Haversine Formula**.
- **Automation:** If the distance is within the defined radius (e.g., 100m), the agent automatically logs a "Check-in" in ERPNext.

- **Web Forms:** Use ERPNext Web Forms embedded in Telegram for high-fidelity reporting (photos of stands, inventory counts).
- **Calendar:** Individual schedules are pushed to staff via `/my_schedule` commands.

---

### **3. Data Structure (DocTypes to Build)**

The following custom fields and structures were identified as essential:

| Entity                 | Critical Fields                                                                      |
| ---------------------- | ------------------------------------------------------------------------------------ |
| **Trade Point**        | `Latitude`, `Longitude`, `Radius (meters)`, `Map Location`                           |
| **Project Activation** | `Client`, `Budget` (Hidden for Staff), `Contractor`, `Start/End Date`                |
| **Check-in Log**       | `Employee Link`, `Actual Lat/Lng`, `Distance Offset`, `Status (In Zone/Out of Zone)` |

---

### **4. Alternatives Evaluated**

- **Basecamp/HEY Calendar:** Rejected for high-volume BTL due to lack of task dependencies, resource allocation, and field-staffing features.
- **[Monday.com/ClickUp](https://www.google.com/search?q=https://Monday.com/ClickUp):** Strong SaaS contenders, but rejected based on the high cost of 50+ licenses and less granular "field-level" privacy control compared to ERPNext.
- **PocketBase (Golang):** Identified as the fastest modern alternative for building a custom portal from scratch, though it lacks ERPNext's ready-made "Business Logic" (HR/Accounting).

---

### **5. Next Implementation Steps for AI Agents**

1. **Deployment:** Deploy ERPNext v16 using a **Docker Compose** stack (MariaDB, Redis, Frappe-Bench).
2. **Schema Design:** Define the `Trade Point` and `Check-in Log` DocTypes.
3. **Telegram Bot Logic:** Write a Python-based Telegram bot listener using `python-telegram-bot` or the Frappe-native API to handle location pings.
4. **Security Policy:** Configure **Permission Levels** (Level 0 for general data, Level 1 for Financials) and assign Level 1 only to the `Account Manager` role.

---

**Would you like me to generate the actual Docker Compose file or the Python server script for the Haversine distance calculation to get the technical setup started?**

---

### Geo and details

Для реализации системы контроля геопозиции (Geofencing) в BTL-агентстве вам потребуется создать или дополнить два типа документов (DocTypes) в ERPNext: **«Торговая точка»** (куда приходят) и **«Лог посещений»** (кто и когда пришел).

Ниже список полей, которые необходимо добавить, чтобы Telegram-бот мог проводить сверку.

### 1. Документ: Торговая точка (Trade Point)

Здесь мы храним «эталонные» координаты. Вы можете добавить эти поля в стандартный документ `Address` или создать новый DocType `Trade Point`.

| Поле (Label)          | Название (Name) | Тип (Field Type) | Зачем нужно                                          |
| --------------------- | --------------- | ---------------- | ---------------------------------------------------- |
| **Название точки**    | `point_name`    | Data             | Имя ТЦ или магазина.                                 |
| **Широта (центр)**    | `latitude`      | Float            | Для математического расчета дистанции.               |
| **Долгота (центр)**   | `longitude`     | Float            | Для математического расчета дистанции.               |
| **Радиус забора (м)** | `radius`        | Int              | Допустимая погрешность (обычно 50–150 м).            |
| **Карта**             | `map_location`  | **Geolocation**  | Чтобы вы видели точку на карте в интерфейсе ERPNext. |

---

### 2. Документ: Отметка прихода (Check-in Log)

Этот документ будет автоматически создавать ваш Telegram-бот, когда промоутер присылает геопозицию.

| Поле (Label)       | Название (Name) | Тип (Field Type) | Зачем нужно                              |
| ------------------ | --------------- | ---------------- | ---------------------------------------- |
| **Промоутер**      | `employee`      | Link (Employee)  | Привязка к конкретному человеку.         |
| **Акция/Проект**   | `project`       | Link (Project)   | К какому проекту относится выход.        |
| **Широта (факт)**  | `actual_lat`    | Float            | Координаты, которые прислал бот.         |
| **Долгота (факт)** | `actual_lng`    | Float            | Координаты, которые прислал бот.         |
| **Дистанция**      | `distance`      | Float            | Рассчитанное отклонение от центра точки. |
| **Статус**         | `status`        | Select           | «В зоне» или «Вне зоны».                 |

---

### Как это работает технически (Logic)

Когда промоутер отправляет локацию в Telegram:

1. Бот берет его `actual_lat` и `actual_lng`.
2. Находит в ERPNext координаты точки (`latitude`, `longitude`), к которой прикреплен промоутер сегодня.
3. Вычисляет расстояние $D$ по формуле гаверсинуса (Haversine):

$$D = 2R \cdot \arcsin\left(\sqrt{\sin^2\left(\frac{\Delta \phi}{2}\right) + \cos \phi_1 \cos \phi_2 \sin^2\left(\frac{\Delta \lambda}{2}\right)}\right)$$

_(где $R$ — радиус Земли, $\phi$ — широта, $\lambda$ — долгота)._ 4. Если $D \leq$ `radius`, система ставит статус «В зоне» и подтверждает начало смены.

### Важное про доступы (ERPNext v16)

В версии 2026 года (v16) вы можете использовать функцию **Field Masking** (Маскирование полей).

- **Для координаторов:** Поле `Budget` в проекте будет видно.
- **Для промоутеров/супервайзеров:** В том же самом документе поле `Budget` будет скрыто или заменено на звездочки `***`, даже если они смотрят этот проект через бота.

**Хотите, чтобы я подготовил Python-скрипт (Server Script), который будет автоматически рассчитывать это расстояние прямо внутри ERPNext?**
