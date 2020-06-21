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
  
  De modo a obter uma maior compreensão dos dados, esta secção inclui:
  
  - Visualização das imagens de input 
  - Contabilização das labels
  - Análise de pacientes COVID

* Capítulo 4:







