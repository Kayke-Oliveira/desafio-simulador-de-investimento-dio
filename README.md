<div align="center">

<a id="topo"></a>

# ◈ CAPITAL INVEST

### `SIMULE` · `COMPARE` · `PLANEJE`

**Uma ferramenta em Excel para transformar aportes mensais em projeções de patrimônio e renda com FIIs.**

[![DIO](https://img.shields.io/badge/DIO-Bootcamp-00C853?style=for-the-badge)](https://www.dio.me/)
[![Excel](https://img.shields.io/badge/Microsoft-Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)](https://www.microsoft.com/microsoft-365/excel)
[![Status](https://img.shields.io/badge/Status-Concluído-00C853?style=for-the-badge)](#aviso)

</div>

---

<img width="1029" height="252" alt="image" src="https://github.com/user-attachments/assets/27a49e0d-8681-44f6-815d-4a4804c17dff" />

> **Uma decisão mensal parece pequena. O tempo mostra o tamanho dela.**

O **Capital Invest** é o projeto final de um bootcamp da **DIO**: uma pasta de trabalho em branco transformada em uma pequena interface de simulação financeira, com o fluxo **informar → simular → comparar → entender**.

O usuário informa o salário, define o aporte, o período e a taxa, escolhe um perfil de investidor e visualiza o patrimônio projetado, os dividendos mensais e a distribuição do aporte entre seis tipos de FIIs.

A pasta de trabalho tem duas abas:

| Aba | Função |
|---|---|
| `capital_invest` | Interface principal: configuração, simulação, cenários, carteira e gráfico de pizza |
| `Apoio` | Chave composta (`Perfil-Tipo de FII`) e percentuais de cada perfil |

**Sumário**

1. [Visão rápida](#visao-rapida)
2. [Como utilizar a aplicação](#como-usar)
3. [Configuração e perguntas do desafio](#configuracao)
4. [Motor da simulação (VF)](#motor)
5. [PROCV e a planilha de apoio](#procv)
6. [Perfis e percentuais](#perfis)
7. [Diferenças em relação à aplicação do instrutor](#diferencas)
8. [Mesmo aporte, outra estratégia](#exemplo)
9. [Projeção de cenários](#cenarios)
10. [Intervalos nomeados](#intervalos)
11. [Conceitos aplicados e o desafio](#conceitos)
12. [Estrutura do repositório](#estrutura)
13. [Prints da ferramenta](#prints)
14. [Aviso importante](#aviso)

---

<a id="visao-rapida"></a>

## ◈ VISÃO RÁPIDA

| Entrada | Resultado |
|---|---|
| 💰 Aporte mensal | Patrimônio acumulado |
| ⏳ Período | Dividendos mensais |
| 📈 Taxa mensal | Projeções de 2 a 30 anos |
| 👤 Perfil | Distribuição entre tipos de FII |

Valores atuais salvos na planilha:

| Bloco | Campo | Célula | Valor |
|---|---|---|---|
| Configuração | Salário | `D12` | R$ 1.600,00 |
| Configuração | Rendimento Carteira *(informativo)* | `D13` | 0,89% ao mês |
| Configuração | Sugestão de Investimento (30%) | `D14` | R$ 480,00 |
| Investimento Mensal | Quanto quero investir por mês | `D18` | R$ 480,00 |
| Investimento Mensal | Período em anos | `D19` | 2 |
| Investimento Mensal | Taxa de rendimento mensal | `D20` | 1,075% ao mês |
| Investimento Mensal | Patrimônio acumulado | `D21` | R$ 13.063,05 |
| Investimento Mensal | Dividendos Mensais | `D22` | R$ 140,43 |
| Carteira | Perfil de Investidor | `D33` | Conservador *(lista suspensa)* |

---

<a id="como-usar"></a>

## ◈ COMO UTILIZAR A APLICAÇÃO

Abra o arquivo `SimuladorInvestimentoFinanceiro.xlsx` e trabalhe na aba **`capital_invest`**. A planilha é dividida em blocos, e o uso segue sempre a mesma regra: **você preenche as células de entrada e o restante é calculado automaticamente**.

| O que você preenche | O que a planilha calcula |
|---|---|
| `D12` Salário · `D13` Rendimento Carteira | `D14` Sugestão de Investimento (30%) |
| `D18` Aporte mensal · `D19` Período em anos · `D20` Taxa mensal | `D21` Patrimônio acumulado · `D22` Dividendos Mensais |
| `D33` Perfil de Investidor *(lista suspensa)* | `C37:D43` Percentual e valor por tipo de FII + gráfico de pizza |
| — | `C26:D30` Cenários de 2, 5, 10, 20 e 30 anos |

### Passo a passo

**1. Configure o perfil financeiro** (bloco `CONFIGURAÇÃO`)

Informe o **Salário** em `D12`. A **Sugestão de Investimento (30%)** (`D14`) é recalculada sozinha. O campo **Rendimento Carteira** (`D13`) é apenas informativo.

**2. Defina a simulação** (bloco `INVESTIMENTO MENSAL`)

- **Quanto quero investir por mês** (`D18`) — o aporte real, livre para ser maior ou menor que a sugestão;
- **Período em anos** (`D19`) — horizonte do investimento;
- **Taxa de rendimento mensal** (`D20`) — rentabilidade considerada nos cálculos.

**3. Leia os resultados**

**Patrimônio acumulado** (`D21`) e **Dividendos Mensais** (`D22`) se atualizam automaticamente a cada alteração. Não é preciso apertar nenhum botão nem arrastar fórmulas.

**4. Consulte os cenários** (bloco `CENÁRIOS`)

A tabela mostra patrimônio e dividendos projetados para **2, 5, 10, 20 e 30 anos** com a configuração atual.

**5. Monte a carteira** (bloco do perfil)

Escolha **Perfil de Investidor** (`D33`) na lista suspensa destacada em verde: `Conservador`, `Moderado` ou `Agressivo`. A tabela abaixo traz o **percentual sugerido** e o **valor em reais** de cada tipo de FII, com o total e o gráfico de pizza da composição.

**6. Compare estratégias**

Mantenha aporte, período e taxa fixos e troque apenas o perfil: a distribuição do dinheiro muda, o total permanece o mesmo.

> ⚠️ **Regra de ouro:** edite somente as células de entrada (`D12`, `D13`, `D18`, `D19`, `D20` e `D33`). As demais já contêm fórmulas — alterá-las quebra os cálculos da simulação.

---

<a id="configuracao"></a>

## ◈ CONFIGURAÇÃO E PERGUNTAS DO DESAFIO

A ferramenta foi construída para responder às cinco perguntas de negócio do desafio:

| # | Pergunta | Resposta da ferramenta |
|---|---|---|
| 01 | Quanto investir por mês? | Sugestão automática de **30% do salário** em `D14`; o valor usado na simulação é o campo **Quanto quero investir por mês** (`D18`) |
| 02 | Por quantos anos investir? | Campo **Período em anos** (`D19`), convertido em meses (`× 12`) para os cálculos |
| 03 | Qual taxa de rendimento mensal? | Campo **Taxa de rendimento mensal** (`D20`), aplicada diretamente no `VF` |
| 04 | Quanto patrimônio será acumulado? | **Patrimônio acumulado** (`D21`) e a tabela **Cenários** (`C26:D30`) |
| 05 | Quanto posso receber de dividendos? | **Dividendos Mensais** (`D22`) e a coluna **Dividendo** dos cenários (`D26:D30`), calculados sobre o patrimônio projetado |

> **Sugestão ≠ aporte da simulação**
>
> A sugestão é apenas um ponto de partida: `R$ 1.600,00 × 30% = R$ 480,00`. O campo **Quanto quero investir por mês** aceita qualquer valor (R$ 200,00 · R$ 750,00 · R$ 1.000,00 ...) e é ele que alimenta o `VF`, os cenários e a distribuição entre FIIs.

---

<a id="motor"></a>

## ◈ MOTOR DA SIMULAÇÃO · `VF`

A função `VF` (Valor Futuro) calcula o patrimônio acumulado com juros compostos:

```excel
=VF(taxa_rendimento_mensal; periodo_em_anos*12; aporte*-1)
```

| Argumento | Nome na planilha | Papel no cálculo |
|---|---|---|
| `taxa` | `taxa_rendimento_mensal` (`D20`) | Rendimento mensal da simulação |
| `nper` | `periodo_em_anos × 12` | Quantidade de meses |
| `pmt` | `aporte * -1` | Aporte mensal (sinal negativo = entrada de caixa) |
| `vp` | omitido (padrão `0`) | Sem aporte inicial |
| `tipo` | omitido (padrão `0`) | Aporte no fim do período |

**Onde o `VF` é usado:**

- **Investimento Mensal** (`D21`): patrimônio acumulado no período escolhido.
- **Cenários** (`C26:C30`): repete a mesma lógica para **2, 5, 10, 20 e 30 anos**.

Os dividendos mensais saem do patrimônio projetado:

```excel
=Patrimônio acumulado * taxa_rendimento_mensal
```

Assim, a ferramenta demonstra matematicamente o impacto do tempo e dos juros compostos.

---

<a id="procv"></a>

## ◈ `PROCV` · A PONTE ENTRE AS PLANILHAS

O `PROCV` conecta a **planilha principal** à **planilha de apoio**, onde fica a tabela de percentuais.

A busca usa uma **chave composta** montada na coluna `A` do apoio (`Perfil & "-" & Tipo de FII`):

```excel
=PROCV($D$33&"-"&B37; Apoio!$A:$D; 4; 0)
```

| Parte da fórmula | Função |
|---|---|
| `$D$33&"-"&B37` | Monta a chave, por exemplo `Conservador-Papel` |
| `Apoio!$A:$D` | Tabela de apoio com chave, perfil, tipo e percentual |
| `4` | Coluna de origem: o percentual |
| `0` | Correspondência exata |

Fluxo completo:

```text
PERFIL (D33)  +  TIPO DE FII (B37:B42)
              │
              ▼
   CHAVE COMPOSTA  →  "Conservador-Papel"
              │
              ▼
   TABELA Apoio!A:D  →  PROCV(...; 4; 0)
              │
              ▼
        PERCENTUAL
              │
              ▼
   PERCENTUAL × APORTE (D37:D42)  →  VALOR DESTINADO AO FII
              │
              ▼
   Total (D43)  +  gráfico de pizza da composição
```

O campo `Perfil de Investidor` (`D33`) é uma **lista suspensa de validação de dados** com as opções `Conservador`, `Moderado` e `Agressivo`. Ao trocar o perfil, os percentuais se atualizam sozinhos — nenhum valor precisa ser editado manualmente na tela principal.

---

<a id="perfis"></a>

## ◈ PERFIS E PERCENTUAIS

| Tipo de FII | 🟢 Conservador | 🟡 Moderado | 🔴 Agressivo |
|---|---:|---:|---:|
| Papel | 20% | 30% | 40% |
| Tijolo | 60% | 45% | 25% |
| Híbridos | 10% | 10% | 5% |
| FOFs | 10% | 5% | 5% |
| Desenvolvimento | 0% | 5% | 15% |
| Hotelarias | 0% | 5% | 10% |
| **TOTAL** | **100%** | **100%** | **100%** |

- 🟢 **Conservador** — maior foco em estabilidade.
- 🟡 **Moderado** — equilíbrio entre estabilidade e risco.
- 🔴 **Agressivo** — maior exposição a risco e volatilidade.

A escolha do perfil **não altera o valor total do aporte**: ela altera apenas **como esse aporte é distribuído** entre os tipos de FII.

---

<a id="diferencas"></a>

## ◈ DIFERENÇAS EM RELAÇÃO À APLICAÇÃO DO INSTRUTOR

A estrutura geral é a mesma apresentada no desafio pelo instrutor (Expert): mesmos blocos de interface, mesma função `VF` para patrimônio e cenários, mesmo `PROCV` com chave composta, os mesmos seis tipos de FII e os três perfis de investidor.

A diferença **consiste apenas na parte da porcentagem distribuída por perfil e categoria de FII**.

A opção foi consciente: em vez de reproduzir os percentuais do instrutor, a distribuição foi definida com base no **que cada categoria de FII representa** em termos de estabilidade, diversificação e risco.

### O que cada categoria representa

| Categoria | O que representa | 🟢 Conservador | 🟡 Moderado | 🔴 Agressivo |
|---|---|---:|---:|---:|
| 🏢 **Tijolo** | Base da carteira: ativos imobiliários físicos (logística, shopping, lajes, renda urbana) e contratos de locação de longo prazo | 60% | 45% | 25% |
| 📄 **Papel** | Recebíveis imobiliários (CRIs): dividendos potencialmente maiores, porém risco de crédito, inadimplência, juros, CDI e IPCA | 20% | 30% | 40% |
| 🔀 **Híbridos** | Combina imóveis físicos e ativos financeiros; categoria intermediária | 10% | 10% | 5% |
| 🧺 **FOFs** | Cotas de outros FIIs: diversificação automática com estrutura de custos adicional | 10% | 5% | 5% |
| 🏗️ **Desenvolvimento** | Obras, custos de construção, atrasos, execução de projetos e condições do mercado imobiliário | 0% | 5% | 15% |
| 🏨 **Hotelarias** | Turismo, sazonalidade, ocupação e condições econômicas | 0% | 5% | 10% |

### Progressão adotada

```text
🟢 CONSERVADOR  →  🟡 MODERADO  →  🔴 AGRESSIVO
   mais Tijolo       equilíbrio      mais Papel,
   menos Papel     entre os        Desenvolvimento
   e Hotelarias      extremos       e Hotelarias
```

- **↓ Tijolo** — menor exposição à base de estabilidade conforme o perfil fica mais agressivo;
- **↑ Papel** — mais exposição a recebíveis e risco de crédito;
- **↑ Desenvolvimento** — mais especulação;
- **↑ Hotelarias** — mais volatilidade.

O objetivo foi tornar a diferença entre as estratégias bem perceptível dentro da própria ferramenta: cada perfil passa a ter uma identidade clara, e a comparação entre os três (mantendo aporte, período e taxa fixos) mostra na prática o efeito da escolha.

---

<a id="exemplo"></a>

## ◈ MESMO APORTE, OUTRA ESTRATÉGIA

Com o aporte padrão de **R$ 480,00**, a mesma quantia é dividida de três formas:

| Tipo de FII | 🟢 Conservador | 🟡 Moderado | 🔴 Agressivo |
|---|---:|---:|---:|
| Papel | R$ 96,00 | R$ 144,00 | R$ 192,00 |
| Tijolo | R$ 288,00 | R$ 216,00 | R$ 120,00 |
| Híbridos | R$ 48,00 | R$ 48,00 | R$ 24,00 |
| FOFs | R$ 48,00 | R$ 24,00 | R$ 24,00 |
| Desenvolvimento | R$ 0,00 | R$ 24,00 | R$ 72,00 |
| Hotelarias | R$ 0,00 | R$ 24,00 | R$ 48,00 |
| **TOTAL** | **R$ 480,00** | **R$ 480,00** | **R$ 480,00** |

> **O dinheiro investido é o mesmo. A estratégia é diferente.**

---

<a id="cenarios"></a>

## ◈ PROJEÇÃO DE CENÁRIOS

Com a configuração atual da planilha (aporte de R$ 480,00 e taxa de 1,075% ao mês):

| Horizonte | Patrimônio | Dividendos mensais |
|---:|---:|---:|
| **2 anos** | R$ 13.063,05 | R$ 140,43 |
| **5 anos** | R$ 40.160,93 | R$ 431,73 |
| **10 anos** | R$ 116.444,10 | R$ 1.251,77 |
| **20 anos** | R$ 536.558,43 | R$ 5.768,00 |
| **30 anos** | R$ 2.052.273,25 | R$ 22.061,94 |

---

<a id="intervalos"></a>

## ◈ INTERVALOS NOMEADOS

A planilha usa intervalos nomeados para tornar as fórmulas legíveis (`=VF(taxa_rendimento_mensal; ...)` em vez de `=VF(D20; ...)`):

| Nome | Referência | Finalidade |
|---|---|---|
| `sugestao_aporte` · `sugestao_investimento` | `capital_invest!$D$14` | Sugestão inicial de 30% sobre o salário |
| `aporte` · `qnt_quero_investir` | `capital_invest!$D$18` | Aporte efetivo: alimenta `VF`, cenários e distribuição |
| `periodo_em_anos` | `capital_invest!$D$19` | Período da simulação em anos |
| `taxa_rendimento_mensal` | `capital_invest!$D$20` | Taxa usada no `VF` e no cálculo dos dividendos |
| `rendimento_carteira` | `capital_invest!$D$13` | Rendimento informativo da configuração |

---

<a id="conceitos"></a>

## ◈ CONCEITOS APLICADOS E O DESAFIO

O desafio da **DIO** partiu de uma pasta de trabalho em branco e pediu uma ferramenta com aparência de aplicativo, capaz de:

1. receber as configurações do investidor;
2. calcular o patrimônio acumulado;
3. projetar cenários de 2 a 30 anos;
4. distribuir o aporte entre seis tipos de FIIs;
5. alterar essa distribuição conforme o perfil selecionado.

Na prática, o projeto aplicou:

`VF` · `PROCV` · `Chave composta` · `Intervalos nomeados` · `Validação de dados` · `Referências absolutas` · `Tabelas de apoio` · `Gráfico de pizza` · `Juros compostos` · `Modelagem de dados` · `Design de planilhas`

Mais do que construir uma tabela, a proposta foi transformar o Excel em uma pequena **interface de simulação financeira**.

---

<a id="estrutura"></a>

## ◈ ESTRUTURA DO REPOSITÓRIO

```text
Capital-Invest/
│
├── 📊 SimuladorInvestimentoFinanceiro.xlsx
│      ├── aba capital_invest  (interface principal)
│      └── aba Apoio           (percentuais e chave composta)
│
├── 🖼️ docs/                   (prints e imagens deste README)
│
└── 📖 README.md
```

---

<a id="prints"></a>

## ◈ PRINTS DA FERRAMENTA

> **Espaço reservado para os prints das simulações** — adicione as imagens na pasta `docs/`.

| Simulação |

<img width="568" height="418" alt="image" src="https://github.com/user-attachments/assets/8f326be2-354d-4e37-958d-3ceb8bf44d44" />

| 🟢 Conservador | 

<img width="566" height="457" alt="image" src="https://github.com/user-attachments/assets/720f617d-1e86-4711-a21e-fab29141dee2" />

| 🟡 Moderado | 

<img width="566" height="453" alt="image" src="https://github.com/user-attachments/assets/b9d934cd-acb9-471a-9c8e-cbc216b147f3" />

| 🔴 Agressivo | 

<img width="567" height="451" alt="image" src="https://github.com/user-attachments/assets/ab8b5584-21a8-4ce3-ac80-73081450457b" />

---

<a id="aviso"></a>

## ◈ ⚠️ AVISO IMPORTANTE

Este projeto possui **finalidade exclusivamente educacional**.

As taxas, percentuais, projeções de patrimônio e estimativas de dividendos existem apenas para **simulação**. Os percentuais definidos para os perfis representam uma decisão de modelagem do projeto e **não constituem recomendação de investimento**.

Resultados simulados não garantem rentabilidade futura.

---

<div align="center">

<br>

**◈ CAPITAL INVEST** — *Simule o presente. Visualize o futuro.*

<br>

Desenvolvido como projeto final do **Bootcamp DIO**.

<br>

**[⬆ Voltar ao topo](#topo)**

</div>
