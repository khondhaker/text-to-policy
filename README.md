# text-to-policy

# Race and Gender Prediction Using Machine Learning Models

This project uses machine learning models to predict the **race** and **gender** of individuals based on their **surname** and **first name**, respectively. The models are trained on textual features derived from names and utilize letter frequency vectors to make predictions.

---

## How It Works

### 1. **Input Requirements**
The prediction system takes two inputs:
- **First Name**: Used for gender prediction.
- **Surname**: Used for race prediction.

### 2. **Preprocessing**
Each name is transformed into a **letter frequency vector**:
- Convert the name to lowercase.
- Count the occurrence of each letter in the English alphabet (a–z).
- Represent the name as a 26-dimensional vector, where each entry corresponds to the frequency of a particular letter.

For example:
- Name: `"John"`
- Letter Frequency Vector: `[1, 0, 0, ..., 1, 1, 0, ...]`  
  - (1 occurrence of `j`, 1 occurrence of `o`, 1 occurrence of `h`, etc.)

---

### 3. **Prediction Models**
Two separate machine learning models are used for predictions:

#### A. **Race Prediction Model**
- **Input**: Letter frequency vector derived from the **surname**.
- **Output**: One of six race categories:
  - White
  - Hispanic
  - Asian or Pacific Islander
  - Black
  - Indian or Alaska Native
  - Other
- **Model Type**: k-Nearest Neighbors (k-NN).
- **Training**: The model was trained on a labeled dataset of surnames with corresponding race labels.

#### B. **Gender Prediction Model**
- **Input**: Letter frequency vector derived from the **first name**.
- **Output**: Gender categories:
  - Male
  - Female
- **Model Type**: Support Vector Machine (SVM).
- **Training**: The model was trained on a labeled dataset of first names with corresponding gender labels.

---

### 4. **System Workflow**
1. **Load Pretrained Models**:
   - The race and gender models are pre-trained and stored as compressed `.pkl.gz` files.
   - The system loads these models once during initialization.

2. **Process Names**:
   - The input names (first name for gender, surname for race) are preprocessed into letter frequency vectors.

3. **Run Predictions**:
   - The race model predicts the race based on the surname vector.
   - The gender model predicts the gender based on the first name vector.

4. **Output**:
   - Both predictions are returned in human-readable formats.

---

### 5. **Advantages of the System**
- **Efficient Model Loading**: Models are loaded once and reused for multiple predictions, reducing overhead.
- **Robust Input Handling**: The system ensures consistent preprocessing of input names, improving prediction accuracy.
- **Scalability**: The modular design allows for easy extension to handle other features or incorporate new models.

---

### 6. **Dependencies**
The system relies on the following Python libraries:
- **joblib**: For loading and saving machine learning models.
- **gzip**: For handling compressed model files.
- **pandas**: For managing input data as structured data frames.
- **collections.Counter**: For counting letter frequencies in names.

---

### 7. **Expected Output**
For a given input:
- **First Name**: `"John"`
- **Surname**: `"Smith"`

The output will be:
```plaintext
Predicted Race for 'Smith': White
Predicted Gender for 'John': Male
```

---

### 8. **Key Files**
- **`knn_race_prediction_model_Nov_2024.pkl.gz`**: Compressed file containing the trained k-NN model for race prediction.
- **`svm_gender_model_Nov_2024.pkl.gz`**: Compressed file containing the trained SVM model for gender prediction.

---

### 9. **How to Use**
1. Install the required Python dependencies:
   ```bash
   pip install joblib pandas
   ```
2. Ensure the pretrained model files are located in the same directory as the script.
3. Run the script and provide inputs for race and gender prediction.

---

### 10. **Future Work**
- Expand the race categories to include finer-grained classifications.
- Improve gender prediction by incorporating cultural or regional naming patterns.
- Add support for handling names from languages with non-Latin alphabets.
