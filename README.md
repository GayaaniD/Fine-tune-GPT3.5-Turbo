# Fine-Tuning GPT-3.5 Turbo with Bank Customer Service Data

This project involves fine-tuning the GPT-3.5 Turbo model with a dataset of **bank customer service questions and answers**. The aim is to create a specialized model capable of handling customer service inquiries effectively.

The goal of this project is to enhance the performance of the GPT-3.5 Turbo model for bank customer service tasks by fine-tuning it with a specific dataset of questions and answers.

## Dataset
The dataset used for this project was sourced from the Hugging Face website. It contains a collection of customer service questions and their corresponding answers.

## Preprocessing
The data was preprocessed into a standard conversational format suitable for the GPT-3.5 model. The following code was used to structure the data:
```
ds_formatted = [
    {
        "messages": [
            {"role": "system", "content": Prompt},
            {"role": "user", "content": question},
            {"role": "assistant", "content": response}
        ]
    }
    for item in data
]
```

## Data Splitting
The dataset was divided into two parts:

  - Training Set: 70% of the data
  - Testing Set: 30% of the data
The data was saved in JSONL format.

## Fine-Tuning
To ensure security, an API key from OpenAI was obtained and saved in a .env file. The training and testing data were uploaded, and IDs for both sets were obtained. The following code was used to initiate the fine-tuning process:
```
response = client.fine_tuning.jobs.create(
    training_file=train_id,
    validation_file=test_id,
    model='gpt-3.5-turbo'
)
```

The fine-tuning process took some time to complete. Afterward, the ID for the fine-tuned model was received, and the fully fine-tuned model was used for inference.

## Inference
The fine-tuned model was employed in a graphical interface to handle customer service inquiries effectively.

## Usage
### Clone the Repository:
```
git clone <repository-url>
cd <repository-directory>
```

### Install Dependencies:
```
pip install -r requirements.txt
```

### Set Up Environment Variables:
Create a .env file in the root directory and add your OpenAI API key:
```
OPENAI_API_KEY=your_openai_api_key
```

### Preprocess the Data:
Ensure your dataset is in the correct format and preprocess it as shown above.

### Split the Data:
Split the dataset into training (70%) and testing (30%) sets and save them in JSONL format.

### Fine-Tune the Model:
Upload the training and testing data, obtain the file IDs, and use the provided code to start the fine-tuning process.

### Inference:
Use the fine-tuned model in your application to handle customer service inquiries.
