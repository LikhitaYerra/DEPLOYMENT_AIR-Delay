
# AIR Delay Prediction

## Overview

**AIR Delay Prediction** is a Flask-based web application designed to predict flight delays based on user inputs such as origin, destination, carrier, day of the week, and departure hour. The project uses a pre-trained machine learning model (loaded from `treemodel.pkl`) and a categorical index dictionary (loaded from `cat`) to make predictions. The application is deployable using Gunicorn for production environments.

## Features

- **Flight Delay Prediction**: Predicts whether a flight will be delayed based on key features.
- **Web Interface**: Simple HTML forms for user input and result display.
- **Machine Learning**: Utilizes a pre-trained decision tree model for predictions.
- **Deployment Ready**: Configured for deployment with Gunicorn.

## Installation

### Prerequisites

- Python 3.8+
- Git

### Dependencies

The project requires the following Python libraries (listed in `requirements.txt`):

```
Flask>=2.3.3
gunicorn>=20.1.0
numpy>=1.11.0
scikit-learn>=0.22.1
scipy>=1.11.3
```

### Steps

1. Clone the repository:
   ```
   git clone https://github.com/LikhitaYerra/DEPLOYMENT_AIR-Delay.git
   cd DEPLOYMENT_AIR-Delay
   ```

2. Install the required dependencies:
   ```
   pip install -r requirements.txt
   ```

3. Ensure the following files are present in the project root:
   - `cat`: Pickle file containing the categorical index dictionary.
   - `treemodel.pkl`: Pickle file containing the pre-trained decision tree model.
   - `templates/home.html`: HTML template for the input form.
   - `templates/result.html`: HTML template for displaying predictions.

## Usage

### Running Locally

1. Start the Flask development server:
   ```
   python app.py
   ```

2. Open your browser and navigate to `http://127.0.0.1:5000/` to access the application.

3. Enter flight details (origin, destination, carrier, day of week, departure hour) in the form and submit to get a delay prediction.

### Running in Production

For production deployment, use Gunicorn:
```
gunicorn app:app --log-file -
```

- This command runs the Flask app (`app:app` refers to the `app` object in `app.py`) and logs output to a file.
- Access the app at the configured host/port (default: `http://127.0.0.1:8000/`).

## Project Structure

```
DEPLOYMENT_AIR-Delay/
├── templates/           # HTML templates
│   ├── home.html        # Input form page
│   └── result.html      # Prediction result page
├── app.py               # Main Flask application
├── cat                  # Pickle file with categorical index dictionary
├── treemodel.pkl        # Pre-trained decision tree model
├── requirements.txt     # List of dependencies
└── README.md            # Project documentation
```

## How It Works

1. **Input**: Users provide flight details via a web form (`home.html`).

2. **Processing**: 
   - The app converts inputs into a one-hot encoded vector using the `cat` dictionary.
   - The vector is reshaped and fed into the pre-trained decision tree model (`treemodel.pkl`).

3. **Output**: The prediction (e.g., delay or no delay) is displayed on `result.html`.

## Notes

- The application assumes the existence of `cat` and `treemodel.pkl`. If these files are missing, the app will fail to run. Ensure they are generated or provided beforehand.
- Error handling is minimal (e.g., `try/except` blocks silently pass on invalid inputs). Consider enhancing this for robustness.

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository.

2. Create a feature branch (`git checkout -b feature-branch`).

3. Commit your changes (`git commit -m "Add feature"`).

4. Push to the branch (`git push origin feature-branch`).

5. Open a pull request.

## License

This project is licensed under the [MIT License](LICENSE) (or specify your preferred license).

## Contact

For questions or feedback, reach out to [Likhita Yerra](https://github.com/LikhitaYerra) via GitHub Issues.
```

