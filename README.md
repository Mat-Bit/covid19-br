# covid19-br

Esse repositório centraliza links e dados sobre boletins de número de casos das
secretarias de saúde estaduais sobre a pandemia de coronavírus no Brasil. O
recorte é por município por dia, para acompanharmos localmente a evolução da
propagação do vírus.

## Licença

A licença do código é [LGPL3](https://www.gnu.org/licenses/lgpl-3.0.en.html) e
dos dados convertidos [Creative Commons Attribution
ShareAlike](https://creativecommons.org/licenses/by-sa/4.0/). Caso utilize os
dados, **cite a fonte original e quem tratou os dados**, como: **Fonte:
Secretarias de Saúde das Unidades Federativas, dados tratados por Álvaro
Justen/[Brasil.IO](https://brasil.io/)**. Caso compartilhe os dados, **utilize
a mesma licença**.

## Dados

Depois de coletados e checados os dados ficam disponíveis de 3 formas no
[Brasil.IO](https://brasil.io/):

- [Interface Web](https://brasil.io/dataset/covid19) (feita para humanos)
- [API](https://brasil.io/api/dataset/covid19) (feita para humanos que desenvolvem programas) - [veja a documentação da API](api.md)
- [Download do dataset completo](https://data.brasil.io/dataset/covid19/_meta/list.html)

Caso queira acessar os dados antes de serem publicados (ATENÇÃO: pode ser que
não tenham sido checados), você pode [acessar diretamente as planilhas em que
estamos
trabalhando](https://drive.google.com/open?id=1l3tiwrGEcJEV3gxX0yP-VMRNaE1MLfS2).

Se esse programa e/ou os dados resultantes foram úteis a você ou à sua empresa,
**considere [fazer uma doação ao projeto Brasil.IO](https://brasil.io/doe)**,
que é mantido voluntariamente.


### FAQ SOBRE OS DADOS

**Antes de entrar em contato conosco (estamos sobrecarregados) para tirar
dúvidas sobre os dados, [CONSULTE NOSSO FAQ](faq.md).**

Para mais detalhes [veja a metodologia de coleta de
dados](https://drive.google.com/open?id=1escumcbjS8inzAKvuXOQocMcQ8ZCqbyHU5X5hFrPpn4).


## Contribuindo

Você pode contribuir de diversas formas:

- Coletando links para os boletins de seu estado;
- Coletando dados sobre os casos por município por dia;
- Entrando em contato com a secretaria estadual de seu estado, sugerindo as
  [recomendações de liberação dos dados](recomendacoes.md);
- Evitando contato com humanos;
- Lavando as mãos várias vezes ao dia;
- Sendo solidário aos mais vulneráveis;

Para se voluntariar, [siga estes passos](CONTRIBUTING.md).

Procure o seu estado [nas issues desse
repositório](https://github.com/turicas/covid19-br/issues) e vamos conversar
por lá.

## Instalando

Necessita de Python 3 (testado em 3.8.2). Para montar seu ambiente:

- Instale o Python 3.8.2
- Crie um virtualenv
- Instale as dependências: `pip install -r requirements.txt`
- Rode o script de coleta: `./collect.sh`
- Rode o script de consolidação: `./run.sh`

Verifique o resultado em `data/output`.

## VEJA TAMBÉM

- [Outros datasets relevantes](datasets-relevantes.md)
- [Recomendações para secretarias de saúde na disponibilização de
  dados](recomendacoes.md)

## Clipping

Outros projetos e/ou notícias na rede que referenciam este projeto.

### Análises e Projetos

- [25/03/2020 - Análise Descritiva do Coronavírus nos Estados Brasileiros](https://marcusnunes.me/posts/analise-descritiva-do-coronavirus/)
- [Visualização em Mapa Interativo - GitHub @endoedgar](https://endoedgar.github.io/covid19-monitorbr/)
- [liibre/coronabr](https://liibre.github.io/coronabr/index.html)
- [Observatório de Dados :: COVID-19 no Brasil CCSL-UFPA](http://ccsl.ufpa.br/covid-19/)
- [Mapa do Covid-19 no Brasil - Hitalo Silva](https://covid19.hitalos.com)

### Notícias

- [25/03/2020 - Folha de São Paulo - Brasil tem ao menos 172 cidades com casos confirmados de coronavírus](https://www1.folha.uol.com.br/cotidiano/2020/03/brasil-tem-ao-menos-172-cidades-com-casos-confirmados-de-coronavirus.shtml)
- [24/03/2020 - Metrópole - Covid-19: Ministério da Saúde divulga menos casos que secretarias](https://www.metropoles.com/brasil/saude-br/covid-19-ministerio-da-saude-divulga-menos-casos-que-secretarias)
- [23/03/2020 - CNN Brasil - Boletins estaduais indicam quase 40 casos de coronavírus a mais do que governo](https://www.cnnbrasil.com.br/saude/2020/03/23/boletins-estaduais-indicam-quase-40-casos-de-coronavirus-a-mais-do-que-governo)

## Atualização dos Dados no Brasil.IO

Crie um arquivo `.env` com os valores corretos para as seguintes variáveis de
ambiente:

```shell
BRASILIO_SSH_USER
BRASILIO_SSH_SERVER
BRASILIO_DATA_PATH
BRASILIO_UPDATE_COMMAND
```

Execute o script:

`./deploy.sh`

Ele irá coletar os dados das planilhas (que estão linkadas em
`data/boletim_url.csv` e `data/caso_url.csv`), adicionar os dados ao
repositório, compactá-los, enviá-los ao servidor e executar o comando de
atualização de dataset.

> Nota: o script que baixa e converte os dados automaticamente deve ser
> executado separadamente, com o comando `./collect.sh`.
