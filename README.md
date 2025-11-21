🚀 Projeto de Benchmark de Algoritmos de Ordenação

Análise de Desempenho e Complexidade de Algoritmos Clássicos em Python (1k a 50k Elementos)

Este projeto de Análise de Algoritmos implementa 10 algoritmos de ordenação em Python para realizar um benchmark completo, medindo e comparando a performance em diferentes escalas (até 50.000 elementos) e cenários (aleatório e pior caso). O objetivo é validar empiricamente as complexidades temporais teóricas ($O(n^2)$, $O(n \log n)$, $O(n+k)$).

🎯 Algoritmos Analisados

O projeto cobre as principais classes de complexidade assintótica, oferecendo uma visão holística sobre a eficiência em ordenação:

Classe de Complexidade

Algoritmos Implementados

Complexidade (Pior Caso)

Quadrática

Bubble Sort, Selection Sort, Insertion Sort

$O(n^2)$

Log-Linear

Quick Sort, Merge Sort, Heap Sort

$O(n^2)$ / $O(n \log n)$

Linear (Counting)

Counting Sort, Radix Sort, Bucket Sort

$O(n+k)$

Intermediário

Shell Sort (Estratégia n // 2)

Pior Caso é complexo, mas sub-quadrático na prática.

📈 Análise e Principais Conclusões

A análise quantitativa, ilustrada por gráficos de desempenho com escala logarítmica, revela uma clara subdivisão de performance e as nuances de cada algoritmo.

1. O Ponto de Ruptura: Complexidade Quadrática ($O(n^2)$)

Os algoritmos de complexidade quadrática (Bubble Sort, Selection Sort e Insertion Sort) demonstraram o pior desempenho, com tempos de execução na escala de 10² segundos para $N=50k$. O crescimento de suas curvas é exponencial no gráfico logarítmico, confirmando a inviabilidade para grandes volumes de dados.

2. Robustez Log-Linear ($O(n \log n)$)

Merge Sort (Estabilidade Garantida): Este algoritmo provou ser o mais estável e previsível. Seu desempenho é $O(n \log n)$ em todos os cenários, com as linhas de Caso Médio e Pior Caso quase sobrepostas. Essa estabilidade tem o custo de $O(n)$ de espaço extra na memória (para cópias de subarrays), validando o trade-off de tempo vs. espaço.

Heap Sort (Estabilidade Teórica): Assim como o Merge Sort, o Heap Sort garante uma performance $O(n \log n)$ no pior caso. Suas curvas escalam de forma eficiente, comprovando sua robustez em situações de dados imprevisíveis.

Shell Sort (Intermediário Prático): Embora sua complexidade teórica (com a sequência n // 2) tenda a $O(n^2)$, o desempenho prático foi significativamente superior aos demais $O(n^2)$ e próximo aos $O(n \log n)$ para a escala testada, operando em uma escala de tempo 10³ vezes menor que o Bubble Sort.

3. A Dicotomia do Quick Sort

Caso Médio (Otimizado): O Quick Sort foi o algoritmo de comparação mais rápido no caso médio, escalando de forma altamente eficiente.

Pior Caso (Vulnerável): A utilização ingênua do último elemento como pivô revelou sua fragilidade. No pior cenário testado (arrays inversamente ordenados), o desempenho se degradou para $O(n^2)$, o que é claramente visível no gráfico "Comparação dos Piores Casos" quando sua linha "salta" para o grupo dos algoritmos lentos.

4. Ultra Velocidade: Ordenação Linear ($O(n+k)$)

Counting Sort e Radix Sort: Estes algoritmos não-comparativos foram, de longe, os mais rápidos no benchmark. Suas curvas são praticamente horizontais (crescimento $O(n)$), pois o overhead é dominado pelo tamanho da lista ($N$) e não pela complexidade logarítmica. Este resultado demonstra a extrema eficiência desses métodos para problemas com um range de valores (k) fixo e pequeno.

⚙️ Estrutura do Projeto

O benchmark foi estruturado em dois notebooks principais para um fluxo de trabalho claro (Execução ➡️ Análise):

arrays.ipynb (Implementação e Geração de Dados):

Contém todas as implementações nativas em Python (com suporte NumPy).

Executa os testes de benchmark em 6 tamanhos de array e 4 cenários (3 aleatórios, 1 pior caso).

Salva os tempos de execução em arquivos .npy para persistência.

sort_benchmark.ipynb (Processamento e Visualização):

Carrega e processa os dados de tempo usando a biblioteca Pandas.

Gera os DataFrames resumidos (resultados_medias.csv e resultados_piores_casos.csv).

Utiliza Matplotlib para gerar todos os gráficos comparativos, incluindo o uso estratégico de escala logarítmica para melhor visualizar a diferença assintótica das classes de complexidade.

🛠️ Habilidades Demonstradas

Análise de Algoritmos: Implementação e validação empírica das complexidades $O(n^2)$, $O(n \log n)$, e $O(n+k)$.

Programação Python Científica: Uso eficiente de numpy e pandas para manipulação e processamento de dados em larga escala.

Visualização de Dados: Geração de gráficos claros e informativos (matplotlib), incluindo a interpretação de escalas logarítmicas.

Engenharia de Software: Benchmarking e testes de estresse de diferentes lógicas de implementação.