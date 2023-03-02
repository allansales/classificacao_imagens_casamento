# Classificacao de imagens do casamento

O objetivo deste projeto é avaliar o desempenho de diferentes abordagens (i.e., treinar rede convolucional do zero ou usar transfer learning) para classificar a presença de meu rosto e/ou o da minha esposa, de frente ou de lado, nas fotos do nosso casamento.

## Treinamento de rede convolucional
Treinamos uma rede convolucional, com Keras, para fazer a classificação. O seu resultado tende a dar uma acurácia de aproximadamente 80%, precisão de 90% e recall de 95%.

Uma próxima abordagem poderia se beneficiar de balanceamento de classes para melhorar ainda mais os valores da classificação. Fotos em que eu e ela aparecemos são bem mais comuns que fotos que apenas eu ou apenas ela aparecem.

Alguns vieses das fotos tambem podem ter influencia na classificação. Por exemplo, em fotos com pose geralmente eu visto terno e apareço à esqueda da foto. Da mesma maneira, o pai de minha esposa aparece à direita da foto e em poucas vezes eu apareço junto dele em uma mesma foto.

## Transfer Learning
Fazemos fine-tuning de um modelo pré-treinado no nosso contexto.

## Comparamos as abordagens
