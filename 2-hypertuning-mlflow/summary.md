# Summary week 2
Having learned from week 1, my first step is to up the number of epochs from 3 to 10.
Right now with 3 epochs the accuracy goes from 52% to 71%.

Finding: So my first finding is that the model was still trained at 71% and continued from then on.
So in a sense it has now underwhent 13 epochs if my observation is right, and the accuracy is now at 84%.

I will also increase the depth from the current number of 4, I tried numerous settings 1,2,3,4,5,6,7,9.
At 9 it gave an error so I knew that it whent beyond the point of having enough search space for my kernel.
So I tried 7, still the same thing an error.
Then I tried 6, and the difference between y and yhat increased so I tried lower as 4, namely 3 and it was also a bigger difference between y and yhat compared to 4.
I tried 1,2 and 5 as well, just to make sure. But 4 still kept being the best result.

Then I increased the hidden from 32 to 64, doubling the amount of features for my 3x3 kernels, I expect my model to become slower, perhaps half as slow. But also more accurate.
Interestingly it did slow down, but the result also got worse, which is not what I expected, so more hidden features does not mean better results.
Perhaps if we add regularization like drop-out the results will increase.

After adding drop-out to both the CNN layers and the dense layers, I have increased the models performance to 86%.
For CNN i whent with the 0.2 drop-out rate, and for the dense I whent with 0.3

I also altered the width for the dense NN, I doubled the values 128 for unit1 to 256 and 64 to 128 for unit2.
Expecting better results, I did not see any improvement.

Lets add normalization, I expect the model to increase in speed not per se in accuracy.
Indeed it became a little faster, but I lost 2% in accuracy.

I decided to add dynamic filters based on the CNN layer. 
64, 128, 256
I expect higher accuracy now.
Unfortunatly not much did change.

Also I have setup the epochs to be doubled from 10 to 20.
I now have an accuracy of 89%.

lets change the hidden values of 64, 128, 256 to 128, 256, 512
See if we see a more robust CNN setup. Higher accuracy.

I adjusted the dropout in my dense NN, from 0.3 to 0.1, now I have an accuracy of 90%.

Learning rate --> Adam is used, how do we alter this? Customize this?

Find the [instructions](./instructions.md)

[Go back to Homepage](../README.md
