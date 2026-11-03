<div align="center">

# -- ! Students Performance Dashboard ! --
### *Interactive Power BI Report for Academic, Attendance & Behavior Analysis*

[![Power BI](https://img.shields.io/badge/Power%20BI-Desktop-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-Measures%20%26%20Logic-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)](https://dax.guide/)
[![Power Query](https://img.shields.io/badge/Power%20Query-ETL%20%2F%20M%20Language-217346?style=for-the-badge&logo=microsoftexcel&logoColor=white)](https://learn.microsoft.com/power-query/)
[![Data Model](https://img.shields.io/badge/Data%20Model-Star%20Schema-9C27B0?style=for-the-badge&logo=databricks&logoColor=white)](https://learn.microsoft.com/power-bi/guidance/star-schema)

<br/>

> *"Data tells the story of every student — a good dashboard simply makes it easy to read."*

</div>

---

## 📋 Table of Contents

- [📌 Overview](#-overview)
- [🎯 Problem Statement](#-problem-statement)
- [✨ Key Features](#-key-features)
- [🏗️ Project Structure](#️-project-structure)
- [🔄 Project Workflow](#-project-workflow)
- [🗃️ Part A — Data Model](#️-part-a--data-model)
- [📊 Part B — Dashboard & DAX Measures](#-part-b--dashboard--dax-measures)
- [🛠️ Tech Stack](#️-tech-stack)
- [📈 Results & Insights](#-results--insights)
- [🏆 Advantages](#-advantages)
- [🚀 How to Use](#-how-to-use)
- [📄 License](#-license)
- [👤 Author](#-author)
- [🙏 Acknowledgements](#-acknowledgements)

---

## 📌 Overview

The **Students Performance Dashboard** is a single-page, interactive **Power BI** report that brings together student demographics, exam scores, daily attendance, and behavior records into one view. Using **Power Query** for data loading, a **relational data model** for connecting tables, and **DAX measures** for calculations, it lets teachers and administrators explore performance by class, section, subject, and term with just a few clicks.

This project is designed to:
- Practice the full Power BI workflow: **Load → Transform → Model → Visualize**
- Build a clean **star-style data model** using one dimension table and three fact tables
- Write reusable **DAX measures** for KPIs such as attendance rate and score percentage
- Design a dashboard with **KPI cards, slicers, charts, and a detail table**

---

## 🎯 Problem Statement

> **Objective:** Build an interactive dashboard to monitor and analyze student academic performance, attendance, and behavior across classes and subjects.

Schools collect large volumes of data — marks, attendance sheets, and behavior notes — but these usually sit in separate files, making it hard to answer simple questions like *"How is Class 7 doing in Math this term?"* or *"What is the overall attendance rate?"*. This dashboard connects all of that data and answers such questions instantly.

| 📂 Dataset | 📄 Type | 🔍 Description |
|------------|---------|----------------|
| `Students.csv` | Dimension | Student ID, name, gender, class, and section |
| `Scores.csv` | Fact | Subject-wise marks for every exam type and term |
| `Attendance.csv` | Fact | Daily Present / Absent records with absence reason |
| `Behavior.csv` | Fact | Behavior type and teacher notes with date |

The goal is to demonstrate **end-to-end Business Intelligence skills** — from raw CSV files to an interactive, decision-ready report.

---

## ✨ Key Features

| Feature | Description |
|--------|-------------|
| 🧮 **3 KPI Cards** | Total Students, Attendance %, and Average Score at a glance |
| 🎛️ **3 Slicers** | Filter the entire page by **Section**, **Class**, and **Subject** |
| 📅 **Term Selector** | Table listing Term 1 / Term 2 / Term 3 for quick reference |
| 📈 **Trend Line Chart** | Score percentage (`%score`) across terms |
| 📊 **Clustered Column Chart** | Average score by subject, split by class |
| 📋 **Student Detail Table** | Name, Subject, and `%score` for drill-down analysis |
| 🔗 **Cross-Filtering** | Every visual reacts to slicer selections and to clicks on other visuals |
| 🎨 **Custom Layout** | 1920 × 1080 canvas with a lavender sidebar and header band (`#9F93CE`) on the Fluent 2 theme |

---

## 🏗️ Project Structure

```
📦 students-performance-dashboard/
│
├── 📊 STUDENTS_PERFORMANCE_DASHBOARD.pbix   ← Main Power BI report (entry point)
│
├── 📂 data/
│   ├── 📄 Students.csv                      ← 1,000 students
│   ├── 📄 Scores.csv                        ← 30,000 score records
│   ├── 📄 Attendance.csv                    ← 100,000 attendance records
│   └── 📄 Behavior.csv                      ← 6,500 behavior records
│
└── 📄 README.md                             ← Project documentation
```

> 📝 *The `.pbix` file loads the CSVs from a local path (`D:\POWER BI\student performance dashboard\`). If you move the files, update the data source path — see [How to Use](#-how-to-use).*

---

## 🔄 Project Workflow

```
Raw CSV Files (Students, Scores, Attendance, Behavior)
      │
      ▼
┌─────────────────────────────┐
│   Power Query (Transform)   │  ← Promote headers, set data types,
│                             │    replace blank Reason with "N/A"
└────────────┬────────────────┘
             │
             ▼
┌─────────────────────────────┐
│   Data Model (Relationships)│  ← 3 × Many-to-One links on StudentID
└────────────┬────────────────┘
             │
             ▼
┌─────────────────────────────┐
│   DAX Measures              │  ← %score, Attendance %, Avg Score,
│                             │    Total students, Behavior count
└────────────┬────────────────┘
             │
     ┌───────┴────────┐
     ▼                ▼
┌─────────────┐   ┌──────────────────┐
│  Slicers    │   │  Visuals         │
│ Section     │   │ Cards / Charts / │
│ Class       │   │ Tables           │
│ Subject     │   │                  │
└──────┬──────┘   └────────┬─────────┘
       │                   │
       └─────────┬─────────┘
                 ▼
     Interactive "Academic dashboard"
```

---

## 🗃️ Part A — Data Model

### 📝 1. Tables & Columns

| Table | Role | Columns | Rows |
|-------|------|---------|------|
| 🧑‍🎓 **Students** | Dimension | `StudentID`, `Name`, `Gender`, `Class`, `Section` | 1,000 |
| 📝 **Scores** | Fact | `StudentID`, `Subject`, `ExamType`, `Score`, `MaxScore`, `Term` | 30,000 |
| 🗓️ **Attendance** | Fact | `StudentID`, `Date`, `Status`, `Reason` | 100,000 |
| 🚦 **Behavior** | Fact | `StudentID`, `Date`, `BehaviorType`, `Notes` | 6,500 |

---

### 🔗 2. Relationships

All three fact tables connect to **Students** through `StudentID` (Many-to-One, single-direction filter), so any filter on Class or Section flows down to scores, attendance, and behavior.

```
                    ┌──────────────┐
                    │   Students   │  (1)
                    │  StudentID   │
                    └──────┬───────┘
          ┌────────────────┼────────────────┐
          │ (*)            │ (*)            │ (*)
   ┌──────▼──────┐  ┌──────▼──────┐  ┌──────▼──────┐
   │   Scores    │  │ Attendance  │  │  Behavior   │
   └─────────────┘  └─────────────┘  └─────────────┘
```

---

### 🧹 3. Power Query Transformations

| Step | Applied To | Purpose |
|------|-----------|---------|
| **Promote Headers** | All tables | Use first CSV row as column names |
| **Change Type** | All tables | Text for IDs/names, Date for dates, Whole Number for `Score`, `MaxScore`, `Class` |
| **Replace Value** | `Attendance[Reason]` | Replace blank reasons with `"N/A"` |

**Sample M code (Attendance):**
```
let
  Source = Csv.Document(File.Contents("...\Attendance.csv"), [Delimiter = ",", Columns = 4]),
  #"Promoted headers" = Table.PromoteHeaders(Source, [PromoteAllScalars = true]),
  #"Changed column type" = Table.TransformColumnTypes(#"Promoted headers",
      {{"StudentID", type text}, {"Date", type date}, {"Status", type text}, {"Reason", type text}}),
  #"Replaced value" = Table.ReplaceValue(#"Changed column type", "", "N/A", Replacer.ReplaceValue, {"Reason"})
in
  #"Replaced value"
```

---

## 📊 Part B — Dashboard & DAX Measures

### 🗺️ 4. Dashboard Layout — "Academic dashboard"

| Zone | Visual | Fields Used | Purpose |
|------|--------|-------------|---------|
| 🔝 **Header band** | Shape | — | Title area (lavender) |
| ◀️ **Left sidebar** | Shape | — | Navigation / branding area |
| 🎛️ **Filter row** | Slicer | `Students[Section]` | Filter by section (A / B / C) |
| 🎛️ **Filter row** | Slicer | `Students[Class]` | Filter by class (range slider, 1–12) |
| 🎛️ **Filter row** | Slicer | `Scores[Subject]` | Filter by subject |
| 📅 **Filter row** | Table | `Scores[Term]` | Lists Term 1, Term 2, Term 3 |
| 🔢 **KPI row** | Card | `Total students` | Count of unique students |
| 🔢 **KPI row** | Card | `Attendance %` | Share of "Present" days |
| 🔢 **KPI row** | Card | `Avg Score` | Average raw score |
| 📈 **Bottom row** | Line chart | `Scores[Term]` × `%score` | Performance trend across terms |
| 📊 **Bottom row** | Clustered column | `Scores[Subject]` × `Avg Score`, legend = `Students[Class]` | Subject comparison by class |
| 📋 **Bottom row** | Table | `Name`, `Subject`, `%score` | Student-level detail |

---

### 🧮 5. DAX Measures

All measures are stored in the **Attendance** table.

#### ➗ `%score` — Score Percentage
```dax
%score = DIVIDE(SUM(Scores[Score]), SUM(Scores[MaxScore]))
```

#### 📊 `Avg Score` — Average Raw Score
```dax
Avg Score = AVERAGE(Scores[Score])
```

#### 🧑‍🎓 `Total students` — Unique Student Count
```dax
Total students = DISTINCTCOUNT(Students[StudentID])
```

#### 🗓️ `Attendance %` — Presence Rate
```dax
Attendance % =
DIVIDE(
    CALCULATE(COUNTROWS(Attendance), Attendance[Status] = "Present"),
    COUNTROWS(Attendance)
)
```

#### 🚦 `Behavior count` — Number of Behavior Records
```dax
Behavior count = COUNTROWS(Behavior)
```

#### 🏅 `Performance catagory` — Score Banding
```dax
Performance catagory =
SWITCH(
    TRUE(),
    [%score] >= 0.75, "high",
    [%score] >= 0.5,  "Medium",
    "Law"
)
```

**Key Concepts Used:**

| Concept | Detail |
|---------|--------|
| ➗ `DIVIDE()` | Safe division that avoids divide-by-zero errors |
| 🎯 `CALCULATE()` | Changes filter context to count only "Present" rows |
| 🔢 `DISTINCTCOUNT()` | Counts unique student IDs |
| 🔀 `SWITCH(TRUE(), …)` | Clean multi-condition banding, a readable alternative to nested `IF` |
| 🔗 Filter Context | Slicers filter `Students`, which then filters all fact tables |

---

## 🛠️ Tech Stack

| Tool | Version | Purpose |
|------|---------|---------|
| 📊 **Power BI Desktop** | Latest (Fluent 2 theme) | Report authoring and visualization |
| 🧮 **DAX** | Built-in | Measures and KPI logic |
| 🧹 **Power Query (M)** | Built-in | Data loading and cleaning |
| 🗃️ **Data Model** | Star-style, 3 relationships | Linking students to scores, attendance, behavior |
| 📄 **CSV** | UTF-8 | Source data format |
| 🎨 **Custom Theme** | Fluent2-CY26SU10 | Consistent fonts and colors |

---

## 📈 Results & Insights

Based on the data currently loaded in the report:

| Metric | Value |
|--------|-------|
| 🧑‍🎓 **Total Students** | **1,000** (525 Male · 475 Female) across **Classes 1–12** and **Sections A, B, C** |
| 🗓️ **Overall Attendance** | **≈ 90.05 %** — 90,048 Present vs 9,952 Absent records |
| 📝 **Overall Score** | **≈ 49.9 %** — 30,000 records, each out of 100 |
| 📚 **Subjects** | Math, Science, English, History, Geography |
| 🧪 **Exam Types** | Unit Test, Mid Term, Final Exam across Term 1–3 |
| 🚦 **Behavior Types** | Disruptive (1,333), Late (1,302), Helpful (1,299), Participative (1,294), Absent without notice (1,272) |
| 📅 **Date Range** | 16 Jun 2024 – 16 Jun 2025 |

**Observations:**

- ✅ **Math** has the highest average score (≈ 50.8), while **Geography** has the lowest (≈ 49.2) — a very small gap.
- 📈 **Term 3** scores slightly higher (≈ 50.3) than Term 1 (≈ 49.7) and Term 2 (≈ 49.6).
- 🏅 Using the `Performance catagory` thresholds on each student's overall score, **514 students fall in "Law" (< 50 %)** and **486 in "Medium"**; none reach the "high" (≥ 75 %) band.
- 🔁 Scores, behavior, and attendance are evenly spread across classes, sections, and subjects, which suggests the dataset is **sample / synthetic data**, ideal for learning and portfolio use.

---

## 🏆 Advantages

| Advantage | Detail |
|-----------|--------|
| 🎓 **Beginner Friendly** | Covers loading, modeling, DAX, and visuals in one small project |
| 🔄 **Reusable Measures** | KPIs are defined once as DAX measures and reused across visuals |
| 🖱️ **Fully Interactive** | Slicers and cross-filtering make exploring data effortless |
| 📏 **Scalable** | Handles 100,000+ attendance rows with fast response |
| 🧩 **Well-Structured Model** | One dimension and three facts keep filters predictable |
| 🧪 **Extensible** | Easy to add pages for Attendance, Behavior, or teacher analysis |
| 📖 **Readable** | Clear naming of tables, columns, and measures |
| 🎨 **Clean Design** | Consistent theme, color palette, and layout |

---

## 🚀 How to Use

1. **Download or clone** this repository.
2. Open `STUDENTS_PERFORMANCE_DASHBOARD.pbix` in **Power BI Desktop**.
3. If Power BI shows a *data source error*, go to **Home → Transform data → Data source settings** and point each CSV to its new location (or edit the `Source` step of each query).
4. Click **Refresh** to reload the data.
5. Use the **Section**, **Class**, and **Subject** slicers to explore the dashboard.

> 💡 *Tip: To avoid path errors, create a Power Query parameter such as `FolderPath` and reference it in all four queries.*

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for full details.

```
MIT License — Free to use, modify, and distribute with attribution.
```

---

## 👤 Author

<div align="center">

### Ayush Isamaliya

[![GitHub](https://img.shields.io/badge/GitHub-yourhandle-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/isamaliya16)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/ayush-isamaliya-686533312/)

> *"Every dashboard starts with a single question — just like every insight starts with a single chart."*

**🎓 Role:** Data Analytics Enthusiast | Power BI Learner \
**📍 Location:** India\
**🛠️ Skills:** Power BI · DAX · Power Query · Data Modeling · Data Visualization

</div>

---

## 🙏 Acknowledgements

Special thanks to the following resources and communities that made this project possible:

- 📚 [Microsoft Learn — Power BI](https://learn.microsoft.com/power-bi/) — Official Power BI documentation
- 🧮 [DAX Guide](https://dax.guide/) — Complete DAX function reference
- 🧹 [Power Query M Reference](https://learn.microsoft.com/power-query/) — Data transformation guide
- ⭐ [Star Schema Guidance](https://learn.microsoft.com/power-bi/guidance/star-schema) — Data modeling best practices
- 🎨 [Power BI Themes Gallery](https://community.fabric.microsoft.com/t5/Themes-Gallery/bd-p/ThemesGallery) — Design inspiration
- 💬 [Microsoft Fabric Community](https://community.fabric.microsoft.com/) — Problem-solving support
- 📖 [Kaggle Learn](https://www.kaggle.com/learn) — Data analysis courses

---

<div align="center">

---

*Made with ❤️ and ☕ — Last updated: 3 November, 2026*

</div>
