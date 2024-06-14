# Desafio Dio - Refinando um Projeto Conceitual de Banco de Dados – E-COMMERCE 

Para este projeto, aplico os conceitos de modelagem de banco de dados vistos anteriormente na seção Bancos de Dados SQL e NoSql do bootcamp Geração Tech Unimed-BH - Ciência de Dados. Neste desafio, modelei um banco para o contexto de Ordens de Serviço, de Universidade e de E-commerce. Para o caso do E-commerce, tive como desafio terminar a modelagem utilizando os requisitos dados pela instrutora.

### Contexto: 
venda de produtos.

## Objetivo:

Refinar o modelo acrescentando os seguintes pontos:

. **Cliente PJ e PF - Uma conta pode ser PJ ou PF, mas não pode ter as duas informações:** 

Como os requisitos não informam se deve haver alguma característica particular ao cliente se ele for PJ ou PF, adicionei um atributo chamado tipo_conta para a entidade Cliente para informar se o cliente é PF ou PJ. Caso houvesse alguma particularização, eu criaria as subclasses Pessoa Física e Pessoa Juridica para a classe Cliente, cada uma dessas contendo atributos relacionados às suas particularidades.



. **Pagamento – Pode ter cadastrado mais de uma forma de pagamento:** Criei uma entidade nova chamada Pagamento, que contém atributos relacionados aos dados de cartões de crédito que podem ser persistidos.



. **Entrega – Possui status e código de rastreio:** Criei uma nova entidade chamada entrega que contém os atributos de status e rastreio, além de outros relacionados às datas de saída e entrega, e também de transportadora.

[Link do diagrama a ser refinado](https://github.com/casjunior93/DIO---Refinando-um-Projeto-Conceitual-de-Banco-de-Dados-E-COMMERCE/raw/main/E-commerce/diagrama-e-commerce-aula.png)

[Link do diagrama refinado](https://github.com/casjunior93/DIO---Refinando-um-Projeto-Conceitual-de-Banco-de-Dados-E-COMMERCE/raw/main/E-commerce/diagrama-e-commerce-aula-refinado.png)



### **Projeto Abrangente e Completo para Refinar um Projeto Conceitual de Banco de Dados para E-commerce**

#### **Introdução:**

Um banco de dados bem projetado é a espinha dorsal de qualquer sistema de e-commerce de sucesso, garantindo a integridade, consistência e eficiência dos dados. Este projeto abrangente visa refinar um projeto conceitual de banco de dados para um sistema de e-commerce, otimizando sua estrutura e relacionamentos para atender aos requisitos de negócios.



### **Metodologia:**



#### **1. Análise de Requisitos:**

- Revisar os requisitos de negócios do sistema de e-commerce, incluindo funcionalidades, casos de uso e regras de negócios.

  

- Identificar as entidades (por exemplo, produtos, clientes, pedidos) e seus atributos.



#### **2. Modelagem Conceitual:**

- Criar um Diagrama Entidade-Relacionamento (DER) para representar as entidades e seus relacionamentos.

  

- Definir as cardinalidades dos relacionamentos (por exemplo, um-para-muitos, muitos-para-muitos).

  

- Atribuir chaves primárias e chaves estrangeiras para garantir a integridade dos dados.



#### **Exemplo de DER:**

```plaintext
+--------------+      +--------------+      +--------------+
| Produto      |      | Pedido        |      | Cliente      |
+--------------+      +--------------+      +--------------+
| id_produto    |      | id_pedido      |      | id_cliente    |
| nome_produto  |      | data_pedido    |      | nome_cliente  |
| descricao     |      | id_cliente     |      | email         |
| preco         |      | id_produto    |      | endereco       |
| quantidade    |      | quantidade     |      | telefone      |
+--------------+      +--------------+      +--------------+
```



#### **3. Normalização:**

- Normalizar o esquema do banco de dados para eliminar redundâncias e inconsistências.

  

- Aplicar as Formas Normais de Boyce-Codd (BCNF) para garantir que os dados estejam organizados de forma eficiente e sem perdas.



#### **4. Otimização do Esquema:**

- Otimizar o esquema do banco de dados para melhorar o desempenho das consultas.

- Criar índices para acelerar o acesso aos dados.

  

- Considerar o particionamento de tabelas para lidar com grandes volumes de dados.



##### **Exemplo de índice:**

sql

```sql
CREATE INDEX idx_produto_nome ON Produto(nome_produto);
```



#### **5. Escolha do Sistema de Gerenciamento de Banco de Dados (SGBD):**

- Selecionar um SGBD adequado com base nos requisitos de desempenho, escalabilidade e recursos do sistema de e-commerce.

  

- Considerar fatores como suporte a transações, replicação e segurança.



#### **6. Implementação Física:**

- Traduzir o projeto conceitual em um esquema físico específico do SGBD escolhido.

  

- Criar tabelas, índices e restrições de acordo com o projeto otimizado.



**Exemplo de criação de tabela no MySQL:**

sql

```sql
CREATE TABLE Produto (
  id_produto INT NOT NULL AUTO_INCREMENT,
  nome_produto VARCHAR(255) NOT NULL,
  descricao TEXT,
  preco DECIMAL(10,2) NOT NULL,
  quantidade INT NOT NULL,
  PRIMARY KEY (id_produto)
);
```





#### **7. Teste e Refinamento:**

- Testar o banco de dados implementado para verificar sua integridade, consistência e desempenho.

  

- Refinar o projeto com base nos resultados dos testes e nos comentários dos usuários.







**Códigos Adicionais para Refinamento do Projeto Conceitual de Banco de Dados para E-commerce:**



**Exemplo de restrição de chave estrangeira no MySQL:**

sql

```sql
ALTER TABLE Pedido ADD FOREIGN KEY (id_cliente) REFERENCES Cliente(id_cliente);
```



**Exemplo de particionamento de tabela no PostgreSQL:**

sql

```sql
CREATE TABLE Produto PARTITION BY RANGE (id_produto) (
  PARTITION p0 VALUES LESS THAN (10000),
  PARTITION p1 VALUES LESS THAN (20000),
  PARTITION p2 VALUES LESS THAN (30000)
);
```



**Exemplo de consulta otimizada usando índice:**

sql

```sql
SELECT * FROM Produto WHERE nome_produto LIKE '%computador%' USE INDEX (idx_produto_nome);
```



**Exemplo de teste de integridade usando o comando CHECK no MySQL:**

sql

```sql
ALTER TABLE Produto ADD CONSTRAINT chk_quantidade CHECK (quantidade >= 0);
```



**Exemplo de refinamento do projeto com base em comentários de usuários:**

- **Comentário do usuário:** "A tabela de pedidos deve incluir um campo para rastrear o status do pedido."

  

- **Refinamento do projeto:** Adicionar um campo `status` à tabela `Pedido` com valores possíveis como "pendente", "processando" e "concluído".

  

Esses códigos e exemplos adicionais demonstram ainda mais o processo de refinamento do projeto conceitual de banco de dados para um sistema de e-commerce, garantindo sua eficiência, confiabilidade e alinhamento com os requisitos de negócios.



## **Conclusão:**

Este projeto de refinamento abrangente visa criar um projeto conceitual de banco de dados robusto e otimizado para um sistema de e-commerce. O projeto aprimorado garantirá a eficiência, confiabilidade e escalabilidade do banco de dados, atendendo aos requisitos de negócios e apoiando o crescimento e o sucesso do sistema de e-commerce.

