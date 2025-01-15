# RNNs_lyrics_generation

This deep-learning project implements a recurrent neural network (RNN) for generating song lyrics based on provided melodies and a starting word. The project utilizes LSTM networks, Word2Vec embeddings, and the Pretty_Midi library for melody analysis.

## Project Overview

The primary objective of this project is to predict the next word of song lyrics given the previous words and the accompanying melody. The model leverages both textual and melodic features to generate coherent and contextually aligned lyrics.

Key features include:
- Long Short-Term Memory (LSTM) architecture for handling long-term dependencies in lyrics.
- Integration of melody features from MIDI files with text embeddings.
- Implementation of two melody integration methods, balancing simplicity and richness.

## Dataset

The dataset comprises 600 songs with paired lyrics and melody data, split into:
- **Training Set:** 593 songs (after cleaning)
- **Test Set:** 5 songs

### Data Sources:
- **Lyrics:** CSV file containing song names, artists, and lyrics.
- **Melody:** MIDI files containing features such as pitch, velocity, instrument type, and timing information.

### Preprocessing:
- Text cleaned, tokenized, and converted into sequences using Word2Vec embeddings.
- Melody features extracted and normalized using global statistics for consistency across songs.
- Padding applied to ensure uniform input lengths.

## Model Architecture

The RNN model is based on a bidirectional LSTM architecture, which includes:
1. **Embedding Layer:** Word2Vec embeddings (300 dimensions) combined with melody features.
2. **Two Bidirectional LSTM Layers:** Hidden size of 256 units for capturing context in both directions.
3. **Dropout Regularization:** To reduce overfitting.
4. **Batch Normalization:** Applied to input embeddings for stabilized learning.
5. **Output Layer:** Fully connected layer projecting LSTM outputs to the vocabulary size.

## Melody Integration Methods

1. **Simplified Features (Method 2):**
   - Input: Word embeddings + 6 melody features (306 dimensions).
   - Features: Pitch range, velocity, instrument presence, duration, number of instruments, drum presence.

2. **Detailed Features (Method 3):**
   - Input: Word embeddings + 128 melody features (428 dimensions).
   - Features: Piano roll representation, including note pitch, velocity, duration, density, and timing information.

## Training and Hyperparameters

- **Optimizer:** Adam with an initial learning rate of 1E-3.
- **Loss Function:** Cross-Entropy Loss.
- **Batch Size:** 1 (song-level processing).
- **Dropout Rates:** Tested values of 0.3, 0.4, and 0.5.
- **Validation Split:** 90% train / 10% validation.
- **Early Stopping:** Training stops after 3 epochs with no validation loss improvement.

## Results and Insights

### Performance Metrics:
- **Method 2:**
  - Validation Loss: 0.8854
  - Dropout: 0.5
- **Method 3:**
  - Validation Loss: 0.8827
  - Dropout: 0.3

### Observations:
- **Method 3** demonstrated superior performance due to richer melody features.
- Initial words influenced the thematic tone of generated lyrics.
- Melody integration enhanced the contextual alignment of lyrics.

## Contributors

- **Adi Maman** - [Email](mailto:adimaman22@gmail.com)
- **Eran Fishbein** - [Email](mailto:eranfish76@gmail.com)

For detailed information about the implementation, refer to the [project report](./RNNs%20lyrics%20generation%20-%20project%20report.pdf).

