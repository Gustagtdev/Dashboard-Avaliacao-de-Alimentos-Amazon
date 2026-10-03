# Dashboard - Avaliação de Alimentos Amazon
Dashboard de duas páginas que analisa avaliações de produtos alimentícios da Amazon: evolução da nota, sentimento das reviews, utilidade percebida pelos leitores e crescimento do volume ao longo dos anos.

Objetivo: praticar o ciclo completo de análise de dados (tratamento, modelagem, DAX e visualização) com uma base real e "suja", como acontece no dia a dia.

## Perguntas de negócio:
Como a nota média das reviews evoluiu ao longo dos anos?
Qual a proporção de reviews positivas, neutras e negativas?
Quais produtos concentram mais reviews?
O volume de reviews cresce ou cai em relação ao ano anterior?
Quão úteis os leitores consideram as reviews? Isso muda conforme a nota?

## Base de dados:
Fonte: Amazon Fine Food Reviews (Kaggle)
Principais colunas usadas: ID do produto, ID do usuário, nome do perfil, nota (1 a 5), data da review (Unix timestamp), resumo, numerador e denominador de utilidade.
Período analisado: 1999 a 2012 (dados até 26/out/2012).

## Tratamento dos dados (Power Query)
Conversão da coluna de data (Unix timestamp) para data/hora.
Limpeza do nome do perfil: remoção de espaços e caracteres não imprimíveis, padronização de maiúsculas e minúsculas e tratamento de valores vazios.
Identificação de usuários pelo ID, não pelo nome: nomes se repetem (ex.: "Amazon Customer") e variam, então contagens e rankings usam o ID.
Tratamento dos IDs com prefixo #oc-, que se comportam como identificadores de review e não de usuário.
Modelo com tabela fato (FATO_REVIEWS) e tabela de datas para as medidas de inteligência de tempo.

## Principais insights
A nota média cai de forma gradual, de cerca de 5,0 nos primeiros anos para cerca de 4,1 em 2012.
Cerca de 78% das reviews são positivas, 16% negativas e 6% neutras.
O volume de reviews cresce em praticamente todos os anos, com a única queda em 2001.

## Limitações
Os primeiros anos (1999 a 2001) têm poucas reviews, então médias e variações percentuais dessa fase são pouco confiáveis. A variação de 800% em 2002, por exemplo, parte de uma base pequena.
2012 é um ano incompleto (dados até outubro), o que distorce a comparação com 2011.
O % Útil considera apenas quem votou, e reviews sem votos ficam de fora do cálculo.
A análise é descritiva: não investiga as causas da queda da nota média.

## Link do Dashboard
https://app.fabric.microsoft.com/view?r=eyJrIjoiMWQ0MjEyODUtMGY5MS00ZDViLWI0ZjMtMTM4Mzk3MGE3MzE3IiwidCI6IjQyNDgxYTM3LWZlZmQtNDNhMy1hOGI0LTQxZGY5Njk2M2EwMCJ9
