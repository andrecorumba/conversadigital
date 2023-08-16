# 5. Carga de Dados de Emendas Parlamentares usando Python e Pandas

*Observação: parte deste texto foi escrita pelo modelo gpt-3.5-turbo.*

No cenário atual de transparência e acesso à informação, o uso de ferramentas tecnológicas tornou-se essencial para a análise e compreensão de dados governamentais. Nesse contexto, o carregamento e manipulação de dados de emendas parlamentares ganham destaque, permitindo aos cidadãos e pesquisadores uma visão mais clara sobre como essas emendas são alocadas e utilizadas. Neste artigo, exploraremos como realizar essa tarefa utilizando a linguagem de programação Python e a biblioteca Pandas.

## O Portal da Transparência

O Portal da Transparência do Governo Federal, https://portaldatransparencia.gov.br, é uma plataforma digital fornecida pelo governo federal para disponibilizar informações sobre a execução orçamentária e financeira, permitindo que cidadãos e entidades fiscalizem os gastos públicos de forma mais direta.

## Dados abertos de Emendas Parlamentares

Os dados abertos de emendas parlamentares são conjuntos de informações que detalham como os parlamentares direcionam recursos do orçamento para ações específicas, como obras, projetos sociais e investimentos. Esses dados proporcionam uma visão das alocações de recursos e auxiliam na análise da atuação dos representantes eleitos.

Os dados de emendas parlamentares da União estão disponíveis na parte de dados abertos do Portal da Transparência em:
https://portaldatransparencia.gov.br/download-de-dados/emendas-parlamentares

![Emendas](/docs/imagens/emendas.png)

## A Linguagem de Programação Python

Python é uma linguagem de programação amplamente utilizada devido à sua simplicidade e versatilidade. Com uma sintaxe legível e expressiva, Python se tornou uma escolha popular para análise de dados e automação de tarefas. Ela faz uso de uma gama de bibliotecas implementadas para fins específicos dentro da linguagem. O interpretador Python pode ser baixado em: https://www.python.org.

## A Biblioteca Pandas

Pandas é uma biblioteca Python amplamente adotada para análise de dados. Ela oferece estruturas de dados flexíveis e eficientes, como o DataFrame, que permite manipular e analisar dados de forma intuitiva. A bibloteca Pandas pode ser instalada no Python por meio do comando: `pip install pandads` e a chamada no código por meio da linha `import pandas as pd`.

## No que a biblioteca Pandas difere do Excel no dia-a-dia?

Enquanto o Excel é uma ferramenta poderosa para análise de dados, o Pandas se destaca por possibilitar análises mais complexas e automatizadas. Ele suporta manipulação de grandes volumes de dados, automação de processos e integração com outras bibliotecas de análise e visualização.

## O Projeto Jupyter Notebook

O Projeto Jupyter Notebook, https://jupyter.org,  é uma aplicação que permite a criação e compartilhamento de documentos interativos contendo código, visualizações e textos explicativos. É amplamente utilizado na análise de dados e na pesquisa científica.

## O que é o Google Colab?

O Google Colab é uma ferramenta poderosa, baseada em nuvem, para desenvolvimento em Python, especialmente quando se trata de análise de dados, aprendizado de máquina e visualização. Ele oferece recursos como acesso a GPUs, "Graphics Processing Unit" (Unidade de Processamento Gráfico) e TPUs, "Tensor Processing Unit" (Unidade de Processamento de Tensores) para acelerar o processamento de dados e treinamento de modelos. Com essas etapas básicas, você estará pronto para explorar e analisar dados de emendas parlamentares de maneira eficiente e colaborativa.

Para carregar os dados de emendas parlamentares no Google Colab, podemos usar a biblioteca Pandas e as funções de leitura de dados, como `read_csv()` ou `read_excel()`, dependendo do formato dos dados fornecidos.

Para acessar o Google Colab é necessário possuir uma conta no Google. 

## Carregando os dados no Google Colab

A seguir constam passos básicos para usar o Google Colab, um ambiente baseado em nuvem para desenvolvimento em Python utilizando Jupyter Notebooks:

1. **Acesso ao Google Colab**:
   Acesse o Google Colab através do link [https://colab.research.google.com/](https://colab.research.google.com/). Você precisará estar logado em uma conta do Google para começar.

2. **Criar um Novo Notebook**:
   No Colab, você pode criar um novo notebook do zero ou fazer o upload de um notebook existente a partir do seu computador ou diretamente de um repositório no GitHub.

3. **Ambiente de Notebook**:
   O ambiente do notebook é dividido em células, que podem conter código, texto ou visualizações. Você pode adicionar uma nova célula clicando no botão "+ Código" ou "+ Texto" na barra de ferramentas.

4. **Escrevendo Código**:
   Nas células de código, você pode escrever código Python. Para executar o código em uma célula, clique no botão "Play" à esquerda da célula ou use o atalho "Shift + Enter". O resultado da execução será exibido logo abaixo da célula.

5. **Instalando Pacotes**:
   Se precisar instalar pacotes adicionais, basta usar o comando `!pip install nome_do_pacote` em uma célula de código e executá-la. O Colab permite a instalação de pacotes diretamente no ambiente.

6. **Uso de Bibliotecas**:
   Importe bibliotecas, como o Pandas, usando os comandos usuais. Por exemplo: `import pandas as pd`.

7. **Carregando Dados**:
   Você pode carregar dados no Colab a partir do seu próprio computador, do Google Drive ou diretamente da web. Por exemplo, para carregar um arquivo CSV usando o Pandas:
   
   ```python
   import pandas as pd
   df = pd.read_csv("/content/Emendas.csv", sep=";", encoding="latin-1")
   df.head()
   ```

8. **Visualizações e Análises**:
   O Colab é ótimo para criar visualizações e realizar análises exploratórias de dados. Use bibliotecas como Matplotlib, Seaborn ou Plotly para criar gráficos e plots informativos.

9. **Salvar e Compartilhar**:
   Você pode salvar seu notebook no Google Drive ou fazer o download dele em vários formatos, incluindo .ipynb, .py e .html. Além disso, você pode compartilhar seu notebook com outras pessoas através do link de compartilhamento.

10. **Persistência**:
   O ambiente do Colab é temporário, e o ambiente de execução (incluindo os arquivos carregados) pode ser reiniciado após algum tempo de inatividade. Certifique-se de salvar seus resultados e códigos regularmente.


## O que é um Data Frame Pandas?

Um DataFrame é uma estrutura de dados bidimensional oferecida pela biblioteca Pandas. Ele se assemelha a uma planilha, permitindo a organização e análise de dados de maneira tabular. Cada coluna em um DataFrame pode ter um tipo de dado diferente.

## Limpeza dos dados

A fase de limpeza dos dados é uma etapa que consome grande parte do tempo de um Analista de Dados.

No caso das emendas faz necessário alterar os campos de valores que estão como string para float, usando o método .astype() com substituição de vírgulas por pontos. Um exemplo de limpeza no campo `'Valor Empenhado'`

```python
df['Valor Empenhado'] = df['Valor Empenhado'].str.replace(',', '.').astype(float)
```

## Operações simples e consultas no Data Frame

Após carregar os dados em um DataFrame, podemos realizar diversas operações e consultas para obter informações específicas. Podemos filtrar dados, agrupar informações, calcular estatísticas e criar visualizações, tudo isso de forma eficiente utilizando a sintaxe e os métodos fornecidos pelo Pandas.

Seguem alguns tipos de filtros que podem ser usados:


- **Filtrar com base em uma condição simples**:
   
Vamos supor que queremos apenas as emendas com valor empenhado maior que 1 milhão de reais:

```python
filtro = df['Valor Empenhado'] > 1000000
df[filtro].head()
```

- **Filtrar com base em múltiplas condições**:

Suponha que queremos as emendas com valor maior que 1 milhão para o município de Campo Grande-MS:

```python
filtro = (df['Valor Empenhado'] > 1000000) & (df['Localidade do gasto'] == 'CAMPO GRANDE - MS')
df[filtro].head()
```

- **Filtrar com base em valores em uma lista**:

Suponha que queremos as emendas de três municípios em uma lista específica:

```python
lista_de_municipios = ['CAMPO GRANDE - MS', 'CORUMBÁ - MS', 'AREIAS - SP']
filtro = df['Localidade do gasto'].isin(lista_de_municipios)
df[filtro]
```

- **Filtrar com base em uma string parcial**:

Suponha que queremos toda as emendas do parlamentar cujo nome começa com ROSE:

```python
filtro = df['Nome do Autor da Emenda'].str.startswith('ROSE')
df[filtro].head()
```

Esses são apenas alguns exemplos de como você pode filtrar DataFrames usando Pandas. A biblioteca oferece muitas outras opções e métodos para realizar operações de filtragem, seja por condições simples, múltiplas condições ou outros critérios específicos aos seus dados.

## Conclusão

Em resumo, a combinação do Python e da biblioteca Pandas oferece uma abordagem poderosa e flexível para carregar, manipular e analisar dados de emendas parlamentares. O uso de ambientes como o Google Colab e técnicas como o Projeto Jupyter Notebook possibilita uma análise interativa e visualmente rica, contribuindo para uma compreensão mais profunda das decisões orçamentárias dos representantes eleitos. Com essas ferramentas ao alcance, os cidadãos têm a oportunidade de se tornarem participantes ativos na fiscalização e no acompanhamento do uso dos recursos públicos.