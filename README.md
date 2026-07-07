# UnderstandingAI: Laboratório Virtual de IA Supervisionada

Aplicação web educacional, construída em Python com Streamlit, que mostra de forma visual e interativa como funcionam os modelos de Aprendizado Supervisionado.

O objetivo não é criar um sistema de previsão, mas sim uma ferramenta de ensino: o usuário acompanha cada etapa do processo, do carregamento dos dados até a previsão final, observando o modelo aprender passo a passo, como em um laboratório virtual.

O público-alvo são estudantes iniciantes, que nunca tiveram contato com Machine Learning. Por isso, toda a interface usa linguagem simples, cartões explicativos, animações suaves e visualizações em cada etapa.

## Principais funcionalidades

- Jornada guiada em 6 etapas, com barra de progresso e navegação por botões
- Leitura dos dados a partir de um arquivo CSV externo
- Detecção automática do papel de cada coluna do CSV (identificação, features e label)
- Funciona com qualquer CSV: qualquer assunto, qualquer quantidade de linhas e qualquer quantidade de features
- Seleção interativa das features que o modelo poderá usar
- Divisão dos dados em treino e teste com slider de porcentagem e sorteio dos grupos
- Treinamento de uma Árvore de Decisão com animação da árvore sendo construída nível por nível
- Gráfico de importância das features após o treinamento
- Avaliação do modelo em dados nunca vistos, com tabela de acertos e erros e cálculo da acurácia
- Playground de previsão: o usuário cria um exemplo novo com sliders e vê o caminho de decisão da árvore explicado pergunta por pergunta
- Envio de um novo CSV pela barra lateral, com adaptação automática de toda a interface

## As 6 etapas do laboratório

1. Introdução. Cartões animados explicam, em linguagem simples, o que é IA, o que é Machine Learning, o que é Aprendizado Supervisionado, o que são exemplos rotulados e o que significa treinar um modelo.

2. Os dados. O laboratório mostra o que detectou no CSV, exibe a tabela completa com cores indicando o papel de cada coluna (azul para features, amarelo para label, cinza para colunas ignoradas) e apresenta um gráfico de dispersão para o estudante enxergar os padrões. O usuário escolhe quais features utilizar.

3. Divisão treino e teste. Um slider controla a porcentagem de dados usada no treinamento. Os registros de cada grupo aparecem como etiquetas animadas, e um botão permite sortear a divisão novamente.

4. Treinamento do modelo. O usuário escolhe o algoritmo (Árvore de Decisão), define a profundidade máxima e assiste à árvore sendo construída nível por nível, como se o modelo estivesse aprendendo em tempo real. Ao final, um gráfico mostra quais features pesaram mais na decisão.

5. Avaliação. O modelo recebe os exemplos do grupo de teste, que ele nunca viu, e suas previsões são comparadas com a realidade. A acurácia é exibida junto com mensagens didáticas que incentivam a experimentação.

6. Faça uma previsão. O estudante inventa um exemplo novo usando sliders (com limites calculados a partir dos valores reais do CSV) e vê a previsão do modelo, o grau de confiança e o caminho completo da decisão, explicado pergunta por pergunta.

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
- Aprendizado supervisionado e exemplos rotulados
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
