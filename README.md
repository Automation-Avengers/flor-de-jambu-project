# README do Projeto Robo Produto

## Descrição

Este projeto automatiza a coleta de informações de produtos e a comunicação por e-mail usando um robô da BotCity. Ele acessa um site específico para pesquisar produtos, obtém a cotação do dólar, lê uma planilha Excel com uma lista de produtos e gera um PDF contendo os produtos e suas informações. Por fim, o robô envia e-mails com o PDF gerado como anexo para uma lista de usuários.

## Funcionalidades

1. **Acesso ao Site**: O robô acessa o site `https://flordejambu.com/shop/` e pesquisa pelo produto "Açaí".
2. **Impressão em PDF**: O robô gera um PDF com a página de resultados da pesquisa.
3. **Cotação do Dólar**: Obtém o valor atualizado do dólar através de uma API.
4. **Leitura de Excel**: Lê uma planilha Excel (`RelacaoProduto.xlsx`) com a lista de produtos.
5. **Inserção no Banco de Dados**: Insere os produtos da planilha no banco de dados, incluindo o valor atualizado em dólar.
6. **Geração de PDF de Produtos**: Cria um PDF com a lista de produtos inseridos.
7. **Merge de PDFs**: Combina os PDFs gerados em um único arquivo chamado `Produtos.pdf`.
8. **Envio de E-mails**: Envia um e-mail com o PDF anexo para cada usuário listado no banco de dados.

## Estrutura do Projeto

- `botproduto/`
  - `pdf/`: Diretório para armazenar arquivos PDF gerados.
  - `planilha/`: Diretório para armazenar a planilha Excel.
  - `e_mail/`: Módulo para envio de e-mails.
  - `planilha/`: Módulo para leitura da planilha.

## Configuração

### Dependências

Certifique-se de ter as seguintes bibliotecas instaladas:

```bash
pip install botcity-web botcity-http-plugin requests pandas openpyxl
```

### Diretórios

Antes de executar o robô, você precisará ajustar os caminhos dos diretórios no código. Verifique e modifique os seguintes caminhos para refletir a estrutura do seu sistema:

- Caminhos para os arquivos PDF:
  - `C:\\LG\\Desafio\\botproduto\\pdf\\SiteProduto.pdf`
  - `C:\\LG\\Desafio\\botproduto\\pdf\\ListaProduto.pdf`
  - `C:\\LG\\Desafio\\botproduto\\pdf\\Produtos.pdf`

- Caminho para a planilha Excel:
  - `C:\\LG\\Desafio\\botproduto\\planilha\\RelacaoProduto.xlsx`

### Execução

Para executar o robô, utilize o seguinte comando:

```bash
python bot.py ou python seu_script.py
```

Certifique-se de que o servidor do banco de dados está em execução e que as APIs estão acessíveis.

## Contribuições

Contribuições são bem-vindas! Se você encontrar um bug ou tiver uma sugestão de melhoria, sinta-se à vontade para abrir um issue ou enviar um pull request.

## Licença

Este projeto está licenciado sob a MIT License. Veja o arquivo `LICENSE` para mais detalhes.
