<div align="center">

# -- ! Students Performance Dashboard ! --
### *Interactive Power BI Dashboard for Academic, Attendance & Behavior Analysis*

[![Power BI](https://img.shields.io/badge/Power%20BI-Desktop-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-Measures%20%26%20Logic-856EAB?style=for-the-badge&logo=microsoft&logoColor=white)](https://learn.microsoft.com/en-us/dax/)
[![Power Query](https://img.shields.io/badge/Power%20Query-ETL%20%26%20Cleaning-0078D4?style=for-the-badge&logo=microsoftexcel&logoColor=white)](https://learn.microsoft.com/en-us/power-query/)
[![Data](https://img.shields.io/badge/Data-4%20CSV%20Files-4CAF50?style=for-the-badge&logo=files&logoColor=white)](#-dataset-description)

<br/>

> *"Data tells the story of every student — a good dashboard makes sure someone listens."*

</div>

---

## 📋 Table of Contents

- [📌 Overview](#-overview)
- [🎯 Problem Statement](#-problem-statement)
- [✨ Key Features](#-key-features)
- [🏗️ Project Structure](#️-project-structure)
- [🔄 Project Workflow](#-project-workflow)
- [📂 Dataset Description](#-dataset-description)
- [🧹 Part A — Data Preparation (Power Query)](#-part-a--data-preparation-power-query)
- [🗺️ Part B — Data Model & Relationships](#️-part-b--data-model--relationships)
- [🧮 Part C — DAX Measures](#-part-c--dax-measures)
- [📊 Part D — Dashboard Pages](#-part-d--dashboard-pages)
- [🛠️ Tech Stack](#️-tech-stack)
- [📈 Results & Insights](#-results--insights)
- [🚀 How to Use](#-how-to-use)
- [🏆 Advantages](#-advantages)
- [📄 License](#-license)
- [👤 Author](#-author)
- [🙏 Acknowledgements](#-acknowledgements)

---

## 📌 Overview

The **Students Performance Dashboard** is a two-page, interactive **Power BI** report that brings together student **exam scores**, **daily attendance**, and **behavior records** into a single, easy-to-read view. It lets teachers and school administrators filter by **class, section, subject, and term** and instantly see how students are performing — academically and behaviorally.

This project is designed to:
- Combine four separate CSV files into one clean **star-style data model**
- Practice **Power Query** cleaning and **DAX** measure writing
- Build interactive visuals — KPI cards, slicers, line, column and donut charts, and detail tables
- Turn raw school records into **actionable insights** for decision-making

---

## 🎯 Problem Statement

> **Objective:** Build an interactive dashboard to monitor and analyze student academic performance, attendance, and behavior across classes and sections.

School data is usually scattered across multiple files — scores in one place, attendance in another, behavior notes somewhere else. This makes it hard to answer simple questions like *"Which class is struggling in Math?"* or *"Which students have low attendance and frequent behavior issues?"*

| 📂 Dashboard Page | 📄 Focus | 🔍 Description |
|-------------------|----------|----------------|
| Academic dashboard | Scores & Attendance | Avg score, attendance %, subject-wise and term-wise performance |
| Behavioral dashboard | Behavior & Attendance | Behavior counts by type and class, student-level behavior table |

The goal is to deliver a **single source of truth** for student performance, driven entirely by slicers.

---

## ✨ Key Features

| Feature | Description |
|--------|-------------|
| 📑 **2 Interactive Pages** | Separate *Academic* and *Behavioral* dashboards |
| 🎛️ **Dropdown Slicers** | Filter by Class, Section, Subject and Term |
| 🔢 **KPI Cards** | Total Students, Attendance %, Average Score, Behavior Count |
| 📈 **Trend Analysis** | Score percentage trend across Term 1, 2 and 3 |
| 📊 **Subject Comparison** | Average score per subject, split by class |
| 🍩 **Behavior Breakdown** | Donut and column charts by behavior type and class |
| 📋 **Student-Level Tables** | Drill down to individual student names with scores / behavior counts |
| 🎨 **Custom Theme** | Fluent 2 base theme with purple (`#856EAB`) header banner and icon set |
| 🔗 **Linked Data Model** | 3 many-to-one relationships tied to a single Students table |

---

## 🏗️ Project Structure

```
📦 students-performance-dashboard/
│
├── 📊 STUDENTS_PERFORMANCE_DASHBOARD.pbix   ← Main Power BI report (entry point)
│
├── 📁 data/                                  ← Source CSV files
│   ├── 📄 Students.csv                       ← Student master data
│   ├── 📄 Scores.csv                         ← Exam scores
│   ├── 📄 Attendance.csv                     ← Daily attendance records
│   └── 📄 Behavior.csv                       ← Behavior incident / note records
│
└── 📄 README.md                              ← Project documentation
```

---

## 🔄 Project Workflow

```
        Raw CSV Files
 (Students · Scores · Attendance · Behavior)
                  │
                  ▼
┌──────────────────────────────────┐
│   Power Query — Load & Clean     │  ← Promote headers, set data types,
│                                  │    replace blank reasons with "N/A"
└────────────────┬─────────────────┘
                 │
                 ▼
┌──────────────────────────────────┐
│   Data Model — Relationships     │  ← Scores / Attendance / Behavior
│                                  │    → Students (via StudentID)
└────────────────┬─────────────────┘
                 │
                 ▼
┌──────────────────────────────────┐
│   DAX — Create Measures          │  ← %score, Avg Score, Attendance %,
│                                  │    Total students, Behavior count
└────────────────┬─────────────────┘
                 │
        ┌────────┴────────┐
        ▼                 ▼
┌───────────────┐  ┌────────────────┐
│  Page 1       │  │  Page 2        │
│  Academic     │  │  Behavioral    │
│  Dashboard    │  │  Dashboard     │
└───────┬───────┘  └───────┬────────┘
        │                  │
        └────────┬─────────┘
                 ▼
     Slicers → Insights ✅
```

---

## 📂 Dataset Description

The dashboard is built on **four CSV files** loaded through Power Query.

| 📄 File | 📏 Rows | 🧾 Columns | 🔍 Description |
|---------|--------:|-----------|----------------|
| `Students.csv` | 1,000 | `StudentID`, `Name`, `Gender`, `Class`, `Section` | One row per student — Class 1 to 12, Sections A / B / C |
| `Scores.csv` | 30,000 | `StudentID`, `Subject`, `ExamType`, `Score`, `MaxScore`, `Term` | Exam results — 5 subjects, 3 exam types, 3 terms |
| `Attendance.csv` | 100,000 | `StudentID`, `Date`, `Status`, `Reason` | Daily attendance — *Present* or *Absent* with reason |
| `Behavior.csv` | 6,500 | `StudentID`, `Date`, `BehaviorType`, `Notes` | Behavior incidents / observations with teacher notes |

**Category values in the data:**

| Field | Values |
|-------|--------|
| 📚 **Subject** | Math, Science, English, History, Geography |
| 📝 **ExamType** | Unit Test, Mid Term, Final Exam |
| 🗓️ **Term** | Term 1, Term 2, Term 3 |
| 🎭 **BehaviorType** | Disruptive, Late, Helpful, Participative, Absent without notice |
| ✅ **Attendance Status** | Present, Absent |

> 📅 **Date range covered:** 16 June 2024 → 16 June 2025 (one academic year)

---

## 🧹 Part A — Data Preparation (Power Query)

### 📝 1. Cleaning Steps

Each CSV is imported with `Csv.Document`, then cleaned with the same pattern:

| Step | Applied To | Detail |
|------|-----------|--------|
| 🔼 **Promote Headers** | All 4 tables | First row converted to column names |
| 🔠 **Change Data Types** | All 4 tables | IDs/text → `Text`, dates → `Date`, scores → `Whole Number` |
| 🔄 **Replace Blank Values** | `Attendance[Reason]` | Empty reasons replaced with `"N/A"` |

**Logic (Attendance table):**
```powerquery
let
  Source = Csv.Document(File.Contents("...\Attendance.csv"),
           [Delimiter = ",", Columns = 4, QuoteStyle = QuoteStyle.None]),
  #"Promoted headers" = Table.PromoteHeaders(Source, [PromoteAllScalars = true]),
  #"Changed column type" = Table.TransformColumnTypes(#"Promoted headers",
           {{"StudentID", type text}, {"Date", type date},
            {"Status", type text}, {"Reason", type text}}),
  #"Replaced value" = Table.ReplaceValue(#"Changed column type", "", "N/A",
           Replacer.ReplaceValue, {"Reason"})
in
  #"Replaced value"
```

> ⚠️ **Note:** The source file paths point to a local folder. After downloading the project, update them via **Home → Transform data → Data source settings**.

---

## 🗺️ Part B — Data Model & Relationships

### 🔗 2. Relationship Diagram

`Students` acts as the central **dimension** table; the three fact-style tables connect to it through `StudentID`.

```
                ┌──────────────┐
                │   Students   │
                │  (1,000 rows)│
                └──────┬───────┘
                       │ StudentID  (1)
       ┌───────────────┼───────────────┐
       │ (*)           │ (*)           │ (*)
┌──────▼──────┐ ┌──────▼──────┐ ┌──────▼──────┐
│   Scores    │ │ Attendance  │ │  Behavior   │
│ (30,000)    │ │ (100,000)   │ │ (6,500)     │
└─────────────┘ └─────────────┘ └─────────────┘
```

| 🔗 From (Many) | ➡️ To (One) | Key | Cardinality | Filter Direction |
|---------------|------------|-----|-------------|------------------|
| `Scores` | `Students` | `StudentID` | Many-to-One | Single |
| `Attendance` | `Students` | `StudentID` | Many-to-One | Single |
| `Behavior` | `Students` | `StudentID` | Many-to-One | Single |

Because of this design, a slicer on `Students[Class]` or `Students[Section]` filters **scores, attendance and behavior at the same time**.

---

## 🧮 Part C — DAX Measures

### 🧠 3. Measures Used

All measures are stored in the `Attendance` table.

| 📌 Measure | 🧾 DAX Formula | 🔍 Purpose |
|-----------|----------------|-----------|
| **Total students** | `DISTINCTCOUNT(Students[StudentID])` | Unique number of students in the current filter |
| **%score** | `DIVIDE(SUM(Scores[Score]), SUM(Scores[MaxScore]))` | Overall score percentage |
| **Avg Score** | `AVERAGE(Scores[Score])` | Average marks per exam record |
| **Attendance %** | `DIVIDE(CALCULATE(COUNTROWS(Attendance), Attendance[Status] = "Present"), COUNTROWS(Attendance))` | Share of days a student was present |
| **Behavior count** | `COUNTROWS(Behavior)` | Total number of behavior records |
| **Performance category** | `SWITCH(TRUE(), [%score] >= 0.75, "High", [%score] >= 0.5, "Medium", "Low")` | Groups students into High / Medium / Low performers |

**Key Concepts Used:**

| Concept | Detail |
|---------|--------|
| ➗ `DIVIDE()` | Safe division — avoids divide-by-zero errors |
| 🎯 `CALCULATE()` | Changes filter context to count only *Present* rows |
| 🔢 `DISTINCTCOUNT()` | Counts unique students, not rows |
| 🔀 `SWITCH(TRUE(), …)` | Clean multi-condition categorization |

---

## 📊 Part D — Dashboard Pages

### 🎓 4. Page 1 — Academic Dashboard

> Focus on **how students are performing in exams** and how that connects to attendance.

| 🧩 Visual | 📐 Type | 🗂️ Fields Used |
|-----------|--------|----------------|
| Class filter | Dropdown slicer | `Students[Class]` |
| Section filter | Dropdown slicer | `Students[Section]` |
| Subject filter | Dropdown slicer | `Scores[Subject]` |
| Term filter | Dropdown slicer | `Scores[Term]` |
| Total Students | Card | `Total students` |
| Attendance % | Card | `Attendance %` |
| Average Score | Card | `Avg Score` |
| Score Trend by Term | Line chart | `Scores[Term]` × `%score` |
| Avg Score by Subject & Class | Clustered column chart | `Scores[Subject]` × `Avg Score`, legend = `Students[Class]` |
| Student Score Table | Table | `Students[Name]`, `Scores[Subject]`, `%score` |

---

### 🎭 5. Page 2 — Behavioral Dashboard

> Focus on **student conduct** — what types of behavior occur, where, and who is involved.

| 🧩 Visual | 📐 Type | 🗂️ Fields Used |
|-----------|--------|----------------|
| Class filter | Dropdown slicer | `Students[Class]` |
| Section filter | Dropdown slicer | `Students[Section]` |
| Behavior Count | Card | `Behavior count` |
| Attendance % | Card | `Attendance %` |
| Total Students | Card | `Total students` |
| Behavior Type Split | Donut chart | `Behavior[BehaviorType]` × `Behavior count` |
| Behavior by Class | Column chart | `Students[Class]` × `Behavior count`, legend = `BehaviorType` |
| Student Behavior Table | Table | `Students[Name]`, `Behavior count`, `Attendance %` |

---

### 🎨 6. Design Details

| Element | Detail |
|---------|--------|
| 🖼️ **Canvas Size** | 1920 × 1080 (Full HD), *Fit to page* |
| 🎨 **Theme** | Fluent 2 base theme |
| 🟣 **Header Banner** | Purple `#856EAB` with white Arial title |
| 🧷 **Icons** | Education, mortarboard, immigration and behavior icons for visual cues |
| 🔤 **Typography** | Large bold KPI values (25–27 pt) for quick reading |

---

## 🛠️ Tech Stack

| Tool | Version | Purpose |
|------|---------|---------|
| 📊 **Power BI Desktop** | Latest | Report design and publishing |
| 🧹 **Power Query (M)** | Built-in | Loading and cleaning CSV data |
| 🧮 **DAX** | Built-in | Measures and calculated logic |
| 🗂️ **CSV Files** | — | Raw data sources |
| 🎨 **Fluent 2 Theme** | Built-in | Consistent visual styling |

---

## 📈 Results & Insights

Based on the data loaded in this report (all classes, sections, subjects and terms selected):

- ✅ **1,000 students** tracked across **Classes 1–12** and **Sections A, B, C**
- 📝 **Overall score ≈ 49.9%** across 30,000 exam records (every exam is out of 100)
- 🗓️ **Attendance ≈ 90.05%** — 90,048 *Present* vs 9,952 *Absent* out of 100,000 records
- 🎭 **6,500 behavior records** spread almost evenly across five behavior types:

| Behavior Type | Records | Nature |
|---------------|--------:|--------|
| Disruptive | 1,333 | ⚠️ Negative |
| Late | 1,302 | ⚠️ Negative |
| Helpful | 1,299 | ✅ Positive |
| Participative | 1,294 | ✅ Positive |
| Absent without notice | 1,272 | ⚠️ Negative |

- ⚖️ Negative behavior records (**3,907**) outnumber positive ones (**2,593**), which highlights where intervention could help
- 🔍 Slicers make it easy to find the weakest class / subject / term and then drill down to individual students in the tables

---

## 🚀 How to Use

1. 📥 **Download** `STUDENTS_PERFORMANCE_DASHBOARD.pbix` and the `data/` folder
2. 🖥️ **Open** the `.pbix` file in **Power BI Desktop**
3. 🔧 **Update data source paths** — *Home → Transform data → Data source settings → Change Source*
4. 🔄 Click **Refresh** to reload the data
5. 🎛️ Use the **dropdown slicers** (Class, Section, Subject, Term) to explore
6. 🔀 Switch between the **Academic dashboard** and **Behavioral dashboard** tabs at the bottom

---

## 🏆 Advantages

| Advantage | Detail |
|-----------|--------|
| 🎯 **Single View** | Scores, attendance and behavior in one dashboard |
| 🎛️ **Fully Interactive** | Every visual reacts instantly to slicer selections |
| 🔗 **Connected Model** | One `StudentID` key links all tables cleanly |
| 🧮 **Reusable Measures** | DAX measures work in any visual or future page |
| 🔍 **Drill-Down Ready** | From class-level trends to individual student rows |
| 📦 **Scalable** | Add new months, subjects or behavior types by simply refreshing CSVs |
| 🎓 **Beginner Friendly** | Demonstrates ETL → Modeling → DAX → Visualization end to end |
| 🧪 **Extensible** | Easy to add pages such as *Attendance Trends* or *Top / Bottom Performers* |

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

> *"Every chart starts with a single data point — just like every insight starts with a single question."*

**🎓 Role:** Junior Data Analyst | Power BI Enthusiast \
**📍 Location:** India\
**🛠️ Skills:** Power BI · DAX · Power Query · Data Modeling · Dashboard Design

</div>

---

## 🙏 Acknowledgements

Special thanks to the following resources and communities that made this project possible:

- 📚 [Microsoft Power BI Docs](https://learn.microsoft.com/en-us/power-bi/) — Official Power BI documentation
- 🧮 [DAX Guide](https://dax.guide/) — Complete DAX function reference
- 🧹 [Power Query M Reference](https://learn.microsoft.com/en-us/powerquery-m/) — M language documentation
- 🎨 [Flaticon](https://www.flaticon.com/) — Icons used in the dashboard design
- 💬 [Power BI Community](https://community.fabric.microsoft.com/) — Problem-solving support
- 📖 [Microsoft Learn](https://learn.microsoft.com/en-us/training/powerplatform/power-bi) — Power BI learning paths

---

<div align="center">

---

*Made with ❤️ and ☕ — Last updated: 3 November, 2026*

</div>
