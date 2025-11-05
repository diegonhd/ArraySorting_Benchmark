# 📊 Análise de Desempenho de Algoritmos de Ordenação em Python

Este projeto realiza uma análise comparativa da eficiência de diversos algoritmos de ordenação (Sorting Algorithms). O foco principal é medir o tempo de execução e, futuramente, outras métricas de desempenho (como comparações e trocas) em diferentes cenários de entrada, utilizando arrays de tamanhos variados.

## 🚀 Status Atual
O projeto concluiu sua primeira fase de análise, focada em medir o tempo de execução para casos médios (aleatórios) e piores casos (invertidos).

## 🧮 Algoritmos Implementados
Atualmente, a análise compara os seguintes algoritmos implementados "do zero" (sem bibliotecas externas de ordenação):

* Bubble Sort
* Selection Sort
* Insertion Sort
* Shell Sort
* Quick Sort (com estratégia de pivô [especificar a sua, ex: último elemento])
* Merge Sort

## 📈 Análise Realizada (Fase 1)

Na primeira fase, a análise foi conduzida em séries de dados com os seguintes tamanhos: **1.000, 10.000, 20.000, 30.000, 40.000 e 50.000 elementos**.

Para cada tamanho, os seguintes cenários foram testados:

### 1. Caso Médio (Listas Aleatórias)
* **Geração:** Foram geradas 3 séries distintas de números inteiros aleatórios (sem repetição).
* **Métrica:** Calculamos o tempo de execução para ordenar cada uma das 3 séries.
* **Resultado:** Foi calculada a **média de tempo** desses três testes para estabelecer um benchmark de "caso médio" para cada algoritmo.

### 2. Pior Caso (Listas Invertidas)
* **Geração:** Foi gerada 1 série de números inteiros totalmente invertida (ordenada de forma descendente).
* **Métrica:** Medimos o tempo de execução para este cenário.
* **Resultado:** Este teste avalia o comportamento dos algoritmos em seu "pior caso" teórico (especialmente relevante para o Bubble Sort e o Quicksort com pivô ingênuo).

## 📊 Resultados Provisórios
Os resultados da Fase 1 foram consolidados em gráficos de **Tempo (s) vs. Tamanho do Array (N)**.

Esses gráficos comparam visualmente o desempenho do **caso médio aleatório** contra o **pior caso invertido** para cada um dos algoritmos implementados, destacando a diferença de complexidade ($O(n^2)$ vs. $O(n \log n)$) na prática.

## 🛠️ Tecnologias Utilizadas
* **Python 3.x**
* **Matplotlib** (para a plotagem dos gráficos)
* **NumPy** (para geração eficiente de arrays)
* **Módulo `timeit`** (para medição precisa do tempo de execução)

## 🗺️ Próximos Passos (Roadmap)

Para tornar a análise ainda mais robusta e completa, os próximos passos do projeto incluem:

* **1. Expansão dos Casos de Teste:**
    * **Melhor Caso:** Adicionar testes com listas *já ordenadas* (para analisar o desempenho $O(n)$ do Insertion Sort e do Bubble Sort otimizado).
    * **Quase Ordenadas:** Simular dados do "mundo real" que estão com poucos elementos (ex: 5-10%) fora de ordem.
    * **Listas com Duplicatas:** Testar com arrays contendo muitos valores repetidos (ex: números de 1 a 10 numa lista de 50.000).

* **2. Métricas Além do Tempo:**
    * Implementar a contagem de **operações de comparação** (quantas vezes dois elementos são comparados).
    * Implementar a contagem de **operações de troca (swaps)**.
    * Analisar a **complexidade de espaço** (memória), comparando algoritmos *in-place* ($O(1)$) com os que exigem memória auxiliar ($O(n)$), como o Merge Sort.

* **3. Benchmark de Comparação:**
    * Incluir o método nativo do Python, **`list.sort()` (Timsort)**, em todas as análises para usá-lo como *baseline* de desempenho otimizado.

* **4. Análise de Pivô (Quicksort):**
    * Investigar e comparar o impacto de diferentes estratégias de escolha de pivô (ex: primeiro elemento vs. aleatório vs. mediana de três) no desempenho do Quicksort, especialmente no "pior caso".

* **5. Novos Algoritmos (Não-Comparativos):**
    * Adicionar algoritmos como **Counting Sort** e **Radix Sort** para analisar seu desempenho $O(n)$ em cenários específicos (ordenação de inteiros).

* **6. Visualizações Avançadas:**
    * Utilizar **escalas logarítmicas** nos gráficos para melhor comparar visualmente algoritmos de complexidades muito diferentes.
