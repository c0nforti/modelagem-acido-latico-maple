# Modelagem e Simulação da Produção de Ácido Lático

Modelagem matemática e simulação numérica da produção de ácido lático utilizando o modelo de Luedeking-Piret com inibição pelo produto, desenvolvida em Maple.

## Objetivo

Este projeto tem como objetivo estudar, por meio de modelagem matemática e simulação numérica, o comportamento de um processo de produção de ácido lático em diferentes condições operacionais.

Foram analisados o comportamento cinético do processo, diferentes taxas de diluição, possíveis efeitos de multiplicidade, planos de fase e cenários de operação do reator.

## Modelo Matemático

O modelo considera três variáveis principais:

- **X** — concentração de biomassa
- **S** — concentração de substrato
- **P** — concentração de ácido lático

A taxa específica de crescimento é definida por:

$$
\mu =
\mu_{max}
\left(1-\frac{P}{P_{max}}\right)^n
\frac{S}{K_s+S}
$$

O sistema de equações diferenciais utilizado é:

$$
\frac{dX}{dt} = \mu X - DX
$$

$$
\frac{dS}{dt} =
D(S_{in}-S)-\frac{\mu X}{Y_{xs}}
$$

$$
\frac{dP}{dt} =
(\alpha\mu+\beta)X-DP
$$

onde `D` representa a taxa de diluição.

## Parâmetros

| Parâmetro | Valor |
|---|---:|
| μmax | 0.6 |
| Pmax | 80 |
| α | 1.5 |
| β | 0.1 |
| Yxs | 0.25 |
| Sin | 60 |
| Ks | 2 |
| n | 2 |

Condições iniciais utilizadas na simulação principal:

- `X₀ = 1`
- `S₀ = 60`
- `P₀ = 0`

## Resultados

### Cinética de Produção de Ácido Lático

O comportamento das principais variáveis do processo foi analisado por meio da simulação da cinética de produção.

![Cinética de Produção de Ácido Lático](resultados/cinetica/cinetica-producao-acido-latico.png)

### Cenários de Diluição

Foram analisados diferentes valores da taxa de diluição, incluindo:

- `D = 0.2`
- `D = 0.3`
- `D = 0.4`
- `D = 0.5`

Os resultados permitem observar como a alteração da taxa de diluição modifica a dinâmica da biomassa, do substrato e do produto.

Os gráficos individuais e as comparações entre diferentes taxas de diluição estão disponíveis na pasta [`resultados/cenarios-diluicao`](resultados/cenarios-diluicao/).

### Multiplicidade

Para investigar o comportamento do sistema em relação às condições iniciais, foram utilizadas duas condições iniciais distintas com `D = 0.18`.

As simulações convergiram para o mesmo estado estacionário nas condições analisadas, não evidenciando multiplicidade para os casos testados.

Os resultados gráficos da análise de multiplicidade estão disponíveis na pasta [`resultados/multiplicidade`](resultados/multiplicidade/).

### Planos de Fase

Foram construídos planos de fase para diferentes taxas de diluição, permitindo visualizar a evolução do sistema no espaço de estados.

Foram considerados:

- `D = 0.2`
- `D = 0.3`
- `D = 0.5`

Os gráficos dos planos de fase estão disponíveis na pasta [`resultados/planos-de-fase`](resultados/planos-de-fase/).

### Simulação Final

A simulação final considera diferentes regimes de operação ao longo do tempo:

1. Operação em batelada;
2. Operação com `D = 0.18`;
3. Alteração para `D = 0.5`.

Essa simulação foi utilizada para analisar a resposta dinâmica do sistema diante de mudanças na condição de operação.

O gráfico correspondente está disponível em [`resultados/simulacao-final`](resultados/simulacao-final/).

### Cenários Finais

#### Cenário A — D = 0.1

A redução da taxa de diluição favoreceu a manutenção da biomassa e a formação do produto, resultando em menor concentração de substrato residual ao longo da simulação.

![Cenário A](resultados/cenarios-finais/cenario-A-D-0.1.png)

#### Cenário B — D = 0.5

O aumento da taxa de diluição provocou uma redução significativa da biomassa e do ácido lático, acompanhada pelo aumento do substrato residual.

O comportamento observado foi utilizado para investigar o regime associado ao fenômeno de lavagem (washout). Entretanto, dentro do horizonte de simulação e dos parâmetros utilizados, a biomassa permaneceu diferente de zero.

![Cenário B](resultados/cenarios-finais/cenario-B-D-0.5.png)

## Conclusões

As simulações permitiram analisar a influência das condições operacionais sobre a dinâmica da produção de ácido lático.

A variação da taxa de diluição apresentou efeitos significativos sobre a biomassa, o substrato e o produto. Taxas de diluição menores favoreceram a permanência da biomassa e a formação do produto, enquanto valores maiores provocaram redução dessas concentrações e aumento do substrato residual.

A análise com diferentes condições iniciais apresentou convergência para o mesmo estado estacionário nos casos estudados, não evidenciando multiplicidade nas condições analisadas.

Os planos de fase e a simulação final complementaram a análise temporal, permitindo observar a dinâmica do sistema e sua resposta a mudanças nas condições de operação.

## Estrutura do Projeto

```text
modelagem-acido-latico-maple/
├── README.md
├── modelo/
│   └── modelo-acido-latico.mw
├── documentacao/
│   └── Trabalho Maple - v4.pdf
└── resultados/
    ├── cinetica/
    ├── cenarios-diluicao/
    ├── multiplicidade/
    ├── planos-de-fase/
    ├── simulacao-final/
    └── cenarios-finais/
```

## Tecnologias

- **Maple**
- Modelagem matemática
- Sistemas de equações diferenciais
- Simulação numérica
- Análise de sistemas dinâmicos

## Contexto Acadêmico

Projeto desenvolvido no contexto da formação em **Engenharia Eletrônica pela Universidade Federal de Pernambuco (UFPE)**.
