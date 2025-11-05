# 📊 Análise de Desempenho de Algoritmos de Ordenação

Este projeto implementa e analisa o desempenho de seis algoritmos de ordenação clássicos em Python, utilizando as bibliotecas `numpy` e `time`. O objetivo principal é medir e comparar a complexidade de tempo (tempo de execução) de cada algoritmo à medida que o tamanho da entrada (N) aumenta.

## 🚀 Algoritmos Analisados

O notebook `arrays.ipynb` contém implementações "do zero" dos seguintes algoritmos:

* Bubble Sort
* Selection Sort
* Insertion Sort
* Shell Sort
* Quick Sort (recursivo)
* Merge Sort (recursivo)

## 🔬 Metodologia de Análise

A análise de desempenho é conduzida da seguinte forma:

1.  **Geração de Dados:** Para cada tamanho de array $N$, são gerados quatro conjuntos de dados:
    * **3x Séries Aleatórias:** Arrays de números inteiros gerados aleatoriamente.
    * **1x Pior Caso (Worst Case):** Um array com os mesmos elementos, mas ordenado em ordem decrescente (o pior caso para a maioria dos algoritmos de ordenação).

2.  **Tamanhos de Entrada (N):**
    * 1.000 (1k)
    * 10.000 (10k)
    * 20.000 (20k)
    * 30.000 (30k)
    * 40.000 (40k)
    * 50.000 (50k)

3.  **Coleta de Métricas:**
    * O tempo de execução de cada algoritmo é medido para cada uma das quatro séries.
    * A **Média de Tempo** é calculada a partir das três execuções com séries aleatórias.
    * O **Tempo do Pior Caso** é registrado separadamente.

4.  **Armazenamento:**
    * Todos os tempos e médias são salvos em arquivos `.npy` (ex: `mean_arr_bs.npy`, `list_qs.npy`) para análise posterior e plotagem de gráficos.

## ⚙️ Como Executar o Projeto

1.  **Pré-requisitos:**
    * Python 3.x
    * Jupyter Notebook ou Jupyter Lab
    * Bibliotecas: `numpy`, `matplotlib`, `time` (a última é nativa do Python).

    ```bash
    pip install numpy matplotlib jupyter
    ```

2.  **Executando os Testes:**
    * Abra o notebook `arrays.ipynb` no Jupyter.
    * Execute todas as células sequencialmente. Isso pode levar um tempo considerável, especialmente para os algoritmos $O(n^2)$ (Bubble, Selection, Insertion) em tamanhos de array grandes.

3.  **Análise dos Resultados:**
    * Após a execução, os arquivos `.npy` estarão disponíveis no diretório.
    * Um segundo notebook (ou script) pode ser usado para carregar esses arquivos `.npy` e plotar os gráficos de **Tempo x Tamanho** usando `matplotlib`.

## 📈 Análises Planejadas e Próximos Passos

Para incrementar a análise e torná-la mais robusta, as seguintes melhorias estão planejadas:

* [ ] **Refinamento da Geração de Dados:**
    * Alterar a geração de dados aleatórios para usar `np.random.permutation(N)` para garantir "números não repetidos", conforme o requisito original.
    * Comparar o desempenho atual (com repetições) versus o desempenho (sem repetições).

* [ ] **Robustez Estatística:**
    * Aumentar o número de execuções de 3 para 10 (ou mais) para calcular uma média de tempo mais estável e confiável.

* [ ] **Inclusão de Novos Cenários de Teste:**
    * **Melhor Caso (Best Case):** Medir o tempo de execução para um array *já ordenado*.
    * **Quase Ordenado:** Medir o tempo para um array 95% ordenado, simulando um cenário de dados do mundo real.

* [ ] **Métricas Adicionais (Além do Tempo):**
    * **Complexidade de Espaço:** Analisar e medir o pico de uso de memória (ex: usando `tracemalloc`) para classificar os algoritmos como *in-place* ($O(1)$) ou que requerem espaço auxiliar ($O(n)$ ou $O(\log n)$).
    * **Estabilidade:** Classificar teoricamente cada implementação como *estável* ou *instável*.

* [ ] **Otimização do Shell Sort:**
    * Analisar o impacto da sequência de `gap` (atualmente `n // 2`).
    * Implementar e comparar o desempenho com outras sequências de `gap` (ex: Knuth, Ciura) para otimizar o algoritmo.