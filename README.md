# Automação Local para Relatórios de Ponto

### Visão geral

Este projeto é uma automação local em Python criada para apoiar a extração e organização de relatórios mensais de ponto a partir de um sistema web.

A automação utiliza Selenium para controlar o navegador, ler uma planilha de controle, buscar colaboradores por identificador único, navegar mês a mês no sistema, solicitar a geração de relatórios e tratar os arquivos baixados.

O foco do projeto é reduzir trabalho manual repetitivo, mantendo uma estrutura simples, modular e fácil de manter.

---

### Contexto

Alguns sistemas web exigem que relatórios históricos sejam gerados individualmente, mês a mês e colaborador por colaborador.

Esse processo pode envolver muitos cliques, múltiplos downloads e organização manual de arquivos. Este projeto automatiza esse fluxo de forma local, usando uma planilha como entrada e salvando os documentos finais em uma estrutura de pastas já existente.

Nenhum dado sensível, credencial, URL interna, caminho corporativo real ou arquivo operacional deve ser versionado neste repositório.

---

### Funcionalidades principais

- Leitura de planilha Excel de controle.
- Validação de colunas obrigatórias.
- Automação de navegador com Selenium.
- Login e navegação em sistema web.
- Busca de colaborador por identificador único.
- Cálculo de competências entre data inicial e data final.
- Navegação mês a mês para geração de relatórios.
- Download automático de arquivos compactados.

---

### Fluxo resumido

```text
Ler planilha
↓
Validar dados
↓
Abrir navegador
↓
Acessar sistema web
↓
Buscar colaborador
↓
Calcular período
↓
Para cada competência:
    gerar relatório
    aguardar download
```

---

### Estrutura do projeto

```text
project/
├── main.py
├── requirements.txt
├── entrada/
│   └── controle.xlsx
├── processamento/
├── logs/
└── src/
    ├── __init__.py
    ├── config.py
    ├── browser.py
    ├── controle.py
    ├── pontotel.py
    └── arquivos.py
```

---

### Stack utilizada

- Python 3.x
- Selenium
- WebDriver Manager
- Pandas
- OpenPyXL

Bibliotecas nativas utilizadas ou previstas:

- `pathlib`
- `time`
- `datetime`
- `zipfile`
- `shutil`
- `logging`
- `traceback`
- `re`
- `unicodedata`

---

### Planilha de entrada

A automação usa uma planilha Excel como fonte de controle.

Colunas esperadas:

```text
MATRICULA
NOME DO AUTOR
ADMISSAO
DEMISSAO
CENTRO DE CUSTO
PRIORIDADE
```

A coluna `PRIORIDADE` pode ser opcional, dependendo da regra de execução.

---


### Instalação

Crie um ambiente virtual:

```bash
python -m venv .venv
```

Ative o ambiente virtual no Windows:

```bash
.venv\Scripts\activate
```

Instale as dependências:

```bash
pip install -r requirements.txt
```

---

### Configuração

As configurações principais devem ficar centralizadas em:

```text
src/config.py
```

Exemplos de configurações esperadas:

```python
URL_SISTEMA = ""
PASTA_DOWNLOADS = ""
PASTA_PROCESSAMENTO = ""
CAMINHO_PLANILHA_CONTROLE = ""
TEMPO_ESPERA_PADRAO = 20
TEMPO_ESPERA_DOWNLOAD = 120
```
---

### Execução

Após configurar o ambiente, a planilha e os caminhos necessários, execute:

```bash
python main.py
```

Durante o desenvolvimento, o navegador pode ser executado de forma visível para facilitar depuração.

---


### Sugestão de `.gitignore`

```gitignore
.venv/
__pycache__/
*.pyc

.env

entrada/*.xlsx
processamento/
logs/
downloads/
output/

*.zip
*.pdf
*.xls
*.xlsx
```

Caso seja necessário manter uma planilha de exemplo, use dados fictícios e um nome explícito, como:

```text
controle_exemplo.xlsx
```

---

### Estado do projeto

A automação está sendo construída de forma incremental.

Etapas principais já previstas:

- Leitura da planilha.
- Navegação no sistema web.
- Busca de colaborador.
- Cálculo de competências.
- Geração de relatórios mensais.

---
