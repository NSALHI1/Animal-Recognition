# Animal Recognition Project

Welcome to the Animal Recognition Project! This application utilizes advanced AI models to recognize animals in images, generate descriptive captions, provide insightful information, translate text into Arabic, and produce audio narrations of the captions. It leverages the power of Hugging Face’s Transformers library and offers a user-friendly interface through Gradio.

## Project Objectives

The main goals of this project are to:

- Identify animals from user-uploaded images.
- Generate descriptive captions about the identified animals.
- Provide detailed insights based on those animals.
- Translate the generated text into Arabic.
- Create audio narrations of the captions for an immersive experience.

## Core Components

### AI Models Utilized

- **Translation Model**: The project uses the `Helsinki-NLP/opus-mt-en-ar` model for translating English text into Arabic.
  
- **Image Captioning**: The BLIP model (`Salesforce/blip-image-captioning-base`) generates captions by analyzing the uploaded images.

- **Question-Answering**: The `deepset/roberta-base-squad2` model is employed to provide relevant information based on a predefined context of animal knowledge.

- **Text-to-Speech**: The `kakao-enterprise/vits-ljs` model converts text captions into audio.

### Context for Animal Insights

A curated set of descriptions covering various animals (like tigers, elephants, and lions) serves as a knowledge base for the question-answering model, allowing it to retrieve relevant information effectively.

### Recognizable Animals

A list of well-known animal names helps the system accurately identify animals mentioned in generated captions.

## Key Features

- **Image Upload**: Users can upload images of animals for recognition.
- **Caption Generation**: The system automatically creates a descriptive caption for the uploaded image.
- **Animal Information**: Detailed insights about the identified animal are provided.
- **Audio Output**: Captions are converted into audio format for enhanced accessibility.
- **Translation**: Captions and insights are translated into Arabic.

## Limitations

- The accuracy of animal recognition may vary based on the quality of the uploaded image.
- Translations might not always capture the full nuances of the original English text.
- Text generation models may stop unexpectedly, leading to incomplete sentences and unfinished thoughts.
- Text generation models are heavily reliant on the context provided.

## Functionality Overview

  ### Extracting Animal Names

The `extract_animal_from_caption(caption)` function identifies the animal mentioned in the generated caption.

  ### Generating Audio

The `generate_audio(text)` function converts the provided text into audio and saves it as a WAV file.

  ### Main Recognition Process

The `recognize_animal_and_get_info(image)` function handles the image recognition process. It performs the following tasks:

1. Generates a caption using the BLIP model.
2. Extracts the animal name from the caption.
3. Retrieves relevant information using the question-answering model.
4. Translates the caption and information into Arabic.
5. Produces audio from the caption.

## Gradio Interface Design

The Gradio interface consists of two main tabs:

1. **Generated Results**:
   - Displays the generated caption, animal insights, and audio narration.
  
2. **Translations**:
   - Shows the translated caption and animal insights in Arabic.
## Justification for Model Choices

### Image Captioning
- **Model Used**: **BLIP (Salesforce/blip-image-captioning-base)**
- **Reason for Selection**: BLIP is an exceptional model when it comes to describing images. It’s designed to understand visual content deeply and generate captions that make sense. This makes it perfect for the project, as it ensures users get meaningful descriptions of the animals they upload.

### Question Answering
- **Model Used**: **deepset/roberta-base-squad2**
- **Reason for Selection**: This model is great at digging into information and providing quick answers. It’s trained on a rich dataset, making it reliable for extracting insights about animals. The goal is to ensure users receive accurate and relevant information, and this model delivers just that. 
  - **Considerations**: Although it excels in many areas, the model may struggle with highly specific or nuanced questions that fall outside the training data. Additionally, it may provide incomplete answers if the context is not sufficiently detailed.

### Text-to-Speech
- **Model Used**: **kakao-enterprise/vits-ljs**
- **Reason for Selection**: When it comes to turning text into speech, this model stands out for its natural and clear audio. Listening to captions can enhance the experience, making it more engaging and accessible for everyone.

### Translation
- **Model Used**: **Helsinki-NLP/opus-mt-en-ar**
- **Reason for Selection**: This translation model is highly regarded for its ability to accurately translate English text into Arabic. Reaching Arabic-speaking users is essential, and having reliable translations helps bridge language barriers and enrich the overall experience.
  - **Considerations**: Although it provides reliable translations, it may not always capture the full nuances or cultural references of the original text, leading to potential misunderstandings. The quality of translation can also vary depending on the complexity of the sentences.

### Packages
- Transformers: For using pre-trained models for tasks like translation, image captioning, and text-to-speech.
- SciPy: For handling audio file saving and manipulation.
- Torch: A deep learning framework that supports the models used in the project.
- Gradio: To create a user-friendly interface that allows users to interact with the application.
- Sentencepiece: For tokenization in various language processing tasks.
- Timm: For vision-related models, especially in image classification.
- Inflect: For converting numbers to words and pluralization.
- Phonemizer: For phoneme conversion from text.
- Py-espeak-ng: For text-to-speech capabilities.
- Soundfile: For reading and writing audio files.
  
## Example Interaction

1. **Input**: An image of a tiger.
2. **Output**:
   - **Caption**: "A tiger in the wild, showcasing its majestic stripes."
   - **Animal Insight**: "Tigers are the largest species among the Felidae..."
   - **Translated Caption**: "نمر في البرية، يظهر خطوطه المهيبة."
   - **Translated Animal Insight**: "النمور هي أكبر الأنواع بين السنوريات..."
   - **Audio**: An audio file narrating the caption.

## URLs

- **Hugging Face Space**: [Hugging Face](https://huggingface.co/spaces/Norahsal/Animals)
- **Google Colab**:[Google Colab](https://colab.research.google.com/drive/1zRrGMN3FJqCe0heSqwHcX197FdUuQGSj?usp=sharing)
