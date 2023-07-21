# deep-learning-challenge

# Report

1.	Overview of the analysis: 
    The purpose of this analysis is to determine what factors affaected the outcome of whether or not 
    funding received was used effectively.

2.	Results: 
    Using bulleted lists and images to support your answers, address the following questions:
    •	Data Preprocessing

        o	What variable(s) are the target(s) for your model?
            The target variable in this analysis was "IS_SUCCESSFUL"

        o	What variable(s) are the features for your model?
            The following variable were used  as features : APPLICATION_TYPE, AFFILIATION, CLASSIFICATION,
            USE_CASE, ORGANIZATION, INCOME_AMT and ASK_AMT.

        o	What variable(s) should be removed from the input data because they are neither targets nor features?
            The STATUS and SPECIAL_CONSIDERATIONS variables should be removed. Only five (5) orgabizations had an
            inactive status which was approximately 0.01% of the dataset. Additionally, there were only 27 applications
            out of 34,299 with special considerations. This amounted to approximately 0.08% of the dataset. Hence both there were not significant features for the analysis. 

            N    34272
            Y       27
            Name: SPECIAL_CONSIDERATIONS, dtype: int64

            1    34294
            0        5
            Name: STATUS, dtype: int64


        •	Compiling, Training, and Evaluating the Model

        o	How many neurons, layers, and activation functions did you select for your neural network model, and why?
            Three layers were sued for the model. For the first  

        o	Were you able to achieve the target model performance?

        o	What steps did you take in your attempts to increase model performance?

3.	Summary: 
    Summarize the overall results of the deep learning model. Include a recommendation for how a different model could solve this classification problem, and then explain your recommendation.
