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

4. **Ajuste fino dos Notebooks 3 e 4:** feito e já commitado (commits `d0d5f01` — Notebook 3; `21a585d` — Notebook 4). O Notebook 4 ganhou também um caderno companheiro de questões Moodle resolvidas.

5. **Ajuste fino do Notebook 5 (Método de Euler para EDOs de 1ª ordem):**
   - O notebook era cópia quase literal do NB06 antigo (só o título mudara) e estava **sem nenhuma saída executada** — logo, o código pôde ser reescrito à vontade e o notebook foi reexecutado do zero no fim.
   - Removida a nota de reorganização, 3 células de código vazias e a propriedade inválida `outputs` que estava em todas as células markdown (resíduo do script de limpeza).
   - Removidas 2 imagens não usadas (`pendulo.png`, `runge_kutta_ordem_2.png`, esta última do NB06); links de imagem padronizados no estilo `raw.githubusercontent.com/.../refs/heads/main/...`.
   - Estrutura renumerada: `## 5` + seções `### 5.1` a `### 5.7` + `#### 5.3.1`; exemplos `Exemplo 5.1` a `5.4` (antes "6.1"–"6.4") com todas as referências cruzadas atualizadas; adicionadas `Atividade 5.1`–`5.3` distribuídas no corpo (padrão dos NB1–NB4).
   - Introdução de diferenças finitas enxugada (recall + ponteiro para o NB3), mantendo só o essencial para motivar o Euler.
   - Bugs corrigidos: tabela de erro do Exemplo 5.1 (comparava a aproximação em $t_{i+1}$ com a exata em $t_i$); solução exata do Exemplo 5.2 (`-5.x^4` → `-0,5x^4`); passo do Exemplo 5.3 (`h=0,20` no código vs. `0,25` no enunciado → `0,25`); `u(ti)-c` → `u(ti)+c`; fórmula `\frac{du}{dt}(t_i,t_i)` → `(t_i, u_i)`.
   - Adicionada a função reutilizável `euler(f, x0, y0, h, N)`, usada em todos os exemplos (antes cada exemplo reescrevia o laço de um jeito).
   - Nova Seção 5.4 "O erro do método de Euler e o efeito do passo $h$": tabela com a razão entre erros sucessivos (≈ 2) e gráfico log-log confirmando erro global $O(h)$.
   - Seção do SciPy reescrita para resolver o mesmo PVI do Exemplo 5.3 (antes usava um PVI solto e inconsistente) e comparar Euler × `solve_ivp` × exata.
   - Exemplo 5.4 (antes 6.4, SymPy + campo de direções) reenquadrado como "solução analítica × numérica", com a aproximação de Euler sobreposta ao campo de direções.
   - Typos: "Matemativamente" → "Matematicamente", "apoximação" → "aproximação", "segiuntes" → "seguintes", "distribuidos" → "distribuídos", "os passos são executadas" → "executados".
   - Notebook inteiro reexecutado com `jupyter nbconvert --execute`; sem erros.

6. **Questões Moodle do Notebook 5** (arquivos *gitignored* — `05_questoes_moodle*.xml` / `05_questoes_moodle_*.ipynb`, nunca entram em commit):
   - Conjunto criado em 2026-09-07: 5 questões de múltipla escolha sobre o método de Euler (`N05_Q1`…`N05_Q5`), nos 4 arquivos-padrão (`_moodle.xml` = enunciado + prompt + alternativas com MathML; `_alternativas.xml` = só o prompt "qual é verdadeira?" + as mesmas alternativas; `_enunciados.ipynb` = só os enunciados em markdown; `_resolvidas.ipynb` = gabarito, com código que confere cada opção e a marcação "Resposta correta: alternativa (a)", sempre a primeira na ordem do arquivo — o Moodle embaralha).
   - Revisão em 2026-09-08:
     - **Q1:** corrigida a inconsistência do passo (o enunciado dizia `h = 0,25`, o código e os números das alternativas usavam `h = 0,2`) → padronizado em `h = 0,2` (5 passos, `y(1) ≈ 2,98`, `E_abs ≈ 0,46`); justificativa reescrita (ainda estava na versão antiga com `h = 0,5`); typo "arelativo" → "relativo".
     - **Todas as alternativas** deixadas no padrão enxuto pedido pelo professor: apenas a afirmação (valor + rótulo), sem descrever como o valor errado foi obtido e sem justificativas. A explicação de por que cada distrator está errado fica só na célula de justificativa do `_resolvidas.ipynb`.
     - **Q3** convertida de comparação numérica para **questão gráfica**: o aluno plota solução exata × aproximação de Euler (PVI `y' = y − t²`, `y(0) = 2`, intervalo `[0, 2]`, `h = 0,4`, 5 passos, 6 pontos) e escolhe entre 4 gráficos. Distratores: (b) malha certa (6 pontos) mas erro reduzido à metade — subestimação boa demais para o passo; (c) `h = 0,5` (4 passos, 5 pontos) — malha mais grossa; (d) malha certa mas poligonal *acima* da solução exata. Imagens geradas com matplotlib e embutidas como `data:image/png;base64` direto no `<img>` dentro do CDATA das `<answer>` dos dois XML (sem arquivo `_imagem.xml` à parte). No `_resolvidas.ipynb`, a célula de código plota os quatro num grid 2×2.
     - **Q2, Q4, Q5:** conferidas contra a saída executada do código — exatamente uma alternativa verdadeira em cada, distratores plausíveis e falsos; dois pequenos ajustes de redação nas justificativas de Q2 e Q4.
     - `_moodle.xml` e `_alternativas.xml` mantidos idênticos no bloco de respostas; `_resolvidas.ipynb` reexecutado com `jupyter nbconvert --execute` (Q1–Q5 sem erros, saídas das demais questões inalteradas).

7. **Ajuste fino do Notebook 6 (Métodos de Taylor e Runge-Kutta para EDOs de 1ª ordem):**
   - Notebook era cópia quase literal do NB07 antigo, sem nenhuma saída executada e com `execution_count` fora de ordem — reescrito e reexecutado do zero (`jupyter nbconvert --execute`), sem erros.
   - Removida a nota de reorganização, 3 células de código vazias e as 6 imagens de `imagens/` não usadas neste notebook (`diffs.png`, `discretizacao.png`, `euler_fig01.png`, `euler_fig02.png`, `pendulo.png`, `pvi01.png` — herança do NB antigo; só `runge_kutta_ordem_2.png` é referenciada).
   - Bugs de conteúdo corrigidos: solução exata errada no enunciado do Exemplo 6.1 (`e^x-x+1` → `e^{-x}+x+1`, o código já usava a certa); resto de Taylor com $(x-\xi)^{p+1}$ e intervalo $x_0<\xi<x$ → corrigido para $h^{p+1}$ e $x_n<\xi<x$; fórmula de $y'''$ sem o termo $f_xf_y$; "=" → "≈" após truncamento; coeficientes $c_1,c_2,a_2$ do Euler modificado introduzidos sem contexto → método reescrito direto, sem a família ad-hoc; referência a "seção 6" (Euler) → "Notebook 5"; afirmação vaga de que os métodos de 2ª ordem dão resultados "de mesma ordem de grandeza" → substituída pela explicação correta (para $f$ afim eles **coincidem exatamente**; verificado simbolicamente) com um exemplo não linear ($y'=xy$) mostrando que, em geral, aperfeiçoado e modificado diferem; item 5 dos exercícios ("repita o Exercício 4") corrigido para "repita o Exercício 2" (a redação original era circular).
   - Numeração refeita: `## 6` + `### 6.1`/`6.2`/`6.3`/`6.4`/`6.5` + `#### 6.1.1`/`6.2.1`/`6.2.2`; exemplos `Exemplo 6.1`–`6.6` (antes "7.1", "7.2"×2, "7.3", "1.14"); `Atividade 6.1`–`6.2` adicionadas no padrão dos NB1–5 (enunciado sem solução); a antiga "Atividade 1" (que já vinha com solução completa) foi promovida a **Exemplo 6.2**, resolvida com o helper simbólico geral.
   - Funções reutilizáveis adicionadas (mesmo padrão do `euler()` do NB5): `taylor2_formula`/`taylor_formula(dy, var, y, p)` (deriva a recorrência de Taylor de qualquer ordem via SymPy — verificada simbolicamente contra a fórmula manual e usada para resolver os exercícios que pedem Taylor de 4ª ordem), `tabela_erro`, `rk2_aperfeicoado`, `rk2_modificado`, `rk3`, `rk4` — eliminando a repetição do laço a cada exemplo. Removidas as dependências ocultas de variáveis entre células (`Xe`/`Ye`), imports duplicados e o `f`/`y` reaproveitados com tipos diferentes.
   - Nova Seção 6.1.1 (Taylor de ordem $p$ geral) e Seção 6.3 (comparação de ordem): tabela de razão entre erros sucessivos e gráfico log-log para Euler/RK2/RK3/RK4, confirmando $O(h^p)$ para $p=1,2,3,4$.
   - Seção do SciPy: corrigido o uso de `Xe`/`Ye` de célula anterior e adicionado parágrafo sobre passo adaptativo do `RK45`.
   - Typos: "recorrênica" → "recorrência", "Darezo" → "Darezzo" (2×), "é dado po" → "é dado por", "$k4$" → "$k_4$".
   - Seção de Referências adicionada ao final (Arenales/Darezzo e Burden/Faires, no padrão ABNT do restante do curso), preservando pequenos ajustes de texto que o professor já tinha feito no notebook nesse meio-tempo (formatação das fórmulas de $k_1,k_2,k_3,k_4$ do RK3/RK4 em linhas separadas).
   - Notebook reexecutado do zero e commitado (commit `9efbaad`).
   - `06_taylor_e_runge_kutta_SOLVED.ipynb` — arquivo não rastreado pelo git, quase idêntico ao notebook principal mas sem a resolução da antiga Atividade 1 (nome sugere o oposto) — **intocado a pedido explícito do professor** ("não faça nada com o SOLVED"); não é mais uma pendência a decidir, é para deixar como está.

8. **Questões Moodle do Notebook 6** (arquivos *gitignored* — `06_questoes_moodle*.xml` / `06_questoes_moodle_*.ipynb`, nunca entram em commit):
   - Conjunto criado em 2026-09-14: 5 questões de múltipla escolha cobrindo Taylor de ordem 2, RK2 (aperfeiçoado × modificado em EDO não afim), RK4 (questão gráfica), e comparação de ordem RK2×RK4 e RK3×RK4 (`N06_Q1`…`N06_Q5`), nos 4 arquivos-padrão do NB5 (`_moodle.xml`, `_alternativas.xml`, `_enunciados.ipynb`, `_resolvidas.ipynb`).
   - PVIs novos, distintos dos usados como exemplo dentro do próprio NB6 (exceto Q4/Q5, que reaproveitam o PVI $y'=x-y+2$ do notebook, como o NB5 também faz na sua Q4): $y'=2x-y$ (Q1), $y'=xy$ (Q2, não afim — testa que RK2 aperfeiçoado e modificado não precisam coincidir), $y'=y-x^2+1$ (Q3, PVI clássico de Burden/Faires).
   - Q3 é questão gráfica (RK4 × solução exata), no mesmo esquema da Q3 do NB5: 4 imagens geradas com matplotlib e embutidas como `data:image/png;base64` direto nos dois XML; no `_resolvidas.ipynb` a célula de código plota as quatro num grid 2×2.
   - Todos os valores numéricos das alternativas foram calculados em Python e conferidos contra a saída executada do `_resolvidas.ipynb` (`jupyter nbconvert --execute`, sem erros); alternativas mantidas no padrão enxuto (só a afirmação, sem justificar o valor errado — a explicação de cada distrator fica só no `_resolvidas.ipynb`).
   - `_moodle.xml` e `_alternativas.xml` idênticos no bloco de respostas, diferindo apenas no enunciado (completo × só o prompt "qual é verdadeira?"), como no padrão do NB5.

## Próximos passos

- Seguir o ajuste fino notebook por notebook, a partir do **Notebook 7** (EDOs de 2ª ordem com SymPy).
- Ao final do ajuste fino de todos os 14, revisitar os pontos de atenção listados acima (redundância 11/14, tamanho de 1 e 3, limpeza de arquivos soltos do repositório como `MatComp_III_old/`, `MatComp_III_old2/`, `.ipynb_checkpoints/`).
- Notebooks 3, 4, 5 e 6 já com ajuste fino feito e commitado (NB5 = commits `392b1bb`, `39e27bb`, `aae3210`; NB6 = commit `9efbaad`). As questões Moodle do NB5 (item 6) e do NB6 (item 8) foram revisadas mas são arquivos *gitignored* — não entram em commit.
