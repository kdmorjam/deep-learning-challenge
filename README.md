# deep-learning-challenge

# Report

1.	Overview:

    The purpose of this analysis is to determine what factors affaected the outcome of whether or not 
    funding received was used effectively.

2.	Results: 

    •	Data Preprocessing

        o	What variable(s) are the target(s) for your model?
            The target variable in this analysis was "IS_SUCCESSFUL"

        o	What variable(s) are the features for your model?
            The following variable were used  as features : APPLICATION_TYPE, AFFILIATION, 
            CLASSIFICATION, USE_CASE, ORGANIZATION, INCOME_AMT and ASK_AMT.

        o	What variable(s) should be removed from the input data because they are neither 
            targets nor features?
            The STATUS and SPECIAL_CONSIDERATIONS variables should be removed. Only five (5) orgabizations had an
            inactive status which was approximately 0.01% of the dataset. Additionally, there were only 27 applications
            out of 34,299 with special considerations. This amounted to approximately 0.08% of the dataset. Hence both
            there were not significant features for the analysis. Please see results from value_counts() below:

            N    34272
            Y       27
            Name: SPECIAL_CONSIDERATIONS, dtype: int64

            1    34294
            0        5
            Name: STATUS, dtype: int64

    •	Compiling, Training, and Evaluating the Model

        o	How many neurons, layers, and activation functions did you select for your neural network model, and why?
            Three layers were used for the model. Adding additional layers did not improve the model's performance.
                1. For the first layer, relu was selected and tested with 70, 80 and 90 neurons. Performance went 
                    down with both 70 & 100 neurons, hence 80 neurons was elected. 
                2. For the second layer, relu was also used. This second layer was tested with tanh, selu and elu 
                    activation functions. 
                3. The third layer used the sigmoid activation function with 1 neuron.

        o	Were you able to achieve the target model performance?
            After testing various optimizations techniques (dropping columns, adding layers, adding neurons, reducing epochs), the accuracy rate averaged around 73%.

        o	What steps did you take in your attempts to increase model performance?
            Result of the original model before optimization:
            322/322 - 1s - loss: 0.5742 - accuracy: 0.7286 - 555ms/epoch - 2ms/step
            Loss: 0.5742040276527405, Accuracy: 0.7285714149475098

            The following steps were taken to increase model performance:
                1. Dropping additional columns: the initial model dropped the EIN and NAME columns. The STATUS and 
                SPECIAL CONSIDERATION columns were also dropped. This increased the accuracy from 72.8% to 73.02%
                Result from model.evaluate:
                322/322 - 1s - loss: 0.5605 - accuracy: 0.7302 - 585ms/epoch - 2ms/step
                Loss: 0.5604860186576843, Accuracy: 0.730223536491394

                2. Changing activation function: the change was applied to the second layer. The reult shown was
                for the elu activation. Tanh gave the lowest accuracy (72.79%).
                Result from model.evaluate:
                322/322 - 1s - loss: 0.5586 - accuracy: 0.7314 - 633ms/epoch - 2ms/step
                Loss: 0.5585817694664001, Accuracy: 0.7313897013664246

                3. Adding more neurons
                Result from model.evaluate:
                322/322 - 0s - loss: 0.5664 - accuracy: 0.7280 - 495ms/epoch - 2ms/step
                Loss: 0.5663771629333496, Accuracy: 0.7279883623123169

                4. Adding more layers - adding a fourth layer reduced performance

                5. Increasing & reducing epochs: Reducing epochs to 90 and increasing to 110 reduced 
                performance.

                5. Combining dropping additional comns and adding more neurons: this combination gave the 
                best improvement.
                Result from model.evaluate:
                322/322 - 1s - loss: 0.5572 - accuracy: 0.7320 - 578ms/epoch - 2ms/step
                Loss: 0.5572029948234558, Accuracy: 0.7319728136062622

3.	Summary: 
    The optimized model had 4 columns removed (EIN, NAME, STATUS & SPECIAL_CONSIDERATION), with 3 layers. 
    Layers 1 & 2 used relu with 80 and 60 neurons respectively. Layer 3 used sigmoid activations with 1 nueron. 
