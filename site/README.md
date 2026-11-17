# Perfil ADMET da série 2l–3l — predições Deep-PK

Material suplementar do TCC. Predições de farmacocinética e toxicidade (ADMET) para
uma série de 15 ligantes candidatos a inibidores de DHODH (PDB 9XYG), comparadas a
600 decoys property-matched.

**→ [Painel interativo](https://SEU-USUARIO.github.io/admet-tcc/)**
· [Figuras](https://SEU-USUARIO.github.io/admet-tcc/figuras.html)

## O que está aqui

| | |
|---|---|
| `index.html` | painel interativo: 73 endpoints por ligante, com a distribuição dos decoys |
| `figuras.html` | as cinco figuras em 300 dpi, com legenda |
| `figuras/` | os PNGs em alta resolução |
| `dados/resultados_wide.csv` | 615 moléculas × 73 endpoints, dados brutos |
| `dados/efeito_ativos_vs_decoys.csv` | tamanho de efeito, p-valor e FDR por endpoint |

## Método

Predições pelo **Deep-PK** (Myung, de Sá & Ascher, 2024), submetidas via API em
4 lotes de até 200 moléculas. 73 endpoints: 8 absorção, 5 distribuição, 13 metabolismo,
3 excreção, 35 toxicidade e 9 propriedades gerais — 49 de classificação e 24 de regressão.

Conjunto: 15 ativos da série 2l–3l e 600 decoys gerados com **DeepCoy**, pareados por
massa molecular, logP, doadores/aceptores de ligação de hidrogênio e carga.

Comparação entre grupos: Mann-Whitney com Cliff's δ nos endpoints numéricos, teste
exato de Fisher nos categóricos, correção de Benjamini-Hochberg sobre os 73 testes.

## Principais resultados

- **30 dos 73 endpoints** separam ativos de decoys com FDR < 0,05; 25 deles permanecem
  ao excluir as 9 propriedades gerais, que são proxies do pareamento. O pareamento do
  DeepCoy não neutralizou o espaço ADMET.
- **Hepatotoxicidade (DILI I e II) e toxicidade respiratória** são preditas nos 15
  ligantes. hERG, CYP2D6, CYP3A4 e P-gp ficam praticamente limpos.
- A série é homogênea: desvio-padrão mediano de **0,71 σ** entre os 15 ligantes.

## Limitações

Os 15 ligantes são análogos de um mesmo scaffold. Os testes os tratam como observações
independentes, o que é pseudo-replicação — **os valores de FDR são otimistas** e devem
ser lidos como descritivos, não inferenciais.

Os SMILES estão na forma carboxilato (`C(=O)[O-]`); os valores de permeabilidade,
volume de distribuição e ligação a proteínas refletem a espécie aniônica.

Deep-PK foi treinado sobre dados agregados de ADMETlab 2.0, Interpretable-ADMET,
toxCSM e pkCSM, e portanto não constitui validação independente frente a essas
ferramentas. Predições in silico não substituem ensaio experimental.

## Como citar a ferramenta

> Myung Y, de Sá AGC, Ascher DB. Deep-PK: deep learning for small molecule
> pharmacokinetic and toxicity prediction. *Nucleic Acids Research*.
> 2024;52(W1):W469–W475. doi:10.1093/nar/gkae254
