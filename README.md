# AI-Agent-for-smart-farming-advice

AI Agent for Smart Farming Advice
An intelligent, conversational AI agent designed to provide small-scale farmers with real-time, data-driven agricultural advice. This project leverages a Retrieval-Augmented Generation (RAG) architecture, combining historical data analysis, AI-based price prediction, and live environmental data to empower farmers with actionable insights.

📖 Table of Contents
Problem Statement

Key Features

System Architecture

Technology Stack

Setup and Installation

How to Run

Usage Examples

Data Source

Future Scope

🎯 Problem Statement
Small-scale farmers often lack access to timely, localized, and actionable data, forcing them to rely on traditional practices which can lead to suboptimal yields and financial instability. This project aims to bridge this information gap by creating an AI-driven assistant that provides crucial guidance on crop selection, market prices, soil conditions, and pest control, thereby reducing risk and boosting income for farmers at the grassroots level.

✨ Key Features
AI-Powered Price Prediction: Trains a machine learning model on historical data to forecast future crop prices, providing a significant advantage over static data.

Data-Driven Profit Analysis: Calculates estimated revenue and net profit per hectare by synthesizing historical yield, AI-predicted prices, and cultivation costs.

Localized Crop Recommendations: Analyzes decades of district-level data to recommend the highest-yielding crops for a farmer's specific location.

Live Environmental Data: Integrates with real-time APIs to fetch current soil properties (pH, organic carbon) for any district in India.

Pest & Cost Advisory: Provides a knowledge base of common pest control measures and estimated cultivation costs for major crops.

Conversational Interface: A simple command-line interface allows farmers to ask questions in a natural way.

🏗️ System Architecture
The agent is built on a Retrieval-Augmented Generation (RAG) architecture to ensure all advice is grounded in factual, verifiable data.

Query & Intent Routing: A user's query is analyzed to determine its intent (e.g., "profit," "price," "soil"). The system then routes the query to the appropriate "tool" or function.

Data Retrieval & Prediction: The selected tool gathers the necessary information. This can involve:

Querying the historical dataset from IBM Cloud Object Storage.

Running an internal AI model to predict prices.

Calling an external API for live soil data.

Context Augmentation: The retrieved data (the "context") is combined with the user's original question to create a detailed prompt.

Response Generation: This augmented prompt is sent to the IBM Granite LLM, which generates a final, coherent, and easy-to-understand answer.

🛠️ Technology Stack
Backend: Python

AI & Machine Learning:

scikit-learn: For training the price prediction model.

pandas & numpy: For data manipulation and analysis.

Cloud & Data:

IBM Cloud Object Storage: For storing the core historical dataset.

IBM watsonx.ai: For accessing the Granite LLM (simulated in the current version).

ibm-boto3: The official SDK for interacting with IBM Cloud services.

APIs & Services:

geopy: For converting district names into geographic coordinates to fetch soil data.

requests: For making API calls to external services.

⚙️ Setup and Installation
Follow these steps to set up and run the project locally.

1. Clone the Repository
git clone https://github.com/your-username/ai-smart-farming-agent.git
cd ai-smart-farming-agent

2. Install Dependencies
It is recommended to use a virtual environment.

# Create and activate a virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`

# Install the required libraries
pip install pandas ibm_boto3 botocore requests geopy scikit-learn

3. Configure Credentials
This project requires credentials for IBM Cloud. For security, it's best to set these as environment variables.

IBM Cloud Credentials:

Find your API Key ID, Endpoint URL, and Bucket Name from your IBM Cloud Object Storage instance.

Set them in your terminal session:

# For Linux/macOS
export IBM_API_KEY_ID="your_api_key_id"
export IBM_ENDPOINT_URL="your_endpoint_url"
export IBM_BUCKET_NAME="your_bucket_name"

# For Windows (Command Prompt)
set IBM_API_KEY_ID="your_api_key_id"
set IBM_ENDPOINT_URL="your_endpoint_url"
set IBM_BUCKET_NAME="your_bucket_name"

You will need to update the Python script to read these environment variables instead of using hard-coded strings.

▶️ How to Run
Once the setup is complete, you can run the agent from the command line:

python main_script_name.py

The application will first load the data from IBM Cloud and train the AI models. It will then prompt you to enter your state and district to begin the interactive session.

💬 Usage Examples
Once the agent is running, you can ask questions like:

What crop is best for this season?

What is the predicted price for wheat?

Show me the profit prediction for rice.

What is the estimated cost to grow sugarcane?

What are the soil conditions here?

How to handle pests in wheat?

exit (to close the application)

📊 Data Source
The historical agricultural data used in this project is sourced from the International Crops Research Institute for the Semi-Arid Tropics (ICRISAT). This dataset provides the foundational knowledge for crop recommendations, yield analysis, and training our predictive models.

Source: ICRISAT Dataverse

🚀 Future Scope
Enhanced UI: Develop a mobile or web application for easier access.

Voice Interaction: Implement voice-to-text and text-to-speech in regional languages.

Advanced Models: Use more complex models (e.g., LSTM) for time-series forecasting.

Wider Data Integration: Incorporate live weather forecasts, satellite imagery, and government subsidy information.
