# 📜 Story Generation

Welcome to the **Story Generation Model** project! This repository contains a PyTorch implementation of a text generation model designed to create captivating stories based on a seed text. 🌌 The model supports multiple RNN architectures like LSTM, GRU, RNN, and BiLSTM to give flexibility in capturing complex sequences. 📖✨

## 🚀 Project Overview

This project uses Recurrent Neural Networks (RNNs) to generate text sequences, building on word-by-word predictions. It can produce new stories from scratch or continue from an input sentence. Here's what makes it exciting:
- **Configurable RNN architecture**: Choose from RNN, LSTM, GRU, or BiLSTM for your model.
- **Simple Dataset Preparation**: Uses a custom dataset class to create input-target pairs for training.
- **Word Embeddings**: Utilizes embeddings to convert words into dense vectors, capturing their semantic meanings.

## 📂 Project Structure

Here's an overview of the main components:

- **`Config`**: Contains hyperparameters like `EMBEDDING_DIM`, `HIDDEN_DIM`, and `SEQ_LENGTH`.
- **`tokenize_text`**: Prepares text by tokenizing and converting it to lowercase.
- **`StoryDataset`**: Handles dataset creation for training, organizing text into sequences.
- **`TextGenerationModel`**: Defines the text generation model, configurable with RNN, LSTM, GRU, or BiLSTM.
- **`train_model`**: Trains the model using Cross-Entropy Loss and Adam optimizer.
- **`generate_text`**: Generates a new story based on the trained model and seed text.

## 🛠 Configuration

You can adjust the following settings in the `Config` class to tune your model:

```python
class Config:
    EMBEDDING_DIM = 256        # Dimension of embeddings
    HIDDEN_DIM = 512           # Dimension of RNN hidden layer
    NUM_LAYERS = 4             # Number of RNN layers
    SEQ_LENGTH = 10            # Sequence length for training
    BATCH_SIZE = 32            # Batch size
    EPOCHS = 25                # Training epochs
    LEARNING_RATE = 0.001      # Learning rate
    UNK_TOKEN = "<UNK>"        # Token for unknown words
```

## 💻 Usage

1. **Install Dependencies**  
   This project requires `torch`, so make sure you have PyTorch installed:
   ```bash
   pip install torch
   ```

2. **Run the Main Script**  
   To train the model and generate text, run:
   ```bash
   python story_gen.py
   ```

   - You can modify the story in the script or set `model_type` to choose from available architectures (`RNN`, `LSTM`, `GRU`, `BiLSTM`).

3. **Model Training**  
   The model will start training, showing loss updates every 10 batches. After training, the model is saved to `text_generation_<model_type>.pth`.

4. **Text Generation**  
   You can generate text by modifying `start_text` and `length` in the `run_inference` function. Experiment with different seed texts!

## 📋 Example

Here’s how to generate a new story:

```python
start_text = "Once upon a time"
generated_story = generate_text(model, start_text, length=50, word2idx=word2idx, idx2word=idx2word)
print(generated_story)
```

## 🧩 Key Functions

### `tokenize_text(text)`
Tokenizes the input text for processing. Uses space-based splitting and converts text to lowercase.

### `prepare_dataset(story)`
Prepares the dataset by creating vocabulary, mappings, and DataLoader for model training.

### `train_model(model, dataloader, epochs, lr)`
Trains the model on the provided DataLoader, utilizing Cross-Entropy Loss and Adam optimizer.

### `generate_text(model, start_text, length, word2idx, idx2word)`
Generates text based on a seed sentence and specified length.

### `load_model(vocab_size, model_type)`
Loads a previously trained model for further training or inference.

## 📈 Model Types

This model supports four RNN variants:
1. **RNN**: Simple recurrent neural network.
2. **LSTM**: Long Short-Term Memory, ideal for longer sequences.
3. **GRU**: Gated Recurrent Unit, efficient in terms of memory and computation.
4. **BiLSTM**: Bidirectional LSTM, captures context from both past and future.

## 📝 Notes
- **Vocabulary Expansion**: Add new words to `UNK_TOKEN` if encountered during inference.
- **Greedy Decoding**: By default, generates the next word based on the highest probability, which may result in repetitive text.

## 📜 License
This project is open-source and free to use.

Enjoy generating stories! 🎉
