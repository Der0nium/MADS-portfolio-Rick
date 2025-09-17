# Summary week 1
When tweaking the parameters for the NN, I tried out numerous things, I tried increasing the depth and width of the NN. Expecting better results in accuracy, it seemed to work but not astoundingly. I tried numerous depths and widts, I even found out going beyond 4 layers of depth resulted in no change with my other settings, so I reverted back from 5 to 4 in depth.

I used a remark of the teacher to decide the width of my NN, I halved down from the starting value 784 to 382, then to 191, then to 80, then to 40 and then to 20 and then to 10, which is the same number as the amount of classes. If you count this correctly it is 6 steps at the moment so I consolidated the steps into 256, 128, 64, 32 and finally into the num of classes (10).

I also tweaked with the amount of epochs, which greatly effected the performance, I whent all the way up to 87% I believe when using 10 epochs. I noticed the model getting stuck in local minima at certain points but pulling himself out and reaching a lower minima.

I also changed the step size, but I was unsure what effect this had, in fact I would love to revisit this topic during class.





Find the [notebook](./notebook.ipynb) and the [instructions](./instructions.md)

[Go back to Homepage](../README.md)
