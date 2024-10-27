# Cleaning data

## Handle missing data
- missing data -> choose frequency of occurrence, mean, meadian..
    ```python
    from sklearn.impute import SimpleImputer
    imputer = SimpleImputer(missing_values=np.nan, strategy='mean')

    df.isna().sum()
    ```
## One-hot encoding / Label encoding : categorical data. 
  
- Covert values in 1 columns to vector(0,1)
  Ex: Dog, Cat, Lion, -> (1,0,0), (0, 1, 0),

## Feature scaling
- Standardisa

## Handling Catogorical Variables



## Multicollinearity

## Attention
    ```python
        ## Code in cleaning project data
        ### Check sum of N/a
        df.isna().sum()

        ### Sort dec, asc
        df.sort_values(by= "ID")

        ### Reset index
        df.reset_index()

        ### Replace : M, S -> Marriage, Single
        df["Marital Status"].str.replace("M", "Marriage")
        df["Gender"] = df["Gender"].str.replace("F|M", lambda x: "Female" if x.group() == 'F' else "Male")

        ## Unique: How many different value in this column?
        df["Education"].unique()

        /////////
        ## Code in Customer Call list
        ### Drop N/a and fill NA
            - # Using dropna() to drop rows with missing values
                df.dropna()

                # Using dropna(axis=1) to drop columns with missing values
                df.dropna(axis=1)

        ### Drop duplicate 
        df.drop_duplicates()

        ### Drop column
        df.drop(columns= "Not_Useful_Column")

        ### Formmating 
        - Phone 
        - Date

        ### Rename Columns
        
        ### Pivot

    ```
## Moreover about cleaning: Imputation
    - Mean/Median Imputation: Replace missing values with the mean (average) or median of the non-missing values in the same column. This method is suitable for numerical data.

    Mode Imputation: Replace missing values with the mode (most frequent value) of the column. This is often used for categorical data.

    Constant Value Imputation: Replace missing values with a predefined constant value, such as 0 or -1, to indicate that data is missing.

    Forward Fill (or Previous Value) Imputation: Use the last observed value to fill in missing values in a time series or sequential data.

    Backward Fill (or Next Value) Imputation: Use the next observed value to fill in missing values in time series or sequential data.

    Regression Imputation: Predict missing values using regression models based on other variables in the dataset.

    K-Nearest Neighbors (K-NN) Imputation: Replace missing values with values from the nearest neighbors in the feature space, based on similarity.

    Multiple Imputation: Generate multiple complete datasets with different imputed values to account for uncertainty and variability in imputation.

    Interpolation: Use mathematical methods like linear interpolation or spline interpolation to estimate missing values based on neighboring data points.

    Deep Learning Imputation: Utilize deep learning models, such as autoencoders, to learn patterns and impute missing values.
