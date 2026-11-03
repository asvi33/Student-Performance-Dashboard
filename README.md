<div align="center">

# 🎓 ✨ Student Performance Dashboard ✨ 🎓
### *Interactive Power BI Report — Academic & Behavioral Insights*

[![Power BI](https://img.shields.io/badge/Power%20BI-Desktop-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-Measures-5EEAD4?style=for-the-badge&logo=microsoft&logoColor=black)](https://learn.microsoft.com/en-us/dax/)
[![Power Query](https://img.shields.io/badge/Power%20Query-Data%20Cleaning-F5C26B?style=for-the-badge&logo=microsoftexcel&logoColor=black)](https://learn.microsoft.com/en-us/power-query/)
[![Data Model](https://img.shields.io/badge/Data%20Model-Star%20Schema-FB7185?style=for-the-badge&logo=databricks&logoColor=white)](https://learn.microsoft.com/en-us/power-bi/transform-model/)
[![Dataset](https://img.shields.io/badge/Dataset-4%20CSV%20Files-6366F1?style=for-the-badge&logo=files&logoColor=white)](#-data-model)

<br/>

![Dashboard Preview](images/01-academic-performance.png)

<br/>

> *"Data tells the story of every student — a good dashboard makes sure the right people can read it."*

</div>

---

## 📋 Table of Contents

- [📌 Overview](#-overview)
- [🎯 Problem Statement](#-problem-statement)
- [✨ Key Features](#-key-features)
- [🏗️ Project Structure](#️-project-structure)
- [🗃️ Data Model](#️-data-model)
- [🔄 Project Workflow](#-project-workflow)
- [📚 Page 1 — Academic Performance](#-page-1--academic-performance)
- [🧠 Page 2 — Behavioral Insights](#-page-2--behavioral-insights)
- [👤 Page 3 — Student Profile (Drillthrough)](#-page-3--student-profile-drillthrough)
- [💬 Page 4 — Tooltip](#-page-4--tooltip)
- [🛠️ Tech Stack](#️-tech-stack)
- [📈 Results & Insights](#-results--insights)
- [🏆 Advantages](#-advantages)
- [🚀 How to Use](#-how-to-use)
- [📄 License](#-license)
- [👤 Author](#-author)
- [🙏 Acknowledgements](#-acknowledgements)

---

## 📌 Overview

The **Student Performance Dashboard** is an interactive, dark-themed **Power BI** report that combines **academic results**, **attendance** and **behavior records** of **1,000 students** into one place. Teachers and school administrators can filter by class, section, term, subject and gender, compare performance across classes, and drill down to the full profile of any single student with a right-click.

This project is designed to:
- 📊 Turn four raw CSV files into a clean, connected **data model**
- 🧮 Build reusable **DAX measures** for scores, attendance and behavior
- 🎛️ Provide **slicers, bookmarks and navigation** for a smooth user experience
- 🔍 Support **drillthrough** and **report-page tooltips** for deeper analysis

---

## 🎯 Problem Statement

> **Objective:** Build an interactive dashboard that helps schools understand how academics, attendance and behavior relate to student performance.

Schools store marks, attendance and behavior notes in separate sheets, which makes it hard to see the full picture of a student or a class. This report brings everything together and answers questions such as *"Which class is struggling?"*, *"How is attendance split?"* and *"Which behaviors occur most often?"*

| 📂 Report Page | 📄 Type | 🔍 Description |
|---------------|---------|----------------|
| Academic Performance | Main page | Scores by class, subject, term and exam type |
| Behavioral Insights | Main page | Behavior types, attendance split and behavior log |
| Student Profile | Hidden drillthrough | Complete profile of one selected student |
| Tooltip | Hidden tooltip | Mini-summary shown when hovering over charts |

The goal is to demonstrate **end-to-end BI skills** — data modeling, DAX, visual design and interactivity — in one report.

---

## ✨ Key Features

| Feature | Description |
|--------|-------------|
| 🎛️ **Dynamic Slicers** | Filter by Class, Section, Term, Subject, Gender and BehaviorType |
| 🔀 **Page Navigation** | *Academic View* / *Behavioral View* buttons built with bookmarks |
| 📊 **KPI Cards** | Total Students, Average Score per Subject, % Score, Attendance %, Behavior Count |
| 🎨 **Custom Dark Theme** | "Midnight Gold" theme with teal, gold, coral and violet accents |
| 🔍 **Drillthrough** | Right-click any student → *Drill through* → *Student Profile* |
| 💬 **Report-Page Tooltips** | Hover on a chart to see a mini-dashboard with % Score and exam-type breakdown |
| 🚦 **Conditional Formatting** | Student table highlights scores — green above 80 %, red below 40 % |
| 📋 **Behavior Log** | Scrollable table with date, student name and behavior type |
| ⬅️ **Back Button** | Returns from the Student Profile to the previous page |

---

## 🏗️ Project Structure

```
📦 student-performance-dashboard/
│
├── 📊 Student-Performance-Dashboard.pbix   ← Main Power BI report
│
├── 🖼️ images/
│   ├── 01-academic-performance.png         ← Page 1 screenshot
│   ├── 02-behavioral-insights.png          ← Page 2 screenshot
│   ├── 03-student-profile.png              ← Page 3 screenshot
│   └── 04-tooltip.png                      ← Tooltip screenshot
│
└── 📄 README.md                            ← Project documentation
```

---

## 🗃️ Data Model

The report is powered by **four fact/dimension tables** loaded from CSV files, plus one **Measure table** that holds all DAX calculations.

| 🗂️ Table | 📄 Role | 🔑 Key Columns |
|----------|---------|----------------|
| **Students** | Dimension | StudentID, Name, Gender, Class, Section |
| **Scores** | Fact | StudentID, Subject, Term, ExamType, Score |
| **Attendance** | Fact | StudentID, Date, Status (Present / Absent) |
| **Behavior** | Fact | StudentID, Date, BehaviorType, Notes |
| **Measure** | Calculations | All DAX measures (listed below) |

### 🧮 DAX Measures

| Measure | What it shows |
|---------|---------------|
| 👥 **Total Students** | Number of distinct students in the current filter |
| 📘 **Average Score per Subject** | Mean score across subjects |
| 🎯 **% Score** | Score as a percentage of the maximum marks |
| 🗓️ **Attendance %** | Share of attendance records marked *Present* |
| ⚠️ **Behavior Count per Type** | Number of behavior records per behavior type |
| 🏅 **Performance Category** | Low / Medium / High label based on % Score |

> 🔗 **Relationships:** `Students[StudentID]` is connected to Scores, Attendance and Behavior, so one slicer or one drillthrough filter updates every table.

---

## 🔄 Project Workflow

```
Raw CSV Files (Students · Scores · Attendance · Behavior)
                      │
                      ▼
┌─────────────────────────────────────┐
│   Power Query — Load & Clean Data   │  ← Types, headers, duplicates
└────────────────────┬────────────────┘
                     │
                     ▼
┌─────────────────────────────────────┐
│   Data Model — Relationships        │  ← StudentID as the common key
└────────────────────┬────────────────┘
                     │
                     ▼
┌─────────────────────────────────────┐
│   DAX — Create Measures             │  ← % Score, Attendance %, Category
└────────────────────┬────────────────┘
                     │
         ┌───────────┴────────────┐
         ▼                        ▼
┌─────────────────┐     ┌──────────────────┐
│ Academic Page   │     │ Behavioral Page  │
└────────┬────────┘     └─────────┬────────┘
         │                        │
         └──── right-click ───────┘
                     │
                     ▼
┌─────────────────────────────────────┐
│  Student Profile (Drillthrough)     │  ← One student, full picture
└────────────────────┬────────────────┘
                     │
                     ▼
        Hover on charts → Tooltip page 💬
```

---

## 📚 Page 1 — Academic Performance

<div align="center">

![Academic Performance](images/01-academic-performance.png)

</div>

> The main page for exam results. Use the slicers at the top to focus on any class, section, term, subject or gender.

### 🔹 What's on this page

| Visual | Type | Purpose |
|--------|------|---------|
| 🔢 **KPI Cards** | Card | Total Students, Average Score per Subject, % Score, Attendance % |
| 📊 **Average Score by Class & Subject** | Clustered Column | Compare all 5 subjects across classes 1 – 12 |
| 📈 **Performance Trend by Term** | Line Chart | See how each subject moves from Term 1 to Term 3 |
| 📋 **Student-wise Scores** | Table | Student, class, subject, % Score and Performance Category with conditional colors |
| 📉 **% Score by Exam Type** | Clustered Bar | Final Exam vs Mid Term vs Unit Test per subject |

### 💡 How to use it
- 🎛️ Pick a **Class** or **Subject** in the slicers — every visual updates instantly.
- 🖱️ **Right-click a student** in the table → **Drill through** → **Student Profile**.
- 💬 **Hover** on the charts to see the tooltip mini-dashboard.
- 🔀 Click **Behavioral View** to switch to the next page.

---

## 🧠 Page 2 — Behavioral Insights

<div align="center">

![Behavioral Insights](images/02-behavioral-insights.png)

</div>

> The second page combines **behavior records** with **attendance** so you can see conduct and presence side by side.

### 🔹 What's on this page

| Visual | Type | Purpose |
|--------|------|---------|
| 🔢 **KPI Cards** | Card | Total Students, Attendance %, Behavior Count per Type, % Score |
| 🍩 **Behavior Types Distribution** | Donut | Share of Absent without notice, Disruptive, Helpful, Late and Participative |
| 🍩 **Attendance: Present vs Absent** | Donut | Overall attendance split |
| 🧱 **Behavior by Class** | Stacked Column | Behavior count per class, stacked by behavior type |
| 📊 **Attendance by Class** | 100 % Stacked Column | Present vs Absent percentage for each class |
| 📊 **Behavior by Gender** | Clustered Bar | Behavior count per type, split by gender |
| 📋 **Behavior Log** | Table | Date, student name and behavior type |

### 💡 How to use it
- 🎛️ Filter by **Class**, **Section**, **Gender** or **BehaviorType**.
- 🔀 Click **Academic View** to go back to the first page.

---

## 👤 Page 3 — Student Profile (Drillthrough)

<div align="center">

![Student Profile](images/03-student-profile.png)

</div>

> A **hidden page** that opens when you drill through from a student row. It shows everything about **one student** — here, *Lara Simmons* (S0001, Class 10).

### 🔹 What's on this page

| Visual | Type | Purpose |
|--------|------|---------|
| 🪪 **Student Name Card** | Card | Shows the selected student's name |
| 🔢 **KPI Cards** | Card | % Score, Average Score per Subject, Behavior Count, Performance Category |
| 📊 **% Score by Subject** | Clustered Bar | Subject-wise result for the student |
| 📈 **Performance by Term** | Line Chart | Progress over terms |
| 🍩 **Behavior** | Donut | Student's behavior records by type |
| 🍩 **Attendance** | Donut | Student's present vs absent share |
| 📉 **% Score by Exam Type** | Clustered Column | Final Exam, Mid Term and Unit Test results |
| ⬅️ **Back Button** | Button | Returns to the page you came from |

### 💡 How to open it

```
Academic Performance page
        │
        ▼
Right-click a student row in the table
        │
        ▼
Drill through  ➜  Student Profile
```

> ℹ️ The page is filtered by **StudentID**. If you open it directly without drilling through, it shows data for all students.

---

## 💬 Page 4 — Tooltip

<div align="center">

![Tooltip Page](images/04-tooltip.png)

</div>

> A small **report-page tooltip** (360 × 260 px). When you hover over a chart on the Academic Performance page, this mini-dashboard pops up instead of the default tooltip.

| Element | Shows |
|---------|-------|
| 🟡 **Card 1** | % Score for the hovered bar / point |
| 🟢 **Card 2** | Average Score per Subject for the hovered bar / point |
| 📊 **Chart** | % Score by Exam Type (Final Exam, Mid Term, Unit Test) |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| 📊 **Power BI Desktop** | Report design, modeling and publishing |
| 🧮 **DAX** | Measures such as % Score, Attendance % and Performance Category |
| 🔧 **Power Query** | Loading and cleaning the CSV files |
| 🗃️ **Data Modeling** | Relationships on `StudentID` |
| 🎨 **Custom Theme (JSON)** | "Midnight Gold" dark theme with a teal / gold / coral palette |
| 🔖 **Bookmarks & Buttons** | Academic / Behavioral view navigation |
| 🔍 **Drillthrough & Tooltip Pages** | Student-level detail and hover summaries |
| 📁 **CSV Files** | Students, Scores, Attendance, Behavior |

---

## 📈 Results & Insights

What the dashboard shows for the current dataset:

- 👥 **1,000 students** across **classes 1 – 12**, tracked in **5 subjects** and **3 terms**
- 🎯 Overall **% Score is about 0.50** and the **average score is 49.87**, with all subjects scoring close to each other
- 🗓️ Attendance records split into **90.05 % Present** and **9.95 % Absent**
- ⚠️ **6,500 behavior records** in total, spread almost evenly over five types — *Absent without notice, Disruptive, Helpful, Late* and *Participative* (roughly 19 – 20 % each)
- 🔍 Individual profiles reveal differences hidden in the averages — for example, *Lara Simmons* scores **0.56 (High)** with a **96 % attendance** rate
- 🧭 The three exam types (Final Exam, Mid Term, Unit Test) can be compared for the whole school or for a single student

---

## 🏆 Advantages

| Advantage | Detail |
|-----------|--------|
| 🎓 **Single Source of Truth** | Scores, attendance and behavior in one connected model |
| 🎛️ **Fully Interactive** | Slicers, bookmarks, drillthrough and tooltips work together |
| 🎨 **Consistent Design** | One custom theme and grid layout on every page |
| 🔍 **From School to Student** | Move from school-level KPIs to one student's profile in two clicks |
| 🧮 **Reusable Measures** | All DAX lives in one Measure table for easy updates |
| 📱 **Easy to Read** | Large KPI cards, clear titles and dark theme for quick scanning |
| 🧪 **Extensible** | New terms, subjects or behavior types can be added without redesign |
| 🔄 **Refreshable** | Replace the CSV files and refresh to update every visual |

---

## 🚀 How to Use

1. 📥 **Download** the `Student-Performance-Dashboard.pbix` file.
2. 💻 Open it in **Power BI Desktop** (free from the Microsoft Store).
3. 🔧 If Power BI asks for the data location, go to **Transform data → Data source settings** and point to your CSV files.
4. 🔄 Click **Refresh** to load the latest data.
5. 🖱️ Explore: use slicers, then right-click a student and choose **Drill through → Student Profile**.

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for full details.

```
MIT License — Free to use, modify, and distribute with attribution.
```

---

## 👤 Author
Asvi Ambaliya
<div align="center">

[![GitHub](https://img.shields.io/badge/GitHub-isamaliya16-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/isamaliya16)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/ayush-isamaliya-686533312/)

> *"Every dashboard starts with a single question — and the best ones answer the next one too."*

**🎓 Role:** Junior Data Analyst | Power BI Enthusiast \
**📍 Location:** India \
**🛠️ Skills:** Power BI · DAX · Power Query · Data Modeling · Dashboard Design

</div>

---

## 🙏 Acknowledgements

Special thanks to the following resources and communities that made this project possible:

- 📚 [Microsoft Power BI Docs](https://learn.microsoft.com/en-us/power-bi/) — Official Power BI documentation
- 🧮 [DAX Guide](https://dax.guide/) — Complete DAX function reference
- 🔧 [Power Query Docs](https://learn.microsoft.com/en-us/power-query/) — Data transformation guide
- 🎨 [Power BI Themes Gallery](https://community.fabric.microsoft.com/t5/Themes-Gallery/bd-p/themes-galley) — Theme inspiration
- 🎓 [SQLBI](https://www.sqlbi.com/) — Data modeling and DAX best practices
- 💬 [Microsoft Fabric Community](https://community.fabric.microsoft.com/) — Problem-solving support
- 📖 [Kaggle Learn](https://www.kaggle.com/learn) — Data analysis courses

---

<div align="center">
Asvi Ambaliya
</div>
