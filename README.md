# Classificação de Tumores Cerebrais usando CNN e Validação Cruzada K-Fold

Este repositório contém o código para um modelo de classificação de imagens baseado em Redes Neurais Convolucionais (CNNs) projetado para classificar imagens de ressonância magnética (RM) de cérebros para detectar a presença e o tipo de tumor cerebral. O modelo foi desenvolvido utilizando TensorFlow/Keras e emprega validação cruzada K-Fold para uma avaliação mais robusta do desempenho.

## Dataset

O modelo foi treinado e avaliado utilizando o dataset "[Brain Tumor MRI Dataset](https://www.kaggle.com/masoudnickparvar/brain-tumor-mri-dataset)" disponível no Kaggle. Este dataset contém imagens de RM cerebrais categorizadas em 4 classes:

*   Sem tumor
*   Glioma 
*   Meningioma
*   Pituitary

O dataset original foi dividido em conjuntos de treino e teste. A validação cruzada K-Fold foi aplicada apenas ao conjunto de treino para otimizar e avaliar o modelo antes da avaliação final no conjunto de teste independente.

## Arquitetura do Modelo

A arquitetura da CNN utilizada consiste em:

*   Camada de Entrada com Data Augmentation e Rescaling.
*   Múltiplas camadas convolucionais com ativação ReLU, seguidas por camadas de Max Pooling para redução dimensional e camadas de Dropout para regularização.
*   Uma camada Flatten para converter a saída das camadas convolucionais em um vetor.
*   Uma camada Dense (Totalmente Conectada) com ativação ReLU e regularização L2.
*   Uma camada de saída Dense com 4 unidades (correspondentes às 4 classes) e ativação Softmax para obter as probabilidades de classe.

A compilação do modelo utiliza a função de perda `categorical_crossentropy` e o otimizador Adam com uma taxa de aprendizado ajustável.

## Treinamento

O treinamento do modelo foi realizado utilizando validação cruzada K-Fold (`K=5` no código). Para cada fold:

1.  O conjunto de treino foi dividido em subconjuntos de treino e validação.
2.  Uma nova instância do modelo foi criada e compilada.
3.  O modelo foi treinado no subconjunto de treino com Early Stopping (monitorando a perda de validação) e ReduceLROnPlateau (reduzindo a taxa de aprendizado quando a perda de validação para de melhorar).
4.  As métricas de desempenho (perda e acurácia) no subconjunto de validação foram registradas.

Após a conclusão da validação cruzada K-Fold, as métricas médias de validação foram calculadas para fornecer uma estimativa mais robusta do desempenho esperado do modelo.

Um modelo final foi então treinado no conjunto de treino completo (combinando todos os folds) para ser avaliado no conjunto de teste independente.

## Resultados

Os resultados da validação cruzada K-Fold fornecem uma indicação do desempenho médio do modelo em diferentes partições dos dados de treino. A avaliação final no conjunto de teste fornece uma medida do desempenho do modelo em dados completamente novos.

**Métricas de Validação Cruzada (Média sobre K folds):**

*   Perda Média de Validação: [AINDA NÃO TREINADA]
*   Acurácia Média de Validação: [AINDA NÃO TREINADA]%

**Métricas no Conjunto de Teste:**

*   Perda no Teste: [AINDA NÃO TREINADA]
*   Acurácia no Teste: [AINDA NÃO TREINADA]%

## Como Usar

1.  Clone este repositório.
2.  Faça o download do dataset "[Brain Tumor MRI Dataset](https://www.kaggle.com/masoudnickparvar/brain-tumor-mri-dataset)" do Kaggle.
3.  Organize o dataset no formato esperado pelo código (pastas "Training" e "Testing" com subpastas para cada classe).
4.  Abra o notebook [Nome do seu Notebook .ipynb] no Google Colab ou ambiente similar.
5.  Conecte-se ao Google Drive para salvar os modelos treinados (opcional).
6.  Execute as células do notebook para baixar o dataset (se ainda não tiver feito), carregar os dados, construir e treinar o modelo com validação cruzada e avaliar o modelo final.

## Dependências

*   TensorFlow
*   Keras
*   NumPy
*   Matplotlib
*   Scikit-learn
*   Kagglehub (para download do dataset)
