<br/>
<p align="center">
  <a href="https://github.com//Data-Wrangling-Handling-Missing-Data">
    <img src="" alt="Logo" width="80" height="80">
  </a>

  <h3 align="center">Master the Art of Data Perfection with Our Data-Wrangling-Handling-Missing-Data Toolkit!</h3>

  <p align="center">
    Transform Missing Pieces into Powerful Insights - Elevate Your Data Game with Our Wrangling Wizardry!
    <br/>
    <br/>
    <a href="https://github.com//Data-Wrangling-Handling-Missing-Data"><strong>Explore the docs »</strong></a>
    <br/>
    <br/>
    <a href="https://github.com//Data-Wrangling-Handling-Missing-Data">View Demo</a>
    .
    <a href="https://github.com//Data-Wrangling-Handling-Missing-Data/issues">Report Bug</a>
    .
    <a href="https://github.com//Data-Wrangling-Handling-Missing-Data/issues">Request Feature</a>
  </p>
</p>

![Downloads](https://img.shields.io/github/downloads//Data-Wrangling-Handling-Missing-Data/total) ![Contributors](https://img.shields.io/github/contributors//Data-Wrangling-Handling-Missing-Data?color=dark-green) ![Stargazers](https://img.shields.io/github/stars//Data-Wrangling-Handling-Missing-Data?style=social) ![Issues](https://img.shields.io/github/issues//Data-Wrangling-Handling-Missing-Data) ![License](https://img.shields.io/github/license//Data-Wrangling-Handling-Missing-Data) 

## Table Of Contents

* [About the Project](#about-the-project)
* [Built With](#built-with)
* [Getting Started](#getting-started)
* [Roadmap](#roadmap)
* [Contributing](#contributing)
* [License](#license)
* [Authors](#authors)
* [Acknowledgements](#acknowledgements)

## About The Project

### Problem: Advanced Data Cleaning and Imputation in Diabetic Patient Records

#### Background
The Pima Indian Diabetes Database is a medical dataset that contains information on female patients of Pima Indian heritage, specifically designed for diabetes research. It includes several diagnostic measurements. However, the dataset has been found to have missing values, particularly in some key diagnostic columns. These missing values are recorded as zeros, which are not plausible values for certain medical metrics.

#### Objective
The goal is to clean the dataset by handling the missing values in a way that preserves the integrity of the data and prepares it for advanced analytical tasks, such as predictive modeling. Traditional methods of imputation, such as mean or median replacement, may not be suitable due to their potential to introduce bias or distort the underlying relationships in the data.

#### Specific Tasks
1. Identify and visualize the missing data for further insight.
2. Conduct an exploratory data analysis to establish a preliminary understanding of the data's structure and existing patterns.
3. Apply a sophisticated imputation technique that accounts for the multivariate nature of the data.
4. Scale the features to normalize the data, as this could improve the performance of the imputation algorithm.
5. Validate that the imputation has been successful and that no missing values remain.
6. Examine the distribution of the imputed data to ensure there are no unintended distortions.
7. Output the clean dataset for future analysis.

### Solution: Advanced Data Imputation Pipeline

The solution involves the application of an advanced data imputation pipeline using Python's scikit-learn, pandas, and seaborn libraries. The detailed steps are as follows:

1. **Visualizing Missing Data**: Using seaborn's heatmap, we immediately visualize the presence and distribution of missing data. This step is crucial for understanding the scope of the problem and planning the imputation strategy.

2. **Exploratory Data Analysis (EDA)**: We employ pandas' descriptive statistics to summarize the central tendencies and dispersions. This EDA is instrumental in revealing any underlying patterns or anomalies in the data, such as outliers, which may influence the choice of imputation technique.

3. **Imputation with K-Nearest Neighbors (KNN)**: We opt for a KNN-based imputation within the `IterativeImputer`. KNN imputation considers the feature space's multivariate nature and imputes missing values based on the similarity between instances. This approach is less biased than univariate methods and helps preserve the relationships in the data.

4. **Feature Scaling**: Before imputation, we scale our features using `MinMaxScaler`. This ensures that all features contribute equally to the distance computation in KNN, thereby avoiding any potential bias towards variables with larger scales.

5. **Implementing the Pipeline**: A pipeline is created to streamline the scaling and imputation process. This encapsulates the sequence of steps into a single process, ensuring reproducibility and ease of management.

6. **Transformation and Validation**: After executing the pipeline, we confirm the absence of missing values, ensuring that the dataset is now complete.

7. **Post-imputation Analysis**: We generate histograms of the imputed columns to inspect the distributions post-imputation. This step checks for any artificial skewness or biases introduced by the imputation.

8. **Exporting the Cleaned Data**: The final step involves saving the processed dataset to a CSV file, preserving the imputed values for any subsequent analysis.

By implementing this pipeline, we provide a robust solution to the missing data problem in the Pima Indians Diabetes Database, which is both sophisticated and considers the intricate relationships between variables. This not only prepares the dataset for more accurate modeling but also enhances the quality of any insights drawn from the data.

Let's provide a detailed walkthrough of each step in the advanced data imputation pipeline as implemented in the provided code:

1. **Visualizing Missing Data**:
   - The code uses `seaborn` to create a heatmap that visually represents where data is missing (denoted as `NaN`). This graphic illustration helps to immediately grasp the extent of missing data in the dataset, which can inform the strategy for imputation.

2. **Exploratory Data Analysis (EDA)**:
   - The `describe()` function generates descriptive statistics that summarize the central tendency, dispersion, and shape of the dataset's numerical features. This is essential for identifying the characteristics of the data, such as the presence of outliers or abnormal distributions, which might influence the imputation strategy.
   - The `isnull().sum()` function computes the number of missing values in each column. This step quantifies the problem, letting us know how much of the data is incomplete and requires imputation.

3. **Imputation with K-Nearest Neighbors (KNN)**:
   - The `IterativeImputer` with `KNeighborsRegressor` is a sophisticated imputation technique that fills in the missing values using a model-based approach. It considers the entire set of available features to predict the missing values rather than relying on a simpler per-feature imputation method. This can lead to more accurate imputations by preserving the relationships among features.

4. **Feature Scaling**:
   - The `MinMaxScaler` is included in the pipeline to scale the numerical features to a uniform range. KNN imputation is sensitive to the distances between data points, and scaling ensures that all features contribute equally to these distance calculations.

5. **Implementing the Pipeline**:
   - The pipeline object sequences the scaling and imputation steps, ensuring that they are executed in the correct order. The pipeline approach makes the code cleaner, more modular, and easier to modify or expand upon in the future.

6. **Transformation and Validation**:
   - By fitting the pipeline to the dataset, the code applies both scaling and imputation. After the transformation, another `isnull().sum()` check is performed to ensure that all missing values have been addressed.

7. **Post-imputation Analysis**:
   - Histograms for each feature that underwent imputation are plotted to assess the distribution of the newly imputed values. This step is critical to ensure the imputation process has not significantly distorted the data's original distribution, which could impact future analysis or predictive modeling negatively.

8. **Exporting the Cleaned Data**:
   - Finally, the `to_csv` function is called to save the preprocessed dataset to a new CSV file, thus making it ready for further analysis or modeling.

Through these steps, the code addresses the challenges posed by the missing data in the diabetes dataset. The choice of imputation method is particularly crucial. By opting for an iterative model-based technique that leverages the inter-feature relationships, the code aims to introduce as little bias as possible, thus preserving the data's overall structure and making subsequent analyses more reliable.

The code provided applies advanced data preprocessing techniques to a dataset known to have missing values. Here is a step-by-step explanation of what each part of the code is doing:

1. **Importing Necessary Libraries**:
   - `pandas` for data manipulation and analysis.
   - `numpy` for numerical operations.
   - `matplotlib.pyplot` and `seaborn` for data visualization.
   - `enable_iterative_imputer` is used to import `IterativeImputer`, even though it is an experimental feature from the sklearn library.
   - `IterativeImputer` for multivariate imputation of missing values.
   - `KNeighborsRegressor` which is used within the IterativeImputer for imputation.
   - `Pipeline` for chaining the preprocessing and imputation steps in a sequence.
   - `MinMaxScaler` for feature scaling which normalizes the data within a particular range.

2. **Loading the Dataset**:
   - A pandas DataFrame is created from the 'diabetes.csv' file.

3. **Identifying and Marking Missing Values**:
   - Certain columns known to contain zeros that may actually represent missing values are listed.
   - The zeros in these columns are replaced with `np.nan`, which is the standard missing value marker in pandas.

4. **Visualizing Missing Data**:
   - A heatmap is generated using seaborn, which provides a visual representation of the missing data. Missing values are shown in a different color, indicating where the data is incomplete.

5. **Exploratory Data Analysis (EDA)**:
   - The `.describe()` function provides a quick statistical summary of the numerical columns in the DataFrame. This helps in understanding the central tendency, dispersion, and shape of the dataset’s distribution.
   - The `.isnull().sum()` function counts the number of missing values per column, providing insight into the extent of missing data.

6. **Data Imputation Using a Sophisticated Approach**:
   - The `IterativeImputer` is configured to use `KNeighborsRegressor` which allows for more sophisticated imputation than simple mean or median imputation. It treats each feature as a function of other features.
   - `MinMaxScaler` is used to scale the data because KNN-based algorithms are sensitive to the scale of the data.
   - The scaling and imputation are combined into a `Pipeline` to ensure that the steps are applied in the correct sequence. The scaler is fitted first, and then the imputer is applied.

7. **Transforming the Data**:
   - The pipeline is fitted on the dataset, which scales the non-missing values and then performs imputation on the missing values. This transforms the specified columns, filling in the missing values with estimated ones.

8. **Verifying the Imputation**:
   - After transformation, `.isnull().sum()` is called again to ensure that all missing values have been imputed.

9. **Post-imputation Analysis**:
   - Histograms of the columns that underwent imputation are plotted, showing the distribution of the imputed values. This can be important to check whether the imputation strategy has introduced any biases or unexpected patterns into the data.

10. **Exporting the Preprocessed Data**:
    - Finally, the DataFrame with the imputed values is written back to a CSV file, preserving the modifications for future analysis or machine learning modeling.

In essence, this code applies robust techniques to deal with missing data, which is a common issue in real-world datasets. The imputation method used is more advanced than simple mean or median imputation, potentially leading to more accurate and reliable results in subsequent analyses or predictive modeling.

## Built With

This project is a testament to the power of modern data science tools and frameworks. Here's what we've used to tackle the challenge of missing data in complex datasets:

- **[Python](https://www.python.org/)** - The core programming language that brings our data wrangling capabilities to life. Python’s versatility and readability make it the lingua franca for data science tasks.
  
- **[Pandas](https://pandas.pydata.org/)** - A cutting-edge data manipulation tool, Pandas is our go-to for efficient data cleaning and analysis. Its DataFrame object provides the perfect canvas for handling and exploring structured data.
  
- **[NumPy](https://numpy.org/)** - Essential for high-performance mathematical computing, NumPy arrays underpin our data structures, allowing for efficient operations on large datasets.
  
- **[SciPy](https://www.scipy.org/)** - When complex mathematical functions or statistical operations are called for, SciPy steps in, extending the capabilities of NumPy into the realms of scientific computing.
  
- **[Scikit-learn](https://scikit-learn.org/stable/)** - Our machine learning powerhouse, Scikit-learn, provides us with advanced imputation methods, including iterative imputation with chaining predictors for a robust handling of missing data.
  
- **[Matplotlib](https://matplotlib.org/)** and **[Seaborn](https://seaborn.pydata.org/)** - These twin libraries arm us with sophisticated data visualization tools. Matplotlib lays the groundwork for customizable plots, while Seaborn builds on it to create attractive and informative statistical graphics.
  
- **[Jupyter Notebook](https://jupyter.org/)** - Development and documentation are seamless in Jupyter Notebooks, which allow us to interleave executable code with rich text, equations, and visualizations.

- **[Git](https://git-scm.com/)** - Version control is key to any successful project, and Git keeps our codebase secure, allowing for distributed development and version tracking.

- **[GitHub](https://github.com/)** - The hosting ground for our code and collaboration hub, GitHub brings our project to the global development community, facilitating issue tracking, feature requests, and user interaction.
  
- **[Sklearn-Pandas](https://github.com/scikit-learn-contrib/sklearn-pandas)** - This library bridges the gap between Scikit-learn's machine learning capabilities and Pandas' DataFrame, enabling us to streamline our data transformation and model fitting processes.

- **[Python-dotenv](https://pypi.org/project/python-dotenv/)** - For managing environment variables and keeping our configuration secrets safe, Python-dotenv is our tool of choice.

- **[Docker](https://www.docker.com/)** - Our application is containerized with Docker, ensuring that it runs smoothly in any environment, from development to deployment.

Each tool and library was chosen for its reliability and excellence in data science and machine learning tasks, ensuring that our project is built upon a solid foundation of the best technologies available.


## Getting Started

Welcome to our Data Wrangling project for handling missing data with grace and efficiency! To get your environment set up and start wrangling data like a pro, follow these detailed instructions.

### Prerequisites

Before you dive in, make sure you have the following prerequisites installed on your system:

- Python (3.7 or later): You can download it from [Python's official site](https://www.python.org/downloads/). Ensure you have `pip` installed alongside Python, as it will be used to install other Python packages.

- Git: We use Git for version control. If you don't have it already, you can download it from [Git's official site](https://git-scm.com/downloads).

- A virtual environment tool: We recommend using `venv` (built into Python 3) or [conda](https://docs.conda.io/en/latest/) to create isolated Python environments.

### Installation

1. **Clone the Repository**: 
   To get started with the project, clone the repo to your local machine using the following command:
   ```
   git clone https://github.com/your-username/Data-Wrangling-Handling-Missing-Data.git
   ```
   Navigate into the project directory:
   ```
   cd Data-Wrangling-Handling-Missing-Data
   ```

2. **Set up a Python Virtual Environment**:
   It's best to create a virtual environment to keep dependencies required by different projects separate by running:
   ```
   python -m venv venv
   ```
   Activate the virtual environment:

   On Windows:
   ```
   venv\Scripts\activate
   ```

   On macOS and Linux:
   ```
   source venv/bin/activate
   ```

3. **Install Dependencies**:
   With your virtual environment active, install the project dependencies using `pip`:
   ```
   pip install -r requirements.txt
   ```

4. **Set Up Environment Variables**:
   Some configurations should not be hard-coded, such as secret keys or database URIs. If the project uses environment variables, you'll need to set them up:
   ```
   cp .env.example .env
   ```
   Then edit the `.env` file with your specific configurations.

### Running the Project Locally

After you have set up your environment and installed the dependencies, you're ready to run the project.

1. **Data Preparation**:
   If there is a need to preprocess the data or perform initial setup tasks, include those steps here. For example:
   ```
   python data_preparation.py
   ```

2. **Running the Imputation Script**:
   Execute the main script to start the data imputation process:
   ```
   python run_imputation.py
   ```

3. **Exploring the Data**:
   Launch Jupyter Notebook to explore the data and the results of your imputation:
   ```
   jupyter notebook
   ```

Now you're all set to explore, analyze, and visualize data without worrying about missing values!

### Running Tests

To ensure that everything is set up correctly, you can run the tests provided (if any):
```
python -m unittest discover
```

### Additional Documentation

Refer to the `docs` directory for more detailed documentation on the project's architecture, modules, and code examples.

## Contributing

We welcome contributions! Please read our [CONTRIBUTING.md](CONTRIBUTING.md) for details on how to submit pull requests, our code of conduct, and the process for submitting pull requests to us.

Happy Data Wrangling!
```

This section provides clear and concise steps for someone to set up the project from scratch. It outlines what software needs to be installed, how to install project-specific dependencies, and the steps to get the project up and running on a local machine.

## Roadmap

See the [open issues](https://github.com//Data-Wrangling-Handling-Missing-Data/issues) for a list of proposed features (and known issues).

## Contributing

Contributions are what make the open source community such an amazing place to be learn, inspire, and create. Any contributions you make are **greatly appreciated**.
* If you have suggestions for adding or removing projects, feel free to [open an issue](https://github.com//Data-Wrangling-Handling-Missing-Data/issues/new) to discuss it, or directly create a pull request after you edit the *README.md* file with necessary changes.
* Please make sure you check your spelling and grammar.
* Create individual PR for each suggestion.
* Please also read through the [Code Of Conduct](https://github.com//Data-Wrangling-Handling-Missing-Data/blob/main/CODE_OF_CONDUCT.md) before posting your first idea as well.

### Creating A Pull Request

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

Distributed under the MIT License. See [LICENSE](https://github.com//Data-Wrangling-Handling-Missing-Data/blob/main/LICENSE.md) for more information.

## Authors

* **Robbie** - *PhD Computer Science Student* - [Robbie](https://github.com/TribeOfJudahLion/) - **

## Acknowledgements

* []()
* []()
* []()
