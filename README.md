# 🔁 Estrutura de Dados — Recursividade e Torre de Hanói

Trabalho acadêmico da disciplina de **Estrutura de Dados** na **Fatec Taquaritinga**, com 3 questões resolvidas sobre **recursividade**, **Fibonacci recursivo** e o **algoritmo recursivo da Torre de Hanói**, com exemplos em **C#**.

📄 **Trabalho completo:** [`Trabalho_ED_Recursividade_Torre_de_Hanoi.docx`](Trabalho_ED_Recursividade_Torre_de_Hanoi.docx)

---

## 📋 Questões

| # | Tema | Conteúdo |
|---|---|---|
| 1 | 🔁 Recursividade | O que caracteriza uma função recursiva, caso base e o que acontece sem ele |
| 2 | 🐚 Fibonacci | A função recursiva e seus casos base |
| 3 | 🗼 Torre de Hanói | As regras, o algoritmo recursivo e o número de movimentos |

---

## 1️⃣ O que é recursividade

É quando uma **função chama a si mesma** para resolver versões menores do mesmo problema, até chegar a um caso simples.

**O que caracteriza uma função recursiva:**
- chama a si mesma dentro do próprio código;
- tem um **caso base**, que para as chamadas;
- tem um **caso recursivo**, que diminui o problema a cada chamada;
- guarda cada chamada na **pilha de execução** até chegar ao caso base.

**Caso base:** é a condição de parada, a situação mais simples, cuja resposta já é conhecida.

```csharp
static int Fatorial(int n)
{
    if (n == 0)                  // caso base
        return 1;
    return n * Fatorial(n - 1);  // caso recursivo
}
```

⚠️ **Sem caso base:** a função se chama para sempre (**recursão infinita**), a memória da pilha acaba e o programa quebra com **stack overflow** (`StackOverflowException` em C#).

---

## 2️⃣ Fibonacci recursivo

Cada termo é a soma dos dois anteriores: **0, 1, 1, 2, 3, 5, 8, 13...**

> F(n) = F(n − 1) + F(n − 2)

| Característica | Explicação |
|---|---|
| **Duas chamadas por vez** | Cada chamada chama `n − 1` e `n − 2` (recursão em árvore) |
| **Soma dos resultados** | O valor é a soma do que as duas chamadas devolvem |
| **Recalcula valores** | Simples, porém lenta: **O(2ⁿ)** |

**Casos base:** `F(0) = 0` e `F(1) = 1`

```csharp
static int Fibonacci(int n)
{
    // casos base: F(0) = 0 e F(1) = 1
    if (n <= 1)
        return n;
    // caso recursivo
    return Fibonacci(n - 1) + Fibonacci(n - 2);
}
```

**Árvore de chamadas de F(4):**

```
          F(4)
        /      \
     F(3)      F(2)
    /    \     /  \
  F(2)  F(1) F(1) F(0)
  /  \
F(1) F(0)
```

Resultado: **F(4) = 3**. O F(2) é calculado duas vezes. Dá para evitar esse retrabalho com **memorização** ou com uma versão iterativa.

---

## 3️⃣ Torre de Hanói

**3 pinos** (origem, auxiliar e destino) e **n discos** de tamanhos diferentes. O objetivo é levar todos os discos da origem para o destino.

**Regras:**
- mover só **um disco por vez**;
- mover só o disco que está **no topo**;
- um disco **maior nunca fica sobre um menor**.

### O algoritmo recursivo

| Etapa | Ação |
|---|---|
| 1 | Mover **n − 1** discos da origem para o **auxiliar** |
| 2 | Mover o **maior disco** da origem para o **destino** |
| 3 | Mover os **n − 1** discos do auxiliar para o **destino** |

**Caso base:** com **1 disco**, ele é movido direto para o destino.

```csharp
static void Hanoi(int n, char origem, char destino, char aux)
{
    if (n == 1)  // caso base
    {
        Console.WriteLine($"Disco 1: {origem} -> {destino}");
        return;
    }
    Hanoi(n - 1, origem, aux, destino);  // etapa 1
    Console.WriteLine($"Disco {n}: {origem} -> {destino}");  // etapa 2
    Hanoi(n - 1, aux, destino, origem);  // etapa 3
}
```

### Exemplo com 3 discos (A = origem, B = auxiliar, C = destino)

| Movimento | Disco | De → Para |
|---|---|---|
| 1º | 1 | A → C |
| 2º | 2 | A → B |
| 3º | 1 | C → B |
| 4º | 3 | A → C |
| 5º | 1 | B → A |
| 6º | 2 | B → C |
| 7º | 1 | A → C |

**Número mínimo de movimentos:** **2ⁿ − 1**. Com 3 discos são 7 movimentos; com 10 discos, 1.023. A complexidade é **O(2ⁿ)**.

---

## 🎓 Informações acadêmicas

| | |
|---|---|
| **Instituição** | Fatec Taquaritinga |
| **Curso** | Análise e Desenvolvimento de Sistemas — 3º semestre |
| **Disciplina** | Estrutura de Dados |
| **Professora** | Gislaine Cristina da Conceição |
| **Ano** | 2026 |

## 👥 Integrantes

- Juan Gabriel Pereira Augusto
- Vitor Gomes de Oliveira
