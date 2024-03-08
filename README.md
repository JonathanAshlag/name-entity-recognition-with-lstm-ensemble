# name-entity-recognition-with-lstm-centered-ensemble

This project was part of my assignments in an NLP course I took during my M.Sc. 
The mission was to build a named entity tagging model with the objective of getting the highest F1 score.
The initial model was a 3-layer LSTM network which achieved good scores with a balanced recall-precision trade-off.
At some point, we experimented with a simple KNN model which had surprisingly good results.
The F1 score was mediocre, but we found an interesting observation: 
the precision score was much better than our LSTM network, and in contrast, the recall was way below.
Inspired by our observation, our final model was an ensemble of the two. 
During inference, we collected predictions from both models and applied the following decision rule:
if KNN_prediction == 1 and LSTM_prediction == 0:
  then final prediction = KNN_prediction
else,
  final prediction = LSTM_prediction.
After some slight tuning, the final ensemble model showed improved results over the LSTM network
