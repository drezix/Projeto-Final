# Projeto de Classificação de Imagens: Abordagens Clássicas e CNNs

## Descrição do Projeto
Este projeto tem como objetivo comparar e avaliar duas estratégias de classificação de imagens, utilizando:

1. **Abordagem Clássica**
   - **Extração de Características:** Implementação de descritores baseados em filtros de Gabor – método não abordado em aula, semelhante a técnicas como LBP, HOG ou SIFT. Para cada imagem, são extraídos estatísticos (média e variância) após a aplicação de múltiplos filtros com diferentes parâmetros (tamanho, orientação, etc.).
   - **Classificador:** Utilização de um classificador SVM com kernel RBF

2. **Abordagem com Redes Neurais Convolucionais (CNNs)**
   - **Modelo:** Emprego de uma rede pré-treinada (ResNet50 com pesos da ImageNet) para extração de features.
   - **Ajuste Fino (Fine-Tuning):** Congelamento parcial das camadas (congeladas as primeiras 150 camadas) e treinamento das camadas posteriores, além da adição de camadas densas personalizadas.
   - **Otimização:** Uso do otimizador Adam com taxa de aprendizado de 0.001 e aplicação de *mixed precision* para ganhos de performance.

Ambas as abordagens são avaliadas com base nas seguintes métricas:
- Matriz de Confusão
- Precisão (Precision)
- Recall
- F1-Score
- Acurácia

## Dataset
O dataset utilizado foi obtido do Kaggle:
[Covid-19 & Normal](https://www.kaggle.com/datasets/tarandeep97/covid19-normal-posteroanteriorpa-xrays)

Sendo organizado em duas classes:
- **covid**
- **normal**

A estrutura esperada é a seguinte:
```
    /dataset 
        ├── /train │ 
            ├── /covid 
            └── /normal 
        └── /test 
            ├── /covid 
            └── /normal
```

Outras bases públicas (como Coffee Bean Dataset, Kaggle, ImageNet ou Open Images) também podem ser utilizadas, desde que haja pelo menos duas classes com amostras suficientes para análise.

## Como Utilizar o Projeto

1. **Baixar o Dataset e Códigos:**
   - Baixe o dataset
   - Baixe os notebooks `CNN_Approach.ipynb` e `Classical_Approach.ipynb` do repositório.

2. **Preparação do Ambiente:**
   - Utilize o Google Colab e monte seu Google Drive com o comando:
     ```python
     from google.colab import drive
     drive.mount('/content/drive')
     ```
   - Certifique-se de que o dataset esteja organizado conforme descrito na seção de **Dataset**.
   - (Opcional) Para usar GPU, vá em **Ambiente de Execução** -> **Alterar o tipo de ambiente de execução** -> selecione uma das GPUs disponíveis (possivelmente a T4) e clique em **Salvar**.

3. **Execução dos Notebooks:**
   - Abra e execute os notebooks:
     - `CNN_Approach.ipynb`
     - `Classical_Approach.ipynb`
   - Os notebooks já incluem todas as etapas de pré-processamento, treinamento, avaliação e exibição dos resultados (métricas e gráficos).

4. **Visualização dos Resultados:**
   - Ao final da execução de cada notebook, serão exibidos os valores das métricas (acurácia, precision, recall, F1-score) e a matriz de confusão para melhor análise do desempenho de cada abordagem.


## Tecnologias e Bibliotecas Utilizadas
- **Ambiente:** Google Colab
- **Linguagem:** Python
- **Bibliotecas:**
  - **Para a Abordagem com CNNs:** TensorFlow, Keras (ResNet50), Mixed Precision
  - **Para a Abordagem Clássica:** OpenCV, Numpy, Scikit-learn, Matplotlib
  - Utilização adicional de funções para leitura e pré-processamento de imagens.

## Detalhes dos Descritores e Classificadores
### Abordagem Clássica (Gabor + SVM)
- **Descritor:** Filtros de Gabor aplicados sobre imagens convertidas para escala de cinza, com extração das estatísticas (média e variância) dos mapas filtrados.
- **Classificador:** SVM com kernel RBF.  
- **Resultados Obtidos:**  
  - Acurácia: *93%*  
  - Outras métricas (precision, recall e F1-score) também foram avaliadas e apresentadas.

### Abordagem com CNNs (ResNet50 Fine-Tuning)
- **Modelo:** ResNet50 pré-treinada com pesos da ImageNet.
- **Ajuste Fino:** Congelamento das primeiras 150 camadas, adição de camada densa de 256 unidades (ReLU) e camada de saída com ativação *sigmoid*.
- **Resultados Obtidos:**  
  - Acurácia Final no conjunto de teste: *100%*  
  - Métricas complementares como a matriz de confusão foram geradas para análise.

## Como Utilizar o Projeto
1. **Preparação do Ambiente:**
   - Utilize o Google Colab e monte seu Google Drive com o comando:
     ```python
     from google.colab import drive
     drive.mount('/content/drive')
     ```
   - Certifique-se de que o dataset esteja organizado conforme descrito na seção de **Dataset**.

2. **Execução dos Notebooks:**
   - Abra e execute os notebooks:
     - `CNN_Approach.ipynb`
     - `Classical_Approach.ipynb`
   - Os notebooks já incluem todas as etapas de pré-processamento, treinamento, avaliação e exibição dos resultados (métricas e gráficos).

3. **Visualização dos Resultados:**
   - Ao final da execução de cada notebook, serão exibidos os valores das métricas (acurácia, precision, recall, F1-score) e a matriz de confusão para melhor análise do desempenho de cada abordagem.

## Repositório e Vídeo de Apresentação
- **Link do Repositório:** [https://github.com/drezix/Projeto-Final](https://github.com/drezix/Projeto-Final)
- **Link para pasta do Drive:** [Drive](https://drive.google.com/drive/folders/1U91zYsd6Pqp5llbaD45vYVWy808VDz6S?usp=drive_link)
- **Vídeo de Apresentação:** [Link para o vídeo de apresentação](https://drive.google.com/drive/folders/1U91zYsd6Pqp5llbaD45vYVWy808VDz6S?usp=sharingo)

## Instruções Adicionais
- O projeto compactado não inclui o dataset; este deverá ser provido separadamente.
- Verifique a estrutura de diretórios e ajuste, se necessário, para assegurar a execução correta dos notebooks.
- Em caso de dúvidas, consulte os comentários presentes no código e a documentação das bibliotecas utilizadas.

*Este projeto foi desenvolvido como parte das atividades da disciplina de Processamento de Imagens.*