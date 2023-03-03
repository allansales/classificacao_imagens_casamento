# Classificacao de imagens do casamento

O objetivo deste projeto é avaliar o desempenho de diferentes abordagens para classificar a minha presença e a da minha esposa nas fotos do nosso casamento. As abordagens são 1) o treinamento de uma rede convolucional do zero e 2) uso de Transfer Learning, fazendo fine-tuning de um modelo VGG19. Por último, nós executamos o LIME em algumas fotos para verificar quais features foram mais importantes para fazer a classificação daquela foto e tirar alguns insights da tarefa.

## Abordagem Multilabel

O notebook *classifica_casal_multilabel* faz o treinamento de ambos modelos usando abordagem multilabel do problema, onde minha presença e a presença de minha esposa são tomadas como labels diferentes que assumem valor 0 ou 1, de acordo com a ausência ou presença na foto (e.g., o rótulo [0, 1] indica minha ausência e presença da minha esposa na foto).

O modelo usando Transfer Learning se mostra bem mais eficiente em fazer a classificação do o modelo treinado do zero, atigindo ~98% de precisão, ~99% de recall e 96% de acurácia. Já quanto ao tempo de treinamento, o modelo com Transfer Learning leva mais de 1h pra treinar, enquanto o outro modelo é treinado em minutos. Em geral é esperado que o Transfer Learning seja mais rápido que o treinamento total de uma rede, no entanto, isso não acontece no nosso contexto devido ao tamanho da rede pré-treinada ser muito maior que a rede que nós estamos contruindo do zero. Quanto à diferença nos seus desempenhos, a rede com Transfer Learning se beneficia das features já aprendidas no seu treino anterio no dataset do imagenet, o que facilita a aplicação no nosso cenário.

Tanto para os casos de acerto quanto para os de erro, o LIME aponta quais foram as partes da foto que mais contribuíram positivamente e negativamente para a classificação. Essa parte é interessante devido revelar vários vieses escondidos nas construção do dataset (e.g., vieses dos fotógrafos, na posição em que noivo e noiva aparecem costumeiramente, locais e posições onde as fotos foram feitas, etc) e que a rede acaba usando para classificar a nossa presença, sem necessariamente estar olhando partes da foto que contenham nossa roupa ou nossos rostos. Por exemplo, na foto usada como exemplo de explicação de acerto, o LIME indica que o arco de flores na entrada da igreja foi fator determinante para a minha ausência na foto e para a presença da noiva, o que faz bastante sentido, dado que todas as fotos que o arco aparece naquela posição tem apenas a noiva.
