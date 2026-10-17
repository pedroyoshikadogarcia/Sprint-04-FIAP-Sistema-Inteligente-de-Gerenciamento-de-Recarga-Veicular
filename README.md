## ChargeGrid Intelligence — Sprint 4

---

**Sistema de Gerenciamento de Estação de Recarga para Veículos Elétricos desenvolvido em C. O projeto evoluiu ao longo do semestre de um simulador conceitual para um Sistema de Gerenciamento de Dados em memória, completo e seguro, com suporte a registro, ordenação manual, buscas, tarifação e análise estatística.**

---

**Principais Funcionalidades**

Estrutura Heterogênea de Dados (struct + typedef): Modelagem completa da entidade Sessao combinando ID, modelo do veículo, consumo (kWh), tempo de recarga (minutos), custo total (R$) e máquina de estados (StatusSessao).

Tratamento Avançado de Memória & Entrada: Função de leitura de string (lerStringSegura) desenvolvida para mitigar vulnerabilidades de Buffer Overflow e vazamentos de memória ao limitar o tamanho máximo de entrada (TAM_MODELO = 30) e tratar caracteres de fim de arquivo (EOF).

Algoritmos de Busca:

Busca Linear: Pesquisa sequencial $O(n)$ por ID em vetores desordenados.

Busca Binária: Algoritmo por divisão e conquista $O(\log n)$ com garantia de ordenação prévia por ID.

Algoritmo de Ordenação Autoral (Insertion Sort): Implementação manual in-place sem bibliotecas externas (qsort), suportando ordenação por 4 critérios: ID, Energia Consumida, Custo Total e Tempo de Recarga.

Módulo de Estatísticas e Relatório: Consolidação da quantidade de recargas, energia total fornecida, faturamento bruto, ticket médio e picos de maior e menor consumo.

---

**Estrutura do Repositório**

```text
chargegrid-intelligence/
├── src/
│   └── main.c
├── docs/
│   └── documento_tecnico_sprint3_toshio_v2.pdf
└── README.md
```      


**Como Compilar e Executar**

Certifique-se de ter um compilador GCC instalado em sua máquina.

1. Clonar o repositório:

```bash
https://github.com/pedroyoshikadogarcia/Sprint-04-FIAP-Sistema-Inteligente-de-Gerenciamento-de-Recarga-Veicular
cd Sprint-04-FIAP-Sistema-Inteligente-de-Gerenciamento-de-Recarga-Veicular
```

2. Compilar o programa via terminal:
```bash
gcc src/main.c -o main.exe
```

3. Executar a aplicação:
```bash
Windows (PowerShell / Prompt):

.\main.exe


Linux / macOS:

./main.exe
```
---

***Análise de Complexidade Computacional (Big-O)**

Insertion Sort:

Melhor Caso: $O(n)$ — Ocorre quando o vetor já se encontra ordenado.

Pior Caso: $O(n^2)$ — Ocorre quando o vetor está em ordem invertida, necessitando de laços aninhados para comparar e mover elementos $\left(\frac{n^2 - n}{2}\text{ operações}\right)$.

Busca Binária:

Algoritmo Isolado: $O(\log n)$ — Redução sucessiva do espaço de busca pela metade ($\frac{n}{2^k} = 1 \implies k = \log_2 n$).

Operação Integrada no Programa: $O(n^2)$ — Devido à ordenação prévia obrigatória (insertionSort) executada antes da divisão e conquista ($O(n^2) + O(\log n) = O(n^2)$).

---

**Informações Acadêmicas**

Instituição: FIAP — Faculdade de Informática e Administração Paulista

Curso: Ciência da Computação

Matéria: Data Structures and Algorithms

Professor: Erick Toshio Yamamoto

Grupo: Grupo 03
