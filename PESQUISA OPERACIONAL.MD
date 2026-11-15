
# 📚 Pesquisa Operacional — Revisão para Prova

> Resumo rápido com foco em cálculos, fórmulas e macetes dos simulados da Estácio.

## 1. Programação Linear — Maximizar e Minimizar

**Apareceu várias vezes nos simulados.**

- `Max Z`: encontrar o maior lucro ou resultado.
- `Min Z`: encontrar o menor custo.
- `≤`: não pode ultrapassar.
- `≥`: precisa atingir pelo menos aquele valor.
- `x1, x2 ≥ 0`: não aceita valores negativos.

### Como resolver rápido

Exemplo:

```text
Max Z = x1 + 2x2

x1 + 2x2 ≤ 8
x1, x2 ≥ 0
```

A função objetivo é igual ao lado esquerdo da restrição.

**Logo, Z máximo = 8**, pois é possível atingir esse limite.

### Macetes

1. Teste os valores das alternativas nas restrições.
2. Se violar qualquer restrição, elimine.
3. Calcule Z apenas para as alternativas viáveis.
4. Na maximização, escolha o maior Z; na minimização, o menor.
5. Se a questão exigir inteiros, descarte resultados fracionários.

**Cuidado:** testar alternativas ajuda, mas não garante que a melhor alternativa seja o ótimo global.

---

## 2. Grafos — Caminho Mínimo e Caminho Crítico

**Apareceu nos dois simulados.**

### Caminho mínimo

Some os pesos das ligações até o destino.

```text
A → B = 1
B → D = 2
D → E = 1

Total = 1 + 2 + 1 = 4
```

Compare as rotas possíveis e escolha a de menor soma.

### Caminho crítico

Em redes de projetos, é o caminho que determina a duração total do projeto.

- Normalmente possui a maior duração acumulada.
- Possui folga total igual a zero.
- Atrasar uma atividade crítica pode atrasar o projeto.

### Macetes

- Caminho mínimo: menor soma.
- Caminho crítico: maior duração do início ao fim, em redes de atividades.
- Respeite o sentido das setas.
- Confira se a rota realmente chega ao destino.
- Pode existir empate entre caminhos.

---

## 3. Algoritmo de Prim — Rede de Menor Custo

**Apareceu na questão das tubulações de água.**

Objetivo: conectar todos os bairros usando a menor quantidade possível de tubulação.

### Como resolver

1. Comece em qualquer vértice.
2. Escolha a menor ligação que alcance um vértice ainda não conectado.
3. Continue expandindo a rede.
4. Não forme ciclos.
5. Some as ligações escolhidas.

### Macetes

- 8 vértices = 7 arestas na árvore final.
- 6 vértices = 5 arestas.
- Nunca precisa conectar um vértice duas vezes para formar um ciclo.
- Não escolha uma aresta que ligue dois vértices já conectados.
- O resultado é a soma de todas as arestas escolhidas.

**Decore:** Prim conecta TODOS os pontos. Dijkstra encontra o MENOR CAMINHO.

---

## 4. Caixeiro Viajante

**Apareceu na questão das cidades.**

Objetivo: visitar todas as cidades uma vez e voltar à origem, percorrendo a menor distância possível.

### Como resolver pelo vizinho mais próximo

1. Comece na cidade indicada.
2. Escolha a cidade não visitada mais próxima.
3. Repita até visitar todas.
4. Volte à cidade inicial.
5. Some todas as distâncias.

### Exemplo

```text
A → B = 10
B → C = 15
C → D = 20
D → A = 25

Total = 70 km
```

### Macetes

- Não esqueça a distância de retorno!
- Não visite a mesma cidade duas vezes, exceto ao retornar à origem.
- Observe a cidade inicial exigida.
- Vizinho mais próximo é uma heurística: pode não encontrar o melhor circuito global.
- Se pedir o ótimo exato com poucas cidades, compare diferentes rotas.

---

## 5. Problema de Alocação — Fermentadores

**Apareceu na questão das cervejas.**

Objetivo: distribuir tarefas entre máquinas, pessoas ou fermentadores com o menor custo total.

### Como resolver

1. Cada produto deve receber um fermentador.
2. Cada fermentador deve ser usado uma única vez.
3. Teste combinações possíveis.
4. Some os custos.
5. Escolha a menor soma.

### Exemplo

```text
C1 → F2 = 9
C2 → F3 = 8
C3 → F4 = 16
C4 → F1 = 14

Total = 47
```

### Macetes

- Não escolha simplesmente o menor valor de cada linha.
- Verifique se não repetiu uma coluna.
- Uma escolha barata agora pode impedir uma combinação melhor depois.
- Em tabelas pequenas, compare combinações a partir dos menores valores.

---

## 6. Dualidade — Primal e Dual

**Apareceu na questão dos bolos.**

Regra mais comum:

- Primal de maximização com restrições `≤`.
- Dual de minimização com restrições `≥`.

### Exemplo

```text
Primal:

Max Z = 5x1 + 6x2 + 8x3

Limites das restrições:
8, 10 e 70
```

A função objetivo do dual será:

```text
Min W = 8y1 + 10y2 + 70y3
```

### Macetes

- Os números à direita das restrições viram coeficientes da função objetivo dual.
- Os coeficientes da função objetivo primal passam para o lado direito das restrições duais.
- A matriz dos coeficientes é transposta.
- Maximização vira minimização na forma padrão estudada.

**Dica:** se pedir somente a função objetivo dual, não precisa resolver todas as restrições.

---

## 7. Branch and Bound — Programação Inteira

**Apareceu na questão de x1 e x2 inteiros.**

Utilizado quando as variáveis precisam ser números inteiros.

### Exemplo

```text
Max Z = x1 + 3x2

3x1 + 2x2 ≤ 180
x1 ≤ 40
x2 ≥ 10
x1 + x2 ≥ 20
```

Teste:

```text
x1 = 0
x2 = 90

3(0) + 2(90) = 180 ✅
0 + 90 ≥ 20 ✅

Z = 0 + 3(90) = 270
```

Essa solução também é ótima, pois a restrição de recursos limita Z a 270.

### Macetes

- Se pedir números inteiros, não aceite frações.
- Teste as alternativas nas restrições.
- Calcule a função objetivo das soluções viáveis.
- O Branch and Bound usa limites para descartar ramos que não podem melhorar o resultado.
- Nem sempre arredondar a solução decimal produz a solução ótima.

---

## 8. Análise Multicritério — Concordância

**Apareceu na escolha do centro de distribuição.**

Compara alternativas utilizando vários critérios e pesos.

### Exemplo

| Critério | Peso |
|---|---:|
| Preço | 25% |
| Construção | 22% |
| Operação | 31% |
| Impacto ambiental | 12% |
| Infraestrutura | 10% |

### Concordância

Some os pesos dos critérios em que a alternativa A é pelo menos tão boa quanto B.

Exemplo:

```text
25% + 22% + 31% = 78%

Concordância = 0,78
```

Se o limite exigido for 65%, a comparação passa no teste de concordância.

### Macetes

- Menor preço normalmente é melhor.
- Menor custo normalmente é melhor.
- Maior infraestrutura normalmente é melhor.
- Concordância mede apoio à escolha.
- Discordância mede oposição à escolha.
- Passar na concordância não basta: verifique também o limite de discordância.

**Atenção:** o maior peso indica o critério mais importante, não necessariamente a melhor alternativa.

---

## 9. Interpolação Polinomial — Newton

**Apareceu nas últimas questões do simulado.**

Serve para estimar valores utilizando pontos conhecidos.

### Fórmula da interpolação linear

```text
f(x) = y0 + [(y1-y0)/(x1-x0)] × (x-x0)
```

### Exemplo

```text
x0 = 1 | y0 = 10
x1 = 3 | y1 = 20

Queremos f(2):

f(2) = 10 + [(20-10)/(3-1)] × (2-1)

f(2) = 15
```

### Polinômio de Newton

As diferenças divididas começam com:

```text
f[x0,x1] = (y1-y0)/(x1-x0)
```

Para mais pontos, calculamos diferenças divididas de ordens superiores.

### Macetes

| Grau | Pontos necessários |
|---|---:|
| 1 | 2 |
| 2 | 3 |
| 3 | 4 |
| 4 | 5 |

- Grau 3: use 4 pontos distintos.
- Se pedir todos os 5 pontos, o grau máximo será 4.
- Não use automaticamente interpolação linear se pedir grau 3.
- Para estimar um valor, substitua o x desejado no polinômio.

---

## 10. Nutrição — Problemas de Minimização

**Apareceu na questão das vitaminas.**

Objetivo: atender às necessidades nutricionais gastando o mínimo possível.

### Exemplo

```text
Min Z = 2x1 + 20x2 + 25x3 + 3x4
```

As restrições representam quantidades mínimas de vitaminas.

### Macetes

- A função objetivo representa o custo total.
- `≥` indica a quantidade mínima exigida.
- Não basta escolher o alimento mais barato.
- É necessário satisfazer todas as necessidades nutricionais.
- Mudanças nos preços podem alterar quais alimentos entram na solução.
- Isso é análise de sensibilidade.

---

# ⚡ Tabela para Decorar Antes da Prova

| Se aparecer... | Pense em... |
|---|---|
| Maior lucro | Maximização |
| Menor custo | Minimização |
| Restrições e função objetivo | Simplex |
| Todos os bairros conectados | Prim |
| Menor caminho entre A e B | Dijkstra |
| Maior duração de um projeto | Caminho crítico |
| Visitar todas as cidades | Caixeiro Viajante |
| Produtos e máquinas diferentes | Problema de alocação |
| Primal e dual | Dualidade |
| Variáveis obrigatoriamente inteiras | Branch and Bound |
| Pesos e critérios | Multicritério |
| Estimar valores em uma tabela | Interpolação |
| Mudança de preço ou capacidade | Análise de sensibilidade |
| Transportar maior quantidade | Fluxo máximo |

---

# 🎯 Estratégia para Ganhar Pontos

1. **Resolva primeiro as teóricas:** normalmente exigem menos tempo.
2. **Leia se pede máximo ou mínimo:** isso muda a resposta.
3. **Teste alternativas em programação linear:** elimine as inviáveis.
4. **Em grafos, some os pesos:** não escolha pelo desenho.
5. **Em Prim, conte as arestas:** sempre `n - 1`.
6. **No caixeiro viajante, inclua o retorno.**
7. **No dual, observe os limites das restrições.**
8. **Em alocação, não repita máquinas.**
9. **Em multicritério, observe o sentido de preferência de cada critério.**
10. **Em interpolação, confira o grau solicitado.**

## Prioridade de estudo

**Alta:** Grafos, Simplex, Dualidade, Caixeiro Viajante e Interpolação.

**Média:** Alocação, Branch and Bound e Multicritério.

**Para decorar:** conceitos de Pesquisa Operacional, Fluxos e Redes e Análise de Sensibilidade.

> **Regra de ouro:** identifique o método, elimine alternativas impossíveis e faça apenas os cálculos necessários.
