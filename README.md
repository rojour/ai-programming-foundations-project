# AI Programming Foundations — Data Workflow

A reproducible data workflow analyzing Boston Marathon finishing results from 2016 and 2017. The project covers data ingestion, cleaning, exploratory analysis, and visualization using Python and Jupyter Notebook. The dataset contains approximately 53,000 runner records sourced from [Kaggle](https://www.kaggle.com/).

## How to Run

1. Clone the repository:

```bash
git clone https://github.com/<your-username>/ai-programming-foundations-project.git
cd ai-programming-foundations-project
```

2. Create a virtual environment and install dependencies:

```bash
python -m venv venv
source venv/bin/activate   # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

3. Open and run the notebook:

```bash
jupyter notebook data_workflow.ipynb
```

Run all cells top-to-bottom. The dataset CSV files must be in the same directory as the notebook.

## Where Poor Data Cleaning Could Introduce Bias

In this dataset, failing to properly clean the data could introduce bias in several ways. If the placeholder values (`"-"`) in the `Proj Time` column were not handled, they would either cause calculation errors or be silently excluded, skewing any analysis that depends on that column. Similarly, if the time-string columns were left unconverted, any numerical operation (averages, comparisons, sorting) would produce incorrect results or fail entirely. Dropping columns like `Citizen` without first examining whether the missingness is random or systematic could also hide meaningful patterns — for instance, if certain countries systematically lack citizen data, removing the column could obscure differences tied to nationality or residency status. Finally, aggregating statistics by country without accounting for vastly different sample sizes would produce misleading comparisons, since small delegations of elite athletes are not comparable to a field of thousands of recreational runners.
