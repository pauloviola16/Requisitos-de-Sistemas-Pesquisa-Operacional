
# 📚 Pesquisa Operacional — Resumo para Prova

> Revisão dos 8 temas da disciplina de Pesquisa Operacional — Estácio.
>
> **Objetivo:** entender os conceitos, reconhecer os métodos e resolver as questões mais comuns da prova.

---

# 1. Introdução à Pesquisa Operacional

## O que é Pesquisa Operacional?

É uma área da matemática que utiliza modelos para encontrar a melhor solução para um problema de decisão.

Pode ser utilizada para:

- Maximizar lucros.
- Minimizar custos.
- Reduzir distâncias.
- Organizar transportes.
- Otimizar recursos.
- Planejar a produção.

### Conceitos principais

| Conceito | Significado |
|---|---|
| Variáveis de decisão | O que precisamos descobrir |
| Função objetivo | O que queremos maximizar ou minimizar |
| Restrições | Limitações do problema |
| Solução viável | Solução que respeita todas as restrições |
| Solução ótima | Melhor solução viável possível |

### Exemplo

Uma fábrica produz mesas (x1) e cadeiras (x2).

Cada mesa gera R$ 500 e cada cadeira R$ 100.

**Função objetivo:**

```text
Max Z = 500x1 + 100x2
```

Se a fábrica possui recursos limitados:

```text
x1 + 2x2 <= 100
x1, x2 >= 0
```

O objetivo é encontrar as quantidades que geram o maior lucro sem ultrapassar os recursos.

### Maximização e minimização

- **Maximizar:** lucro, produção, eficiência.
- **Minimizar:** custos, distâncias, desperdícios.

**Na prova:** identifique primeiro o objetivo, depois as variáveis e as restrições.

---

# 2. Método Simplex

## O que é?

É um método matemático utilizado para resolver problemas de Programação Linear.

Busca a melhor solução considerando a função objetivo e as restrições.

### Quando utilizar?

Quando precisamos:

- Maximizar lucros.
- Minimizar custos.
- Distribuir recursos limitados.
- Determinar quantidades ideais de produção.

### Exemplo

```text
Max Z = x1 + 2x2

Sujeito a:

x1 + 2x2 <= 8
-x1 + x2 <= 16

x1, x2 >= 0
```

A primeira restrição limita diretamente a função objetivo:

```text
Z = x1 + 2x2 <= 8
```

Logo:

```text
Z máximo = 8
```

Por exemplo:

```text
x1 = 0
x2 = 4

Z = 0 + 2(4) = 8
```

### Variáveis de folga

São utilizadas para transformar desigualdades em igualdades.

Exemplo:

```text
x1 + x2 <= 10
```

Adicionamos uma variável de folga:

```text
x1 + x2 + s1 = 10
```

A variável `s1` representa o recurso que sobrou.

### Conceitos importantes

- Solução básica viável: atende às restrições.
- Variável de folga: representa recursos não utilizados.
- Variável artificial: auxilia na obtenção de uma base inicial em determinados problemas.
- Solução ótima: não existe melhoria possível dentro da região viável.

**Na prova:** antes de montar o Simplex, verifique se a função objetivo já está limitada diretamente por alguma restrição.

---

# 3. Dualidade e Análise de Sensibilidade

## O que é dualidade?

Todo problema de Programação Linear possui um problema associado chamado **dual**.

Normalmente:

- Primal de maximização → dual de minimização.
- Primal de minimização → dual de maximização.

### Exemplo

Problema primal:

```text
Max Z = 5x1 + 6x2 + 8x3

Sujeito a:

0,2x1 + 0,1x2 + 0,2x3 <= 8
0,6x1 + 0,4x2 + 0,5x3 <= 10
2x1 + 4x2 + 3x3 <= 70

x1, x2, x3 >= 0
```

A função objetivo do dual será:

```text
Min W = 8y1 + 10y2 + 70y3
```

As restrições do dual serão:

```text
0,2y1 + 0,6y2 + 2y3 >= 5

0,1y1 + 0,4y2 + 4y3 >= 6

0,2y1 + 0,5y2 + 3y3 >= 8

y1, y2, y3 >= 0
```

### Regra para montar o dual

| Primal | Dual |
|---|---|
| Maximizar | Minimizar |
| Minimizar | Maximizar |
| Coeficientes da função objetivo | Limites das restrições |
| Limites das restrições | Coeficientes da função objetivo |
| Matriz das restrições | Matriz transposta |

> Essas regras de sinais consideram as formas padrão apresentadas.

## Análise de sensibilidade

Verifica como mudanças nos dados afetam a solução ótima.

Exemplos:

- Se o preço de um produto aumentar, ele continuará sendo produzido?
- Se um recurso ficar mais caro, a solução muda?
- Se a capacidade aumentar, o lucro melhora?

### Preço-sombra

Representa a variação marginal do valor ótimo quando aumentamos em uma unidade a disponibilidade de um recurso, dentro de certos limites.

### Custo reduzido

Indica a melhoria necessária no coeficiente da função objetivo para que uma variável atualmente igual a zero possa entrar na solução ótima, respeitadas as condições do modelo.

**Na prova:** questões com mudanças nos preços, custos ou capacidades geralmente envolvem análise de sensibilidade.

---

# 4. Problemas de Conexão

## O que são grafos?

Um grafo é formado por:

- **Vértices (nós):** representam lugares ou pontos.
- **Arestas:** representam ligações entre os pontos.
- **Pesos:** representam distâncias, custos ou tempos.

Exemplo:

```text
A -- 4 -- B -- 2 -- C
```

A ligação A → B custa 4.

A ligação B → C custa 2.

Custo total:

```text
4 + 2 = 6
```

## Árvore Geradora Mínima

O objetivo é conectar todos os vértices gastando o mínimo possível.

Exemplos:

- Instalação de tubulações.
- Redes elétricas.
- Redes de internet.
- Distribuição de água.

### Algoritmo de Prim

Também conhecido como método do vértice adjacente mais próximo.

Passos:

1. Escolha um vértice inicial.
2. Identifique a menor aresta que liga um vértice já conectado a um ainda não conectado.
3. Adicione essa aresta e o novo vértice.
4. Repita até conectar todos.
5. Some os pesos das arestas selecionadas.

### Regras importantes

- Não formar ciclos.
- Conectar todos os vértices.
- Escolher a ligação mais barata disponível entre o conjunto conectado e o restante.
- Para `n` vértices, a árvore possui `n - 1` arestas.

**Atenção:** a menor aresta do grafo inteiro não é necessariamente a próxima escolha do algoritmo de Prim.

---

# 5. Fluxos e Redes

## O que são?

São problemas que envolvem movimentação de recursos em uma rede.

Exemplos:

- Transporte de mercadorias.
- Distribuição de água.
- Fluxo de veículos.
- Redes de computadores.
- Transporte de produtos entre fábricas e lojas.

### Caminho mínimo

Busca o percurso de menor custo entre dois pontos.

Exemplo:

```text
A → B = 2
B → D = 3

A → C = 4
C → D = 5
```

Caminho A → B → D:

```text
2 + 3 = 5
```

Caminho A → C → D:

```text
4 + 5 = 9
```

**Melhor caminho: A → B → D, custo 5.**

### Algoritmo de Dijkstra

Utilizado para encontrar caminhos mínimos em grafos com pesos não negativos.

Passos:

1. Inicie a distância da origem com zero.
2. Coloque distância infinita nos demais vértices.
3. Atualize as menores distâncias conhecidas.
4. Escolha o vértice não visitado com menor distância provisória.
5. Repita até encontrar o destino.

### Fluxo máximo

Determina a maior quantidade que pode atravessar uma rede respeitando as capacidades das ligações.

Exemplo:

```text
Origem → A = 10 unidades
Origem → B = 15 unidades
```

A capacidade de saída da origem é de até 25 unidades, mas o fluxo máximo também depende das demais conexões.

### Diferença importante

| Problema | Objetivo |
|---|---|
| Caminho mínimo | Menor distância ou custo entre pontos |
| Árvore geradora mínima | Conectar todos os pontos com custo mínimo |
| Fluxo máximo | Transportar a maior quantidade possível |

---

# 6. Problema do Caixeiro Viajante

## O que é?

Um viajante precisa visitar várias cidades, passando uma vez por cada uma e retornando ao ponto inicial, percorrendo a menor distância total possível.

### Exemplo

Distâncias:

```text
A → B = 10
B → C = 15
C → A = 20
```

Rota:

```text
A → B → C → A
```

Distância total:

```text
10 + 15 + 20 = 45
```

## Métodos utilizados

### Vizinho mais próximo

1. Escolha a cidade inicial.
2. Vá para a cidade não visitada mais próxima.
3. Repita até visitar todas.
4. Retorne à origem.

Esse método é rápido, mas não garante a solução ótima.

### Inserção com maior afastamento

É uma heurística que constrói uma rota inserindo cidades progressivamente.

Uma inicialização comum utiliza dois vértices mais distantes.

Depois:

1. Identifique o vértice ainda não visitado mais afastado da rota.
2. Verifique em qual posição inseri-lo.
3. Escolha a inserção que cause o menor aumento na distância.
4. Repita até incluir todos os vértices.

### Diferença para caminho mínimo

**Caminho mínimo:** vai de A até B pela menor distância.

**Caixeiro viajante:** visita todas as cidades e retorna ao início.

**Na prova:** se aparecer uma tabela de distâncias entre cidades e a obrigação de visitar todas, provavelmente é um problema do caixeiro viajante.

---

# 7. Análise Multicritério à Decisão

## O que é?

É um método para escolher a melhor alternativa considerando vários critérios simultaneamente.

Exemplo: escolher onde construir um centro de distribuição.

Critérios possíveis:

- Preço do terreno.
- Custo de construção.
- Custo operacional.
- Impacto ambiental.
- Infraestrutura.

Cada critério possui um peso.

### Concordância e discordância

São conceitos utilizados em métodos como o ELECTRE.

**Concordância:** mede quanto os critérios apoiam a afirmação de que uma alternativa é pelo menos tão boa quanto outra.

**Discordância:** mede a oposição a essa afirmação, especialmente quando uma alternativa é muito pior em determinado critério.

### Exemplo de pesos

| Critério | Peso |
|---|---|
| Preço | 25% |
| Construção | 22% |
| Operação | 31% |
| Impacto ambiental | 12% |
| Infraestrutura | 10% |

O custo operacional possui o maior peso individual: 31%.

Isso não significa que a alternativa mais barata operacionalmente será automaticamente a melhor.

### Critérios de maximização e minimização

**Maximização:**
- Melhor infraestrutura.
- Maior produtividade.
- Maior qualidade.

**Minimização:**
- Menor preço.
- Menor custo.
- Menor impacto ambiental, quando medido como dano.

### Regra da concordância

Se os critérios favoráveis a uma alternativa somam:

```text
25% + 22% + 31% = 78%
```

O índice de concordância dessa comparação será:

```text
C = 0,78
```

O resultado deve ser comparado ao limite de concordância estabelecido.

**Na prova:** identifique quais critérios devem aumentar, quais devem diminuir e os pesos utilizados.

---

# 8. Programação Matemática

## Programação Linear

Utiliza funções e restrições lineares.

Exemplo:

```text
Max Z = 3x1 + 5x2
```

## Programação Inteira

As variáveis de decisão precisam assumir valores inteiros.

Exemplos:

- Quantidade de caminhões.
- Número de funcionários.
- Quantidade de máquinas.
- Número de veículos.

Não faz sentido contratar 2,5 funcionários.

### Branch and Bound

Método utilizado para resolver problemas de otimização inteira.

Funcionamento:

1. Resolve a relaxação linear do problema.
2. Verifica se a solução é inteira.
3. Se houver valores fracionários, divide o problema em ramos.
4. Calcula limites para cada ramo.
5. Descarta ramos que não podem melhorar a solução.
6. Continua até encontrar uma solução inteira ótima.

### Exemplo

```text
Max Z = x1 + 3x2

Sujeito a:

3x1 + 2x2 <= 180
x1 <= 40
x1 <= 60
x2 >= 10
x1 + x2 >= 20

x1, x2 inteiros não negativos
```

Como x2 contribui mais para o lucro por unidade e consome 2 unidades do recurso:

```text
x1 = 0
x2 = 90

Z = 270
```

Essa solução respeita todas as restrições e maximiza Z.

---

# 9. Interpolação Polinomial

Esse conteúdo também apareceu no simulado.

## O que é interpolação?

É uma técnica utilizada para estimar valores entre pontos conhecidos de uma tabela.

### Interpolação Linear

Utiliza dois pontos.

Fórmula:

```text
f(x) = y0 + [(y1 - y0) / (x1 - x0)] × (x - x0)
```

Exemplo:

```text
x0 = 1, y0 = 10
x1 = 3, y1 = 20

Calcular f(2):
```

```text
f(2) = 10 + [(20 - 10)/(3 - 1)] × (2 - 1)

f(2) = 15
```

### Polinômio de Newton

Utiliza diferenças divididas para construir o polinômio interpolador.

Para três pontos:

```text
P(x) = f[x0]
     + f[x0,x1](x-x0)
     + f[x0,x1,x2](x-x0)(x-x1)
```

Diferença dividida de primeira ordem:

```text
f[x0,x1] = (f(x1) - f(x0))/(x1 - x0)
```

Diferença dividida de segunda ordem:

```text
f[x0,x1,x2] =
(f[x1,x2] - f[x0,x1])/(x2-x0)
```

### Grau do polinômio

| Pontos utilizados | Grau máximo |
|---|---|
| 2 pontos | 1 |
| 3 pontos | 2 |
| 4 pontos | 3 |
| 5 pontos | 4 |

**Na prova:** se a questão pedir polinômio de grau 3, normalmente utilizamos 4 pontos.

Se pedir para utilizar todos os 5 pontos, o polinômio interpolador terá grau no máximo 4.

---

# 10. Revisão Rápida — O Que Memorizar

| Assunto | Palavra-chave | O que fazer |
|---|---|---|
| Pesquisa Operacional | Otimização | Identificar objetivo e restrições |
| Simplex | Programação Linear | Maximizar ou minimizar |
| Dualidade | Primal e dual | Inverter objetivo e transpor restrições |
| Sensibilidade | Alteração de custos | Analisar impacto na solução |
| Prim | Rede mínima | Conectar todos com menor custo |
| Dijkstra | Caminho mínimo | Encontrar menor distância |
| Fluxo máximo | Capacidade | Maximizar fluxo na rede |
| Caixeiro Viajante | Visitar cidades | Menor circuito completo |
| Multicritério | Pesos | Comparar alternativas |
| Branch and Bound | Inteiros | Resolver otimização inteira |
| Newton | Interpolação | Estimar valores usando pontos |

---

# 11. Pegadinhas Frequentes

### 1. Caminho mínimo não é árvore geradora mínima

- Caminho mínimo conecta origem e destino.
- Árvore geradora mínima conecta todos os vértices.

### 2. Maximizar não significa necessariamente produzir mais unidades

O objetivo é obter o maior valor da função objetivo, respeitando as restrições.

### 3. Nem toda solução viável é ótima

Uma solução pode respeitar todas as restrições e ainda existir outra melhor.

### 4. O maior peso não determina sozinho a melhor alternativa

Em análise multicritério, precisamos avaliar os demais critérios e as relações de concordância e discordância.

### 5. Caixeiro viajante precisa visitar todas as cidades

No modelo clássico, deve visitar cada cidade uma vez e retornar à origem.

### 6. Variáveis inteiras não podem assumir valores fracionários

Se x representa quantidade de caminhões, valores como 3,5 não são permitidos.

### 7. Dualidade não é apenas inverter Max para Min

Também é necessário transpor a matriz de coeficientes e ajustar as restrições.

### 8. Polinômio de grau 3 utiliza quatro pontos

Para determinar um polinômio interpolador cúbico, são necessários quatro pontos com valores de x distintos.

---

# 12. Checklist Final para a Prova

- [ ] Saber identificar função objetivo e restrições.
- [ ] Diferenciar maximização de minimização.
- [ ] Entender a finalidade do Simplex.
- [ ] Saber construir a função objetivo dual.
- [ ] Entender análise de sensibilidade.
- [ ] Diferenciar Prim e Dijkstra.
- [ ] Saber calcular uma árvore geradora mínima.
- [ ] Entender o problema do caixeiro viajante.
- [ ] Reconhecer critérios de custo e benefício.
- [ ] Saber a finalidade do Branch and Bound.
- [ ] Reconhecer interpolação linear e polinomial.

---

## Dica final

Para questões com cálculos, siga sempre esta sequência:

1. Identifique o que o problema deseja otimizar.
2. Observe os valores fornecidos.
3. Identifique as restrições.
4. Escolha o método adequado.
5. Faça os cálculos.
6. Compare o resultado com as alternativas.

**Prioridade de revisão:** Simplex, Dualidade, Grafos, Caixeiro Viajante, Análise Multicritério e Interpolação.

Esses assuntos apareceram diretamente nos simulados e merecem atenção especial antes da prova.

