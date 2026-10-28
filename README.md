# Hospital Appointment & No-Show Analysis

## Understanding appointment attendance, scheduling lead time, reminder coverage, and operational risk

An exploratory data analysis project using Python and SQLite to investigate patterns associated with missed hospital appointments and translate those patterns into practical operational recommendations.

## Business Objective

Missed appointments reduce clinical capacity and can delay access to care. This project examines appointment-level data to answer:

- What is the overall no-show rate?
- Which patient and appointment characteristics are associated with higher no-show rates?
- How does scheduling lead time relate to attendance?
- How should SMS reminder results be interpreted in context?
- Which operational interventions are worth testing?

## Dataset

The project uses the Medical Appointment No Shows dataset supplied for this project, containing 110,527 appointment records and 14 original variables.

The dataset includes:

- Patient and appointment identifiers
- Gender and age
- Appointment and scheduling dates
- Neighbourhood
- Scholarship status
- Selected health indicators
- SMS reminder status
- Appointment outcome

The raw dataset is stored in `data/Medical Appointment No Shows.csv`.

## Tools

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SQLite
- Jupyter Notebook

## Analysis Workflow

1. Data quality audit
2. Data cleaning and validation
3. Appointment lead-time engineering
4. Age and patient segmentation
5. Executive KPI analysis
6. Appointment timing analysis
7. Demographic analysis
8. SMS reminder analysis
9. Health and social characteristic analysis
10. Neighbourhood analysis
11. Repeat-patient analysis
12. SQLite business queries
13. Operational risk segmentation
14. Business findings and recommendations

## Key Analytical Points

The analysis shows that:

- About one in five analysed appointments is a no-show.
- Same-day appointments have a substantially lower observed no-show rate than appointments scheduled several days or weeks in advance.
- No-show rates vary across age groups and appointment weekdays.
- Neighbourhood-level rates differ, but low-volume groups require cautious interpretation.
- SMS recipients have a different observed no-show rate from non-recipients, but this cannot be interpreted as evidence that SMS causes no-shows because reminder assignment is not random.
- Repeat-patient history provides additional context for operational segmentation.

## Important Data-Quality Decisions

- The dataset contains one invalid `Age = -1` value; it is treated as missing.
- Five records produce negative scheduling lead times; they are retained for audit transparency but excluded from lead-time analysis.
- No duplicate appointment records were found.
- No missing cells were found in the supplied raw dataset.
- Patient IDs are treated as identifiers rather than numeric measures.

## SQLite

The notebook creates `hospital_appointments.sqlite` automatically and stores the cleaned appointment-level analytical data in an `appointments` table.

The SQLite database is intentionally excluded from version control because it is a generated analytical artifact.

## Project Structure

```text
Hospital-Appointment-No-Show-Analysis/
│
├── data/
│   └── Medical Appointment No Shows.csv
│
├── Hospital_Appointment_No_Show_Analysis.ipynb
├── README.md
└── .gitignore
```

## How to Run

Clone the repository and open the project directory:

```bash
git clone https://github.com/mahendra-samant/Hospital-Appointment-No-Show-Analysis.git
cd Hospital-Appointment-No-Show-Analysis
```

Install the required packages:

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

Start Jupyter:

```bash
jupyter notebook
```

Open:

```text
Hospital_Appointment_No_Show_Analysis.ipynb
```

The notebook expects the dataset at:

```text
data/Medical Appointment No Shows.csv
```

Running the notebook creates the SQLite database locally.

## Limitations

This is an observational analysis. The results identify associations and patterns but do not establish causation.

Other limitations include:

- SMS assignment is not random.
- Repeated appointments from the same patient mean appointment records are not fully independent.
- Neighbourhood rates can be unstable for small samples.
- The dataset does not provide a reliable monetary cost for missed appointments.
- The available variables do not capture every clinical or operational reason for a missed appointment.

## Business Recommendations

The analysis suggests several areas for operational testing:

1. Prioritize additional confirmation for appointments scheduled well in advance.
2. Evaluate reminder timing and communication channels rather than simply increasing SMS volume.
3. Use observable appointment and patient-history characteristics to prioritize follow-up.
4. Monitor neighbourhood performance using both appointment volume and no-show rate.
5. Measure any new reminder or scheduling intervention using before/after or controlled evaluation.

## Conclusion

The project demonstrates an end-to-end analytical workflow from raw healthcare appointment data to data-quality assessment, feature engineering, visualization, SQL analysis, operational segmentation, and evidence-based recommendations.

The central analytical principle is to distinguish **association from causation** and validate operational interventions rather than assuming that a correlation represents a causal effect.

## Author

**Mahendra**

GitHub: `https://github.com/mahendra-samant`
