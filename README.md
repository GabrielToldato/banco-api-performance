# Banco API – Testes de Performance com K6

## 1. Introdução

Este projeto tem como objetivo realizar testes de performance na **Banco API**, utilizando JavaScript e K6 como ferramenta de execução dos testes de carga.

Os testes permitem avaliar o comportamento da API diante de diferentes condições de utilização, simulando requisições simultâneas e analisando métricas como tempo de resposta, quantidade de requisições, taxa de erros e desempenho geral dos endpoints.

O projeto utiliza uma estrutura organizada para facilitar a manutenção, reutilização de código e evolução dos cenários de testes.

**Repositório da API testada:**  
https://github.com/GabrielToldato/banco-api

## 2. Tecnologias utilizadas

As principais tecnologias e ferramentas utilizadas neste projeto são:

| Tecnologia | Finalidade |
|---|---|
| JavaScript | Linguagem utilizada para desenvolver os scripts de testes. |
| K6 | Ferramenta utilizada para execução dos testes de performance. |
| Git | Controle de versão do projeto. |
| GitHub | Hospedagem e gerenciamento do código-fonte. |
| HTML | Formato utilizado para exportação do relatório de performance. |

## 3. Estrutura do repositório

O projeto está organizado da seguinte maneira:

```text
banco-api-performance/
│
├── config/
│
├── fixtures/
│
├── helpers/
│
├── tests/
│
├── utils/
│
├── config/
│
└── README.md
```

### Objetivo de cada grupo de arquivos

**config/**

Responsável por armazenar arquivos relacionados às configurações utilizadas durante a execução dos testes, permitindo centralizar parâmetros e facilitar eventuais alterações no ambiente de execução.

**fixtures/**

Armazena dados utilizados pelos cenários de testes, permitindo reutilizar informações e organizar os dados necessários para realizar as requisições.

**helpers/**

Contém funções auxiliares que podem ser reutilizadas em diferentes scripts de testes, evitando duplicidade de código e facilitando a manutenção.

**tests/**

Diretório responsável por armazenar os cenários de testes de performance desenvolvidos com K6 e JavaScript.

É neste diretório que ficam os scripts responsáveis por executar as requisições e avaliar o comportamento da API.

**utils/**

Contém funções utilitárias e recursos de apoio utilizados pelos testes, contribuindo para a organização e reutilização de funcionalidades.

**config/**

Arquivos de configuração de variaveis de ambiente.


## 4. Instalação do projeto

### 4.1. Pré-requisitos

Antes de iniciar, é necessário possuir:

- Git instalado.
- K6 instalado e configurado no PATH do sistema.
- Acesso à Banco API.
- Um terminal para executar os comandos.

A instalação do K6 pode ser realizada seguindo a documentação oficial:

https://grafana.com/docs/k6/latest/set-up/install-k6/

### 4.2. Clonando o repositório

Execute o comando abaixo para clonar o projeto:

```bash
git clone https://github.com/GabrielToldato/banco-api-performance.git
```

Acesse o diretório:

```bash
cd banco-api-performance
```

### 4.3. Configuração da variável de ambiente

O projeto utiliza a variável de ambiente `BASE_URL` para definir o endereço da API que será submetida aos testes.

Essa configuração permite executar os mesmos scripts em diferentes ambientes sem precisar alterar diretamente o código-fonte.

Exemplo:

```text
BASE_URL=http://localhost:3000
```

**Windows – PowerShell:**

```powershell
$env:BASE_URL="http://localhost:3000"
```

**Windows – CMD:**

```cmd
set BASE_URL=http://localhost:3000
```

**Linux / macOS:**

```bash
export BASE_URL=http://localhost:3000
```

A URL configurada deve corresponder ao endereço em que a Banco API está disponível.

## 5. Execução dos testes

### 5.1. Execução convencional

Após instalar o K6, iniciar a API e configurar a variável `BASE_URL`, execute o script desejado:

```bash
k6 run tests/nome-do-arquivo.js
```

Substitua `nome-do-arquivo.js` pelo nome do script existente no diretório `tests/`.

O K6 apresentará no terminal as métricas coletadas durante a execução, incluindo:

- Total de requisições realizadas.
- Tempo médio de resposta.
- Tempo mínimo e máximo de resposta.
- Percentis de tempo de resposta.
- Taxa de requisições por segundo.
- Quantidade de requisições com falha.
- Resultado dos checks definidos nos cenários.

### 5.2. Acompanhamento do relatório em tempo real

O K6 disponibiliza um dashboard web que permite acompanhar visualmente as métricas durante a execução dos testes.

Para habilitar o dashboard e exportar o relatório em HTML, utilize as variáveis de ambiente disponibilizadas pelo próprio K6:

**Windows – PowerShell:**

```powershell
$env:BASE_URL="http://localhost:3000"
$env:K6_WEB_DASHBOARD="true"
$env:K6_WEB_DASHBOARD_EXPORT="html-report.html"

k6 run .\tests\nome-do-arquivo.js
```

**Windows – CMD:**

```cmd
set BASE_URL=http://localhost:3000
set K6_WEB_DASHBOARD=true
set K6_WEB_DASHBOARD_EXPORT=html-report.html

k6 run tests/nome-do-arquivo.js
```

**Linux / macOS:**

```bash
BASE_URL=http://localhost:3000 K6_WEB_DASHBOARD=true K6_WEB_DASHBOARD_EXPORT=html-report.html k6 run tests/nome-do-arquivo.js
```

Durante a execução, acesse o dashboard pelo navegador:

```text
http://localhost:5665
```

O dashboard permite acompanhar em tempo real informações como:

- Requisições por segundo.
- Tempo de resposta.
- Número de usuários virtuais (VUs).
- Quantidade de requisições realizadas.
- Taxa de erros.
- Evolução das métricas durante o teste.

### 5.3. Exportação do relatório em HTML

A variável:

```bash
K6_WEB_DASHBOARD_EXPORT=html-report.html
```

define o nome do arquivo HTML que será gerado com os dados do dashboard.

Ao finalizar a execução, o relatório ficará disponível na raiz do projeto:

```text
banco-api-performance/
│
├── html-report.html
```

O arquivo pode ser aberto diretamente no navegador para consultar os resultados da execução.

**Observação:** o relatório HTML é um artefato gerado pelo teste e não precisa ser versionado no Git. Adicione `html-report.html` ao `.gitignore` caso ainda não esteja contemplado.

---

## Considerações finais

Este projeto faz parte da minha jornada de desenvolvimento na área de Quality Assurance (QA), com foco em automação de testes e testes de performance.

A iniciativa busca aplicar conhecimentos de JavaScript e K6 na validação de APIs, explorando conceitos de desempenho, comportamento sob carga, análise de métricas e identificação de possíveis gargalos.

O projeto continuará evoluindo com a inclusão de novos cenários e melhorias na cobertura dos testes.

**Desenvolvido por Gabriel Teles Toldato.**

GitHub: https://github.com/GabrielToldato
