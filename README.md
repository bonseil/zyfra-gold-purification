# zyfra-gold-purification

## Project description

Zyfra <a href='https://www.zyfra.com/' >(www.zyfra.com)</a>  is big company working to improve the efficiency and safety of the mining, oil & gas, chemical and engineering industries. 
In this project we need to develop a model that must predict the amount of gold recovered from gold ore after the purification process. 
We need to deal with the raw data that contains many outliers and missing values as the data depends on the reliability of the machinery that functions in difficut conditions at mining sites.
The model will help to maximize the recovery of gold from the mining process and eliminate unprofitable parameters.

## Steps in analysis

    Opening the data file and studing the general information
    Preparing the data
    Analyzing the data
    Dealing with missing data and outliers
    Scaling the data
    Building baseline models
    Selecting features for our ML models
    Checking the evolution of the feed after each purification stage
      Concentrations of metals
      Feed particle size distributions
      Total concentrations of all substances
    Training Machine Learning Models
      Decision Tree Regressor
      Linear Regression
      Random Forest Regressor
      Lasso Regression
      Ridge Regression
    General conclusion

## Data description

### Technological process

    - Rougher feed — raw material
    - Rougher additions (or reagent additions) — flotation reagents: Xanthate, Sulphate, Depressant
        - Xanthate — promoter or flotation activator;
        - Sulphate — sodium sulphide for this particular process;
        - Depressant — sodium silicate.
    - Rougher process — flotation
    - Rougher tails — product residues
    - Float banks — flotation unit
    - Cleaner process — purification
    - Rougher Au — rougher gold concentrate
    - Final Au — final gold concentrate

### Parameters of stages

    - air amount — volume of air
    - fluid levels
    - feed size — feed particle size
    *feed rate*
    
### Feature naming
Name of the features:
[stage].[parameter_type].[parameter_name]
Example: rougher.input.feed_ag
Possible values for [stage]:

    _rougher_ — flotation
    _primary_cleaner_ — primary purification
    _secondary_cleaner_ — secondary purification
    _final_ — final characteristics

Possible values for [parameter_type]:

    _input_ — raw material parameters
    _output_ — product parameters
    _state_ — parameters characterizing the current state of the stage
    _calculation_ — calculation characteristics
    

### Recovery calculation
We use the following formula to simulate the process of recovering gold from gold ore.
![Recovery Formula](https://pictures.s3.yandex.net/resources/Recovery_1576238822_1589899219.jpg)
where:

    C — share of gold in the concentrate right after flotation (for finding the rougher concentrate recovery)/after purification (for finding the final concentrate recovery)
    F — share of gold in the feed before flotation (for finding the rougher concentrate recovery)/in the concentrate right after flotation (for finding the final concentrate recovery)
    T — share of gold in the rougher tails right after flotation (for finding the rougher concentrate recov
    
### Evaluation metric
We use symmetric Mean Absolute Percentage Error (sMAPE) to evaluate the result.
![sMAPE](https://pictures.s3.yandex.net/resources/smape_1576238825_1589899257.jpg)

We apply this on two values:

    rougher concentrate recovery rougher.output.recovery
    final concentrate recovery final.output.recovery

The final metric includes these two:
![Final sMAPE](https://https://pictures.s3.yandex.net/resources/_smape_1589899561.jpg)
