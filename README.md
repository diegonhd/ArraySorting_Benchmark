# Projeto de Benchmark de Algoritmos de Ordenação

Este projeto realiza uma análise de desempenho e complexidade de seis algoritmos de ordenação comuns. Ele mede e compara os tempos de execução em arrays de tamanhos variados (de 1.000 a 50.000 elementos) para casos médios (dados aleatórios) e piores casos (dados inversamente ordenados).

## Algoritmos Implementados

Os seguintes algoritmos foram implementados e testados:

* **Bubble Sort**
* **Selection Sort**
* **Insertion Sort**
* **Shell Sort** (com estratégia de *gap* inicial = `n // 2`)
* **Quick Sort** (com estratégia de pivô = último elemento, `lista[n-1]`)
* **Merge Sort**

## Estrutura do Projeto

O projeto é dividido em dois notebooks Jupyter principais:

1.  **`arrays.ipynb` (Geração de Dados):**
    * Contém as implementações em Python (usando NumPy) de todos os seis algoritmos de ordenação.
    * Define funções de *benchmark* (`tempo_ordenaçao_...`) para cronometrar o tempo de execução de cada algoritmo.
    * Gera os conjuntos de dados de teste:
        * **Tamanhos:** 1k, 10k, 20k, 30k, 40k e 50k elementos.
        * **Casos Médios:** 3 arrays com dados aleatórios para cada tamanho.
        * **Pior Caso:** 1 array inversamente ordenado para cada tamanho.
    * Salva os dados de tempo de execução em arquivos `.npy` (ex: `list_bs.npy`, `list_qs.npy`, etc.) para análise posterior.

2.  **`sort_benchmark.ipynb` (Análise e Visualização):**
    * Carrega os arquivos `.npy` gerados pelo `arrays.ipynb`.
    * Processa os dados brutos e os organiza em DataFrames do Pandas.
    * Cria dois DataFrames principais para comparação:
        * `df_medias`: Contém a média dos tempos de execução dos arrays aleatórios.
        * `df_piores_casos`: Contém os tempos de execução dos arrays de pior caso.
    * Salva esses DataFrames de resumo em `resultados_medias.csv` e `resultados_piores_casos.csv`.
    * Utiliza Matplotlib para gerar os gráficos de desempenho, tanto individualmente para cada algoritmo quanto em comparações (Casos Médios e Piores Casos) com escala logarítmica.

## Análise e Principais Conclusões

A análise dos gráficos gerados revela o comportamento de complexidade de tempo de cada algoritmo na prática.

### 1. Divisão Clara: $O(n^2)$ vs. $O(n \log n)$

O gráfico "Comparação dos Casos Médios", que usa uma escala Y logarítmica, mostra uma divisão nítida de desempenho:

* **Grupo Lento $(O(n^2))$:** `Bubble Sort`, `Selection Sort` e `Insertion Sort`. Seus tempos de execução são ordens de magnitude maiores, crescendo exponencialmente.
* **Grupo Rápido ($O(n \log n)$ ou sub-quadrático):** `Quick Sort`, `Merge Sort` e `Shell Sort`. Seus tempos são significativamente mais baixos e escalam muito melhor.

### 2. A Dicotomia do Quick Sort

Este algoritmo apresentou o desempenho mais contrastante:

* **Caso Médio $O(n \log (n))$:** Foi o algoritmo **mais rápido** de todos no caso médio. Com dados aleatórios, a estratégia de pivô (`lista[n-1]`) funciona bem, dividindo o array eficientemente.
* **Pior Caso $O(n^2)$:** A estratégia de pivô "último elemento" é ingênua e vulnerável. Como visto no gráfico "Tamanho x Tempo (Quick Sort)", o pior caso (linha vermelha) ocorre quando o array está ordenado (ou inversamente ordenado), forçando o algoritmo a partições desbalanceadas ($n-1$ e $0$) e degradando o desempenho para quadrático.

### 3. A Consistência do Merge Sort

O `Merge Sort` provou ser o algoritmo mais estável e previsível.

* **Todos os Casos $O(n \log (n))$ :** Seu desempenho é $O(n \log (n))$ em todos os cenários. O gráfico "Tamanho x Tempo (Merge Sort)" confirma isso, mostrando as linhas de caso médio e pior caso quase sobrepostas.
* **Artefato de Pior Caso:** Uma observação interessante é que o "pior caso" (linha vermelha) foi consistentemente *mais rápido* que a média. Isso é provavelmente um artefato de otimização de hardware (CPU *Branch Prediction*), onde dados previsíveis (como um array ordenado) são processados de forma mais eficiente do que dados aleatórios e imprevisíveis.
* **Custo de Espaço:** Conforme observado no `sort_benchmark.ipynb`, essa estabilidade de tempo tem um custo: o `Merge Sort` utiliza **$O(n)$ de espaço extra** na memória para criar cópias dos subarrays durante a mesclagem.

### 4. Comparação Final: Piores Casos

O gráfico "Comparação dos Piores Casos" (escala Y logarítmica) destaca a importância de escolher o algoritmo certo para dados não confiáveis:

* O **Quick Sort** (linha roxa) "salta" do grupo rápido para o grupo lento, confirmando sua degradação para $O(n^2)$.
* O **Merge Sort** (linha marrom) e o **Shell Sort** (linha vermelha) permanecem na base, provando sua robustez e desempenho superior mesmo no pior cenário testado.

## Como Executar

1.  Execute todas as células no notebook `arrays.ipynb` para gerar os dados de benchmark. (Isso pode levar vários minutos, especialmente para os algoritmos $O(n^2)$).
2.  Após a conclusão, execute todas as células no notebook `sort_benchmark.ipynb` para analisar os dados e gerar todos os gráficos e arquivos CSV de resultados.