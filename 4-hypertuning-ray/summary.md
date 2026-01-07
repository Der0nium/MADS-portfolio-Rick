# Summary week 4
1. Setup and Strategy
I set up a custom Convolutional Neural Network (CNN) in collaboration with Gemini. For the data setup, I chose not to use Batch Normalization initially, as my hypothesis was that on a small subset (5,000 images), it might introduce noise rather than stability.

I set up the model with a dynamic architecture where Ray Tune controls the depth (1-3 blocks) and width. Every model was trained for 10 epochs.

2. The Analysis Problem
Initially, the results were difficult to analyze because Ray Tune outputs a massive amount of raw log data in the terminal. It was hard to spot patterns just by scrolling through text.

Therefore, I worked with Gemini to implement a custom visualization script (visualize.py). This script parses the JSON results from disk and aggregates them into a Pandas DataFrame. By using the dataframe, it became possible to visualize interactions (Parallel Coordinates & Heatmaps) and identify exactly where the model performed best.

Below is the visualization of the hyperparameter flow from the session:

<img width="700" height="500" alt="1_parallel_coords" src="https://github.com/user-attachments/assets/2198e874-d5e0-4131-a333-317615fe357b" />

3. Iteration and Improvements
Using the dataframe analysis, I noticed clear patterns:

Depth matters: Models with only 1 convolutional layer consistently failed (bottom lines in the chart).

Optimizer: The Adam optimizer consistently beat SGD for these short 10-epoch runs.

Regularization: Changes in dropout rate had minor effects, but a "Goldilocks" zone around 0.2 seemed optimal.

I refined the search space to focus on these promising areas—pruning the 1-layer models and narrowing the learning rate range.

4. Results: Custom Model Ceiling
After recovering the data from 18 successful trials, the best custom configuration was identified:

Trial ID: ad7f4_00017

Accuracy: 55.60%

Config: 3 Layers, Base Filters 32, Adam Optimizer, Learning Rate ~0.0027.

Below is the correlation heatmap showing how depth (num_conv_layers) was the strongest predictor of success:

<img width="1000" height="800" alt="2_correlation_heatmap" src="https://github.com/user-attachments/assets/6a100395-39f6-4079-9569-507992875886" />

I also have a scatterplot to showcase the randomness in LR vs Accuracy based on conv_layers.

<img width="1000" height="600" alt="3_interaction" src="https://github.com/user-attachments/assets/64151593-0f1c-4f15-a394-f53af037bb68" />

5. Comparison: The Transfer Learning Gap
While my custom model achieved 55.6% (a strong result for training from scratch on a small subset), I compared this to a classmate's approach using Transfer Learning (using a pre-trained ResNet/VGG).

My Custom Model: ~55% Accuracy

Classmate's Transfer Learning: ~96% Accuracy

Conclusion: Training a CNN from scratch on 5,000 images hits a performance ceiling because the model has to learn basic feature extractors (edges, textures) from a limited dataset. The "Transfer Learning" approach jumps to 96% because it skips this step, borrowing feature extractors learned from millions of ImageNet photos.

Here are the [instructions](./instructions.md) and here is a script to start [hypertune.py](./hypertune.py)

[Go back to Homepage](../README.md)
