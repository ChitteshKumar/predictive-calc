# Project Structure

The directory layout of **Predictive Calc** is organized in a way that separates concerns between model development, frontend interaction, and configuration management. Below is a breakdown of the key folders and files:

```
predictive-calc/
├── app.py                          # Main entry point for the Streamlit web app
├── docs/                           # Documentation files
├── models/                         # Folder containing machine learning models
│   ├── house_price/                	# Example model directory (for house price prediction)
│	│   ├── data/                   	# Datasets used by the models
│   │   ├── notebooks/              	# Jupyter notebooks for training and experimentation
│   │   │   ├── house_price.ipynb 
│   │   ├── model.py                	# Code to define and train the model
│   │   ├── predict.py              	# Code to make predictions using the trained model
│	│   ├── saved_models/           	# Serialized (pickled) model files and scalers
│	│   │   ├── model.pkl               	# Trained model for predictions
│	│   │   ├── scaler.pkl              	# Scaler for data normalization
│   ├── modelEvaluation.py          	# Model evaluation Class
├── pages/                          # Streamlit pages representing different calculators
│   ├── house_price_calculator.py   	# Streamlit app page for house price prediction
├── form_configs/              # Configuration files for the forms
│   ├── house_price.json            	# JSON configuration for house price model form input fields
├── form_handler.py                 # Handles dynamic form generation based on JSON configs
├── requirements.txt                # List of Python dependencies
```

### Key Components

#### 1. `app.py`
This is the entry point for the **Streamlit** application. It initializes the app and renders the home page, and loads the model calculators having their pages in the `pages/` directory.

#### 2. `models/`
Each model gets its own folder within the `models/` directory, which contains all necessary files for that particular model. This includes:
- **notebooks/**: Jupyter notebooks for model training and experimentation.
- **model.py**: Code defining and training the finally chosen machine learning model.
- **predict.py**: Code to load the trained model and make predictions based on user input.
- **saved_models/**: Directory where the trained model (`model.pkl`) and any preprocessing objects like scalers (`scaler.pkl`) are stored.
- **data/**: Raw datasets used for training the model.
- **modelEvaluation.py**: Scripts for model evaluation and reporting.

#### 3. `pages/`
Each model has a corresponding Streamlit page in the `pages/` folder. This page handles the frontend logic, rendering the forms for user input and displaying the prediction results. For example, the `house_price_calculator.py` page contains the interface for the house price prediction model.

#### 4. `form_configs/`
The `form_configs/` folder contains JSON configuration files that define the input fields required by each model. These JSON files dictate how the forms are dynamically generated by `form_handler.py`. For example, the `house_price.json` file specifies the input fields (e.g., square footage, number of bedrooms, etc.) needed for the house price prediction model.

#### 5. `form_handler.py`
This script dynamically generates the input forms based on the JSON configuration files. It maps user inputs to the model’s expected parameters and passes the data to the prediction logic.

#### 6. `docs/`
Contains the project's documentation. This is where you can find information about how the system is structured and how to contribute to the project.