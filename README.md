# UnderstandingAI: Laboratório Virtual de IA Supervisionada
## Acesse a aplicação

**[Entendendo IA Supervisionada](https://entendendo-ia.streamlit.app/)**
<br>
**[Entendendo IA Não supervisionada](https://entendendo-ia-naosupervisionada.streamlit.app/)**
<br>
Aplicação web educacional, construída em Python com Streamlit, que mostra de forma visual e interativa como funcionam os modelos de Aprendizado de Máquina.

O objetivo não é criar um sistema de previsão, mas sim uma ferramenta de ensino: o usuário acompanha cada etapa do processo, do carregamento dos dados até a previsão final, observando o modelo aprender passo a passo, como em um laboratório virtual.


## Principais funcionalidades

- Jornada guiada em 6 etapas, com barra de progresso e navegação por botões
- Leitura dos dados a partir de um arquivo CSV externo
- Detecção automática do papel de cada coluna do CSV (identificação, features e label)
- Funciona com qualquer CSV: qualquer assunto, qualquer quantidade de linhas e qualquer quantidade de features
- Seleção interativa das features que o modelo poderá usar
- Divisão dos dados em treino e teste com slider de porcentagem e sorteio dos grupos

## Como o laboratório entende qualquer CSV

Ao carregar um arquivo, a aplicação observa cada coluna e deduz o papel dela usando três regras simples:

- Identificação (opcional): coluna de texto em que cada linha tem um valor diferente, como um nome ou código. Serve apenas para identificar o registro e não entra no treinamento. Se não existir, as linhas são numeradas automaticamente.
- Features (entradas): todas as colunas numéricas. São as pistas que o modelo pode usar para aprender.
- Label (saída): coluna com poucas categorias que se repetem. É a resposta que o modelo aprende a prever. Funciona com duas ou mais categorias.

Requisito mínimo do CSV: pelo menos uma coluna numérica (feature) e uma coluna de categorias (label).

A interface inteira se adapta ao arquivo carregado. Com muitas features, os checkboxes viram uma lista de seleção múltipla e o gráfico ganha seletores de eixos. Com muitos registros, as etiquetas dos grupos são resumidas. Os sliders da etapa de previsão aceitam números inteiros e decimais, com limites derivados dos próprios dados.

## Requisitos

- Python 3.10 ou superior
- Bibliotecas listadas em requirements.txt: streamlit, pandas, scikit-learn e matplotlib

## Instalação e execução

Clone o repositório:

```bash
git clone https://github.com/seu-usuario/laboratorio-virtual-ia.git
cd laboratorio-virtual-ia
```

Crie um ambiente virtual (opcional, mas recomendado):

```bash
python -m venv .venv
source .venv/bin/activate        # Linux e macOS
.venv\Scripts\activate           # Windows
```

Instale as dependências:

```bash
pip install -r requirements.txt
```

Execute a aplicação:

```bash
streamlit run app.py
```

O navegador abrirá automaticamente em http://localhost:8501. O arquivo dados.csv precisa estar na mesma pasta do app.py.

## Usando seus próprios dados

Existem duas formas de trocar os dados:

1. Editar o arquivo dados.csv diretamente (adicionar linhas, mudar valores, renomear colunas) e recarregar a página.
2. Enviar qualquer outro CSV pela barra lateral da aplicação, sem reiniciar nada. O laboratório detecta as novas colunas e reorganiza tabelas, gráficos, textos e sliders sozinho.

Exemplo de formato aceito (o CSV de exemplo incluído no projeto):

```csv
Aluno,Nota Matemática,Frequência (%),Horas de Estudo,Situação
Ana,92,98,12,Aprovado
Bruno,45,70,2,Reprovado
Carlos,80,95,8,Aprovado
```

Nesse caso, a coluna Aluno é detectada como identificação, as três colunas numéricas viram features e a coluna Situação vira o label. Mas o mesmo funcionaria para pacientes e diagnósticos, produtos e categorias, times e resultados, ou qualquer outro tema.

## Conceitos ensinados

Ao percorrer o laboratório, o estudante entra em contato com os seguintes conceitos de Machine Learning:

- Inteligência Artificial e Aprendizado de Máquina
- Aprendizado supervisionado e não supervisionado e exemplos rotulados
- Features (entradas) e label (saída)
- Divisão dos dados em treino e teste
- Árvore de Decisão e como ela escolhe suas perguntas
- Importância das features
- Acurácia e avaliação em dados nunca vistos
- Generalização versus memorização
- Inferência: uso do modelo treinado para prever casos novos

## Contribuindo

Contribuições são bem-vindas. Sinta-se à vontade para abrir uma issue com sugestões ou relatos de problemas, ou enviar um pull request com melhorias, como novos algoritmos, novas visualizações ou traduções.

## Licença

Este projeto está licenciado sob a licença MIT. Consulte o arquivo LICENSE para mais detalhes.
