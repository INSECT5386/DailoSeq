16688/16688 ━━━━━━━━━━━━━━━━━━━━ 14589s 874ms/step - accuracy: 0.8129 - loss: 1.8762 - val_accuracy: 0.8281 - val_loss: 1.6310

| Layer (type)          | Output Shape        | Param #      | Connected to       |
|----------------------|-------------------|-------------|------------------|
| input_layer (InputLayer) | (None, 25)       | 0           | -                |
| input_layer_1 (InputLayer) | (None, 36)     | 0           | -                |
| embedding (Embedding) | (None, 25, 80)    | 18,469,280  | input_layer[0][0] |
| embedding_1 (Embedding) | (None, 36, 80)  | 22,985,920  | input_layer_1[0][0] |
| encoder_lstm_1 (LSTM) | [(None, 25, 80), (None, 80), (None, 80)] | 51,520 | embedding[0][0] |
| decoder_lstm_1 (LSTM) | [(None, 36, 80), (None, 80), (None, 80)] | 51,520 | embedding_1[0][0], encoder_lstm_1[0][1], encoder_lstm_1[0][2] |
| attention (Attention) | (None, 36, 80)    | 0           | decoder_lstm_1[0][0], encoder_lstm_1[0][0] |
| concatenate (Concatenate) | (None, 36, 160) | 0           | decoder_lstm_1[0][0], attention[0][0] |
| time_distributed (TimeDistributed) | (None, 36, 287324) | 46,259,164 | concatenate[0][0] |
