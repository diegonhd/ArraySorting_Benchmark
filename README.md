Aqui está uma versão atualizada e aprimorada do seu `README.md`, adaptada para um portfólio.

As principais mudanças foram:
1.  **Inclusão dos novos algoritmos** encontrados no seu notebook (`Heap Sort`, `Bucket Sort`, `Counting Sort`, `Radix Sort`).
2.  **Categorização técnica** dos algoritmos por complexidade para demonstrar domínio teórico.
3.  **Atualização das conclusões** para refletir os dados dos algoritmos lineares (que são muito mais rápidos).
4.  **Melhoria na formatação** e linguagem para um tom mais profissional.

---

# 📊 Benchmark e Análise de Algoritmos de Ordenação

Este projeto consiste em um estudo prático de **Estrutura de Dados e Algoritmos**, focado na análise de desempenho e complexidade assintótica de **10 algoritmos de ordenação** (Sorting Algorithms).

O objetivo é comparar a eficiência teórica ($Big-O$) com o tempo de execução real em Python, utilizando grandes volumes de dados e diferentes cenários de ordenação.

## 🛠️ Tecnologias Utilizadas
* **Linguagem:** Python 3
* **Manipulação de Dados:** NumPy, Pandas
* **Visualização:** Matplotlib
* **Ambiente:** Jupyter Notebook

---

## 🚀 Algoritmos Implementados e Testados

O estudo cobre três categorias principais de algoritmos de ordenação, permitindo uma comparação rica entre diferentes abordagens:

### 1. Algoritmos Quadráticos - $O(n^2)$
* **Bubble Sort**
* **Selection Sort**
* **Insertion Sort**
* **Shell Sort** (Otimizado com estratégia de *gap*, mas comparado neste grupo)

### 2. Algoritmos Log-Lineares - $O(n \log n)$
* **Quick Sort** (Estratégia de pivô: último elemento)
* **Merge Sort** (Abordagem *Divide and Conquer*)
* **Heap Sort** (Baseado em estrutura de Heap Binária)

### 3. Algoritmos Lineares / Distribuição - $O(n+k)$
* **Bucket Sort**
* **Counting Sort**
* **Radix Sort**

---

## 📂 Estrutura do Projeto

A pipeline de execução foi dividida para garantir a integridade dos dados e facilitar a reprodução dos testes:

### 1. Geração e Processamento (`arrays.ipynb`)
* Implementação manual de todos os 10 algoritmos (sem uso de `.sort()` nativo para fins educativos).
* Funções de *benchmark* para cronometragem precisa.
* **Cenários de Teste:**
    * **Tamanhos de Input:** 1.000, 10.000, 20.000, 30.000, 40.000 e 50.000 elementos.
    * **Caso Médio:** Média de 3 execuções com arrays de inteiros aleatórios.
    * **Pior Caso:** Execução com array inversamente ordenado (decrescente).
* Persistência dos dados brutos em arquivos binários `.npy`.

### 2. Análise e Visualização (`sort_benchmark.ipynb`)
* Processamento dos arquivos `.npy` e estruturação em **Pandas DataFrames**.
* Exportação dos resultados consolidados:
    * `resultados_medias.csv`: Desempenho em dados aleatórios.
    * `resultados_piores_casos.csv`: Desempenho em cenários de estresse.
* Geração de gráficos comparativos com escala logarítmica para visualização de ordens de grandeza.

---

## 📈 Análise de Resultados e Insights

A visualização dos dados permitiu extrair conclusões valiosas sobre o comportamento dos algoritmos:

### 1. O Abismo de Desempenho
O gráfico comparativo (escala logarítmica) evidencia três camadas distintas de performance:
* **Lentos:** Bubble, Selection e Insertion Sort sofrem exponencialmente com o aumento de $N$. Para 50k elementos, o tempo é proibitivo.
* **Eficientes:** Merge, Heap e Quick Sort mantêm tempos baixos e escalam suavemente.
* **Instantâneos:** Counting, Radix e Bucket Sort rodam quase instantaneamente, provando a superioridade de algoritmos não baseados em comparação para dados inteiros.

### 2. A Instabilidade do Quick Sort
Apesar de ser o mais rápido dos algoritmos baseados em comparação no **Caso Médio** ($O(n \log n)$), o Quick Sort apresentou uma falha crítica no **Pior Caso**.
* Devido à escolha ingênua do pivô (último elemento), ao ordenar uma lista já inversa, o algoritmo degradou para $O(n^2)$, comportando-se de forma similar ao Bubble Sort no gráfico de piores casos.

### 3. Robustez do Merge Sort e Heap Sort
Ambos demonstraram consistência absoluta. As curvas de tempo para dados aleatórios e dados inversos foram praticamente idênticas, confirmando a garantia de $O(n \log n)$ independente da disposição inicial dos dados.
* *Nota:* O Merge Sort consumiu mais memória ($O(n)$) devido à criação de arrays auxiliares durante a recursão.

### 4. A Superioridade dos Algoritmos Lineares
Os algoritmos de distribuição (**Counting, Radix, Bucket**) superaram todos os outros por ordens de magnitude. O gráfico de "Caso Médio" mostra suas linhas praticamente coladas ao eixo X (tempo próximo de zero), validando a complexidade $O(n+k)$ para o tipo de dado testado (inteiros).

---

## ⚙️ Como Executar

Para reproduzir este estudo em sua máquina:

1.  **Pré-requisitos:** Certifique-se de ter Python instalado com as bibliotecas: `numpy`, `pandas`, `matplotlib`.
2.  **Gerar Dados:** Execute todas as células do notebook `arrays.ipynb`.
    * *Aviso:* Esta etapa pode levar vários minutos devido à execução dos algoritmos quadráticos ($O(n^2)$) em arrays grandes.
3.  **Visualizar Resultados:** Execute o notebook `sort_benchmark.ipynb`. Ele lerá os dados gerados e plotará os gráficos comparativos.