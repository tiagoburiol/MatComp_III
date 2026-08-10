# Upgrade do curso Matemática Computacional III — acompanhamento

Este arquivo registra o plano geral do upgrade do material e o progresso feito, para retomar o trabalho em sessões futuras sem perder o contexto.

## Instruções gerais dadas pelo professor (início do projeto)

- Upgrade **completo** do material, mas feito **aos poucos, de forma controlada** — uma etapa de cada vez.
- Ordem de trabalho combinada:
  1. Primeiro reorganizar a **sequência e o escopo** do curso em 14 notebooks (feito — ver abaixo).
  2. Depois "recortar e remontar" o conteúdo já existente dentro dessa nova estrutura de 14 notebooks (feito — ver abaixo).
  3. Só então revisar o **conteúdo em si**, notebook por notebook, em um "ajuste fino" (numeração de seções/exemplos/atividades, correção de erros, remoção de redundâncias, texto, exercícios). Em andamento — ver "Próximos passos".
- Escopo completo do upgrade (para lembrar todas as frentes, mesmo as que ainda não começamos):
  - Corrigir bugs e erros técnicos no código.
  - Padronizar formatação entre notebooks (numeração de exemplos/atividades, seções, referências, cabeçalhos).
  - Revisar e melhorar o conteúdo pedagógico (explicações, motivação, progressão didática).
  - Limpar arquivos soltos do repositório (pastas antigas, versões duplicadas, notebooks sem numeração clara).
- Preferência de trabalho: notebooks com tamanho aproximadamente parecido entre si.
- Ao fazer o ajuste fino, **preservar as saídas (outputs) já executadas** pelo professor nos notebooks — só editar texto/células específicas, sem tocar em células de código já rodadas.

## Estrutura nova: de 11 para 14 notebooks

O curso tinha 11 notebooks. Foram reorganizados em 14, com a seguinte sequência e origem de conteúdo:

| Nº | Título | Escopo | Origem (notebooks antigos) |
|---|---|---|---|
| 1 | Séries numéricas | Sequências, séries, convergência experimental, séries telescópicas/geométricas/harmônicas, intuição de aproximar funções (Taylor/Fourier) | NB02 antigo + trecho reduzido do NB03 antigo |
| 2 | Testes de convergência de séries | Comparação, integral, razão, raiz — experimentos computacionais + SymPy | conteúdo novo (esqueleto criado, falta desenvolver) |
| 3 | Discretização, derivadas e integrais numéricas | Derivada/integral numérica com numpy/scipy, malhas 2D/3D | NB01 antigo completo |
| 4 | EDOs 1ª ordem: soluções analíticas com SymPy | Famílias de soluções, verificação, superposição, fator integrante, variáveis separáveis, exatas | NB04 + NB05 antigos (resumidos) |
| 5 | Método de Euler para EDOs 1ª ordem | Campo de direções + Euler | NB06 antigo completo |
| 6 | Taylor e Runge-Kutta para EDOs 1ª ordem | Taylor ordem 2, RK 1-4 | NB07 antigo completo |
| 7 | EDOs 2ª ordem com SymPy | Homogêneas, não-homogêneas, coeficientes indeterminados | NB08 antigo completo |
| 8 | EDOs 2ª ordem: métodos numéricos | Euler/Taylor estendidos via redução a sistema | conteúdo novo (esqueleto criado, falta desenvolver) |
| 9 | Diferenças finitas para EDOs 2ª ordem | Problemas de valor de contorno | NB09 antigo (sem a introdução de derivadas, já coberta no NB3) |
| 10 | Sistemas de EDOs: da ordem superior ao sistema | Reescrever EDO de ordem n como sistema, plano de fase introdutório | NB10 antigo (1ª metade) |
| 11 | Retratos de fase e pontos críticos | Exemplos completos: nó, sela, centro, espiral | NB10 antigo (2ª metade) |
| 12 | Autovalores e autovetores | Cálculo com SymPy/NumPy | NB11 antigo (parte 1) |
| 13 | Sistemas lineares via autovalores | Solução geral: reais distintos, complexos, repetidos | NB11 antigo (parte 2) |
| 14 | Estabilidade de sistemas lineares | Critérios de estabilidade, aplicações | NB11 antigo (parte 3) |

**Pontos de atenção conhecidos** (sinalizados também dentro dos próprios notebooks, em células de nota):
- Notebooks 11 e 14 têm conteúdo redundante entre si (ambos classificam pontos críticos: nó/sela/centro/espiral) — precisa resolver na revisão de conteúdo.
- Notebooks 1 e 3 ficaram os maiores (candidatos a corte adicional).
- Notebooks 2 e 8 são só esqueletos (título + descrição + 1 exemplo funcional por seção), aguardando desenvolvimento de conteúdo de verdade.

## O que foi feito

1. **Reorganização de arquivos:**
   - Os 11 notebooks antigos foram movidos com `git mv` para a pasta `Notebooks_v1_arquivo/` (histórico do git preservado, incluindo edições que já estavam em aberto/não commitadas).
   - Criadas as 14 novas pastas `Notebook 01 - ...` a `Notebook 14 - ...`, cada uma com subpasta `imagens/`.
   - Conteúdo de cada notebook novo montado por extração de células dos notebooks antigos (script Python ad-hoc, usando casamento de texto único para cortar nos pontos certos).
   - Nada foi commitado ainda — tudo está no working tree, pronto para revisão.

2. **Ajuste fino do Notebook 1 (Séries numéricas):**
   - O professor já tinha inserido conteúdo novo no notebook (nova introdução a sequências, Exemplo 1.2 com três formas de computar termos, Exemplo 1.3 de Fibonacci, uma seção de Exercícios no final).
   - Corrigida a numeração de seções (`### 1.1` a `1.6`), exemplos (`Exemplo 1.1` a `1.16`, sem lacunas nem duplicatas — havia dois pares indevidamente repetidos) e atividades (`Atividade 1.1` a `1.4`).
   - Corrigidas duas referências cruzadas no texto que citavam números antigos de exemplo.
   - Corrigidos typos: "cox(x)" → "cos(x)" (2x), "POr exemplo" → "Por exemplo", "coeficientes sāo" → "são", "eos" → "e os".
   - Outputs já executados pelo professor foram preservados (só células de markdown foram editadas).

3. **Ajuste fino do Notebook 2 (Testes de convergência de séries):**
   - Seção 2.5 (Usando SymPy para tratar séries) estava rasa (um único exemplo, atividade genérica sem itens) — desenvolvida com um segundo exemplo (`sp.apart` explicitando a telescopagem antes de somar com `sp.Sum`) e um terceiro que confirma simbolicamente a soma exata da série do Exemplo 2.1, além de uma atividade com dois itens lettered (a)/(b) remetendo a atividades anteriores.
   - Seção 2.4 (Teste da raiz) também estava rasa (um exemplo sem confirmação simbólica, atividade com uma única série) — adicionada confirmação simbólica via `sp.limit` ao exemplo existente, um segundo exemplo totalmente simbólico ($b_n=\left(\frac{3n+2}{4n+1}\right)^{2n}$) e a atividade expandida para três itens (a)/(b)/(c), o último ilustrando que um fator polinomial não altera o limite do teste da raiz.
   - Corrigida a numeração de exemplos (`Exemplo 2.1` a `2.11`, sequencial, sem reiniciar por subseção) e atividades (`Atividade 2.1` a `2.5`) para seguir o mesmo padrão do Notebook 1 — antes havia mistura de "Exemplo 1..9"/"Atividade 1..3" sem prefixo do notebook com "Atividade 2.4"/"2.5" já corretos.
   - Corrigidas três referências cruzadas no texto que citavam números antigos de exemplo/atividade.
   - Corrigidos typos: "SumPy" → "SymPy", "conver-gente" → "convergente", "calaculando" → "calculando", "ontenha" → "obtenha".
   - Todas as saídas novas foram calculadas via SymPy e conferidas rodando o notebook completo (`jupyter nbconvert --execute`) numa cópia de teste antes de aceitar os valores; outputs já existentes no notebook original foram preservados sem alteração.
   - Pendências que ficaram de fora por estarem fora do escopo pedido: pasta `imagens/` vazia e não referenciada (candidata a remoção), possível redundância entre a célula solta após a Atividade 2.2 e o enunciado da própria atividade.

## Próximos passos

- Seguir o ajuste fino notebook por notebook, a partir do **Notebook 3**.
- Ao final do ajuste fino de todos os 14, revisitar os pontos de atenção listados acima (redundância 11/14, tamanho de 1 e 3, limpeza de arquivos soltos do repositório como `MatComp_III_old/`, `MatComp_III_old2/`, `.ipynb_checkpoints/`).
- Decidir em algum momento se/quando commitar o progresso (nada commitado até o momento deste registro).
