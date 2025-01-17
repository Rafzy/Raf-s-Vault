
Classification -> use correlation by weights


Preprocessing classification training
- Remove any non-numeric things in numerical categories (Use replace)
- Create the Risk into a label (use set role)
- Create the id into id (use set role)
- Drop the region attribute for some reason
- Change the categorical data into numerical (Use mapping or nominal to numerical)
- Use parse numbers to convert them into proper numbers
- Normalize the values
- Use weight by correlation (No need to change parameters)
- Select by weight (We can try adjusting the parameters, make sure it connects weight to weight, example to example from weight by correlation)
- We'll use validation to train the mode
- Inside validation, we'll use the algorithms we want to try out on the left side
- On the right side, we'll put Apply model, and performance after
- We'll connect the model and test data to the apply model
- When testing, we don't need to use validation anymore, we can create a new process altogether, copy everything except validation, and just put in the best model
- then, copy everything up until normalization for the testing data
- drag the normalize to the uni parameter in apply mod from the testing preprocess, and drag the model parameter from knn to the apply model from the training side
- after apply model, we can put the map function to return the risk as low and high from 0 and 1




KNN: 86,04%
Naive Bayes 83.83
Decision Tree: 86.08%
