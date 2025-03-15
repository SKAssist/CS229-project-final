# Fine-Tuning MusicGen for Composer Style Transfer: Leveraging Style Embeddings for Conditioned Music Generation

Generating music that convincingly mimics the style of a specific composer presents a unique challenge in machine learning. While transformer-based models like MusicGen can generate coherent music, they often struggle to capture the subtle stylistic traits that define individual classical composers. Achieving accurate composer style transfer was particularly interesting to both of us, as we are a team composed of a classical pianist and a classical vocalist.

Our primary goal is to enable style transfer based on a prompt such as “Convert this music to Chopin’s style.” For instance, given a one-minute audio recording of Bach’s music as input, our fine-tuned model aims to generate a new piece that reflects Chopin’s musical characteristics.

In our project, we achieved three key advancements:

- **Style Encoder**: We trained a style encoder using contrastive loss to produce embeddings that cluster audio samples from the same composer.
  
- **Fine-Tuning**: We fine-tuned MusicGen using parameter-efficient fine-tuning (PEFT) to integrate style embeddings and align generated audio with a target composer’s style by minimizing the mean squared error (MSE) between the generated audio’s embedding and the target composer’s mean embedding.

- **Composer Classifier**: We developed a classifier using transfer learning with the MusicNet dataset that predicts the composer of a one-minute audio sample with 92% validation accuracy, which we used to evaluate the generated music’s alignment with the intended style.

To further evaluate our model’s consistency, we employed a cycle consistency evaluation that reconstructs music through Composer A → Composer B → Composer A and measures similarity using Frechet Audio Distance (FAD).
