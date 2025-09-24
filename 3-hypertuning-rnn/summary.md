# Summary week 3
For my first step I altered the hyper parameters for the Grumodel.
    config = ModelConfig(
        input_size=3,
        hidden_size= 128, #3200 sequences
        num_layers=5, #I altered the depth from 3 to 5
        output_size=20, #20 gestures --> 20 output classes
        dropout=0.1,
    )

Then I ran 8 epochs, and got a 92% accuracy.

Seeing I already hit target I then added a LSTMmodel class to be used, by copying over the code from the Grumodel.
I used the same settings for the hyper parameters... but only got 56% accuracy after 8 epochs.

We were also tasked to add Conv1D layers and see what this did. Honestly I don't feel capable of doing this without a code generator having my back. I would really like to see how one adds these Conv1D layers.

After adding Conv1D the cheap way, with LSTM the result after 8 epochs is 67%.

I will now try the Grumodel with Conv1D, same settings.
After 8 epochs it provides: 94% accuracy. (even showing 95% at 7 epochs)

Find the [notebook](./notebook.ipynb) and the [instructions](./instructions.md)

[Go back to Homepage](../README.md)
