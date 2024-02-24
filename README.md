# Index
- [Description](#Description)
- [Project structure](#project-structure)
- [Instructions to run](#instructions-to-run)
- [Results](#Results)

# Description

This project uses recurrent neural network (RNN) models with LSTM layers to predict the number of bicycles available at Bicing Barcelona stations in future timeframes. An approach has been implemented where individual models are generated for each time interval. During testing, the day has been divided into 30-minute intervals, resulting in a total of 48 time slots and, consequently, the creation of 48 different models. This strategy facilitates the capture of specific patterns and trends for each moment of the day. The data used in this project were provided by Bicing Barcelona and contain detailed historical information about bicycle availability at each station at different time intervals.


# Project structure

`./data/raw/`: Files to process obtained from the official source [OpenData Ajuntament Barcelona](https://opendata-ajuntament.barcelona.cat/data/ca/dataset/estat-estacions-bicing). All the files from 2023 are here. For the most recent data, users should check online.

`./data/dataframes/`: Dataframes created to organize the data in a way that makes it easy to consume.

`./models/`: Contain folders where each one implements different prediction models.

`./models/analyze_models.ipynb`: Collect the predictions made by each of the models in a single location, and then analyze the results.

`./config.py`: Centralized configuration file.


# Instructions to run

1. Put all data files into the directory ./data/raw/.

2. Configure the config.py file

3. Process the data, train all models, and execute testing for each one using the following script from root:

```
python .\data\generate_station_csv.py
python .\data\resample_csv.py
python .\data\split_train_test.py
python .\models\dummy\model_dummy.py
python .\models\avg\model_avg.py
python .\models\rnn\model_rnn.py
python .\models\rnn_by_time\model_rnn_by_time.py
```

4. Analyze the results from the Jupyter Notebook named 'analyze_models'.

# Results
