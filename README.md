# Identificação de COVID-19 em imagens pulmonares

Aprendizagem Automática II - Universidade do Minho

* Célia Manuela Fernandes Ferreira

* Mohammad Reza Tabrizi

Este repositório inclui propostas de modelos de <b>machine learning</b> e <b>deep learning</b> que visam identificar o COVID-19 em imagens pulmonares.

### Motivação
* Os testes COVID-19 são difíceis de obter: não são suficientes para testar toda população, o que dificulta o diagnóstico atempado e a mitigação do contágio. Este cenário pode ainda potenciar a ocorrência de situações oportunistas, com a criação de testes falsos.

* Estas limitações podem ser mitigadas com o recurso a outras formas de diagnóstico. Como o COVID-19 ataca as células epiteliais que revestem o trato respiratório, os raios-X podem ser usados para analisar a saúde pulmonares de um paciente e identificar o COVID-19 sem os kits de teste usuais.

* Porém, a análise de raios-X consome preciosos recursos humanos e tempo, pelo que o desenvolvimento de um sistema de análise automática de raios-X se constitui uma mais-valia. É este o objetivo deste projeto. 


### Objetivos:

- Identificar automaticamente pneumonia em raios-X
- Devido à escassez atual de dados sobre eventos Covid, usar modelos generativos
- Comparar a performance de algoritmos tradicionais de machine learning e deep learning
- Interpretar resultados


### Organização:

O repositório está organizado da seguinte forma:

* Capítulo 1. [Importação de dados](https://github.com/celiaferreira/Covid19_RX/blob/master/1_ImportarDados.ipynb)

  Para garantir o maior número de dados para um treino adequado, foram recolhidos dados de várias fontes: Kaggle e github.

* Capítulo 2. [Pré-processamento de dados](https://github.com/celiaferreira/Covid19_RX/blob/master/2_PreProcessamento.ipynb)

  Nesta secção faz-se o reshape e standardização das imagens, o one-hot-encoding das labels e a partição dos dados em conjuntos de treino, validação e teste.
  
* Capítulo 3: [Análises exploratórias de dados](https://github.com/celiaferreira/Covid19_RX/blob/master/3_AnaliseDados.ipynb)
  
  De modo a obter uma maior compreensão dos dados, esta secção inclui visualização das imagens de input, contabilização das labels e análise de pacientes COVID.

* Capítulo 4: Os dados COVID-19 estão ainda pouco disponíveis. Para ultrapassar esta limitação e permitir uma aprendizagem efetiva serão testadas duas abordagens para aumentar o registo de dados.

  - 4.1 [Oversampling](https://github.com/celiaferreira/Covid19_RX/blob/master/4_1_SMOTE.ipynb)

    Utilizando a técnica de oversampling SMOTE (Sythetic Minority Oversampling TEchnique) são geradas imagens no conjunto de treino de modo a que o dataset fique balanceado.
    
    
  - 4.2 [Data Generation](https://) 
  
    Recorrendo a ligeiras translaões e rotações das imagens COVID-19 no conjunto de treino, são quadruplicados os casos COVID-19 no conjunto de treino.

  Nas secções seguintes serão apresentados e comparados modelos recorrendo a estes 2 tipos de técnica para aumentar e balancear datasets. 


* Capítulo 5: [Funções auxiliares](https://github.com/celiaferreira/Covid19_RX/blob/master/5_FuncoesAuxiliares.ipynb)

  Neste capítulo estão parametrizadas funções que simplificarão os outputs dos modelos desenvolvidos: métricas, matriz de confusao, plots da evolução da accuracy e da loss por epoch e visualização de camadas convolucionais e fully connected.



