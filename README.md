# Projeto Flor de Jambu

## Descrição Geral

Este projeto consiste em um robô automatizado que coleta informações sobre produtos e uma API em Flask que gerencia usuários, produtos e eleitores. O robô acessa um site para pesquisar produtos, lê dados de uma planilha Excel, gera PDFs e envia e-mails, enquanto a API fornece endpoints para manipulação de dados.

## Estrutura do Projeto

```
/flor-de-jambu-project
│
├── /api_database
│   ├── /__pycache__           # Arquivos compilados do Python
│   ├── /env_api_database      # Ambiente virtual da API
│   ├── /http                  # Módulos de integração HTTP
│   ├── /repository             # Módulos para gerenciar dados (usuários, produtos, eleitores)
│   ├── /service               # Serviços da API
│   └── servico_api.py        # Script principal da API em Flask
│
├── /botproduto                # Diretório do robô
│   ├── /e_mail                # Módulo para envio de e-mails
│   ├── /pdf                   # Módulo para manipulação de PDFs
│   ├── /planilha              # Módulo para leitura de planilhas
│   ├── /resources             # Recursos auxiliares (se necessário)
│   ├── /ListaProduto.pdf      # PDF gerado com a lista de produtos
│   ├── /Produtos.pdf          # PDF combinado com os produtos
│   ├── /SiteProduto.pdf       # PDF com a página do site
│   ├── bot.py                 # Script do robô
│   ├── botproduto.botproj     # Projeto do BotCity
│   └── build.*                # Scripts para build (Windows/Linux)
│
└── requirements.txt           # Arquivo com dependências do projeto
```

## Funcionalidades do Robô

1. **Acesso ao Site**: Pesquisa por produtos em `https://flordejambu.com/shop/`.
2. **Impressão em PDF**: Gera um PDF com a página de resultados da pesquisa.
3. **Cotação do Dólar**: Obtém o valor atualizado do dólar através de uma API.
4. **Leitura de Excel**: Lê uma planilha Excel (`RelacaoProduto.xlsx`) com a lista de produtos.
5. **Inserção no Banco de Dados**: Insere os produtos da planilha no banco de dados.
6. **Geração de PDF de Produtos**: Cria um PDF com a lista de produtos inseridos.
7. **Merge de PDFs**: Combina os PDFs gerados em um único arquivo.
8. **Envio de E-Mails**: Envia e-mails com o PDF anexo para usuários cadastrados.

## Funcionalidades da API

### Usuários
- **Criar Usuário**: Adiciona um novo usuário.
- **Atualizar Usuário**: Atualiza dados de um usuário existente.
- **Deletar Usuário**: Remove um usuário pelo ID.
- **Obter Usuário por ID**: Recupera dados de um usuário específico.
- **Listar Usuários**: Retorna todos os usuários cadastrados.

### Produtos
- **Criar Produto**: Adiciona um novo produto.
- **Atualizar Produto**: Atualiza dados de um produto existente.
- **Alterar Preço do Dólar**: Atualiza o preço do dólar de um produto.
- **Deletar Produto**: Remove um produto pelo ID.
- **Obter Produto por ID**: Recupera dados de um produto específico.
- **Listar Produtos**: Retorna todos os produtos cadastrados.

### Eleitores
- **Criar Eleitor**: Adiciona um novo eleitor.

## Instalação

### Instalação da API

1. Navegue até o diretório da API:

   ```bash
   cd api_database
   ```

2. **Crie um ambiente virtual** (se ainda não existir):

   ```bash
   python -m venv env_api_database
   ```

3. **Ative o ambiente virtual**:
   - **Windows**:
     ```bash
     .\env_api_database\Scripts\activate
     ```
   - **Linux/Mac**:
     ```bash
     source env_api_database/bin/activate
     ```

4. **Instale as dependências**:

   ```bash
   pip install flask
   ```
   ```bash
   pip install mysql-connector-python
   ```
6. **Se precisar refazer o ambiente virtual**, você pode excluir o diretório `env_api_database` e repetir os passos acima:

   ```bash
   rm -rf env_api_database  # Linux/Mac
   rmdir /s /q env_api_database  # Windows
   ```

### Instalação do Robô

1. Navegue até o diretório do robô:

   ```bash
   cd botproduto
   ```

2. **Crie um ambiente Conda** (se ainda não existir):

   ```bash
   conda create --name botproduto python=3.9
   ```

3. **Ative o ambiente Conda**:

   ```bash
   conda activate botproduto
   ```

4. **Instale as dependências**:

   ```bash
   pip install botcity-email-plugin
   ```
   ```bash
   pip install botcity-http-plugin
   ```
   ```bash
   pip install openpyxl
   ```
   ```bash
   pip install pandas
   ```
   ```bash
   pip install requests
   ```
   ```bash
   pip install webdriver_manager
   ```
   ```bash
   pip install PyPDF2
   ```
   ```bash
   pip install reportlab
   ```
   ```bash
   pip install ipython
   ```

5. **Se precisar refazer o ambiente Conda**, você pode excluir o ambiente e repetir os passos acima:

   ```bash
   conda remove --name botproduto --all
   ```

### Configuração

#### Diretórios

Antes de executar o robô, ajuste os caminhos dos diretórios no código:

- PDFs:
  - `C:\\LG\\Desafio\\botproduto\\pdf\\SiteProduto.pdf`
  - `C:\\LG\\Desafio\\botproduto\\pdf\\ListaProduto.pdf`
  - `C:\\LG\\Desafio\\botproduto\\pdf\\Produtos.pdf`

- Planilha Excel:
  - `C:\\LG\\Desafio\\botproduto\\planilha\\RelacaoProduto.xlsx`

#### Banco de Dados

Configure seu banco de dados MySQL com as tabelas apropriadas para usuários, produtos e eleitores. As funções nos módulos de repositório assumem que essas tabelas já existem.

### Executando o Robô

Para executar o robô, use:

```bash
python botproduto/bot.py
```

### Executando a API

Para executar a API, use:

```bash
python api_database/servico_api.py
```

A API estará disponível em `http://127.0.0.1:5000`.

## Uso da API

A API pode ser acessada através de requisições HTTP. Exemplos de endpoints:

### Usuários

- **Criar Usuário**
  - Método: `POST`
  - Endpoint: `/usuario`
  - Corpo: `{"nome": "Nome do Usuário", "email": "email@example.com", ...}`

- **Listar Usuários**
  - Método: `GET`
  - Endpoint: `/usuario`

### Produtos

- **Criar Produto**
  - Método: `POST`
  - Endpoint: `/produto`
  - Corpo: `{"descricao": "Descrição do Produto", "preco": 100.0, ...}`

- **Listar Produtos**
  - Método: `GET`
  - Endpoint: `/produto`

### Eleitores

- **Criar Eleitor**
  - Método: `POST`
  - Endpoint: `/eleitor`
  - Corpo: `{"nome": "Nome do Eleitor", "titulo": "Número do Título", ...}`

## Contribuições

Contribuições são bem-vindas! Se você encontrar um bug ou tiver sugestões de melhorias, fique à vontade para abrir um issue ou enviar um pull request.

## Licença

Este projeto está licenciado sob a MIT License. Veja o arquivo `LICENSE` para mais detalhes.

## Observações

- Para o funcionamento correto da API, certifique-se de que o servidor MySQL esteja em execução e que as credenciais estejam corretamente configuradas nos módulos de repositório.
- Os módulos de repositório devem ser ajustados para refletir a estrutura do seu projeto, se necessário.
