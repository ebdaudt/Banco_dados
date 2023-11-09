# Comando de banco de dados

## Criar database
* Local para criar as tabelas do sistema
```
create database NOME_DATABASE;
```

### Para executar o comando
```
CTRL + Enter
```

### Selecionar database
```
use NOME_DATABASE:
```
<hr>

## Projeto site Ecommerce
* Tabela de usuarios
* Tabela de produtos
* Tabela carrinho de compras

### Criar tabela de usuarios
```
create table usuarios(
    id int not null auto_increment,
    nome varchar(120) not null,
    email varchar(120) not null,
    senha varchar(120) not null,
    primary key(id)

);
```
* id: identificador de cada registro
* not null: campo obrigatório, não pode ser nulo
* auto_increment: soma +1 no último registro de id
* varchar(120): campo de texto com 120 caracteres

### Criar tabela de produtos
```
create table produtos (
    id int not null auto_increment,
    modelo varchar(120),
    nome varchar(120) not null,
    valor float not null,
    primary key(id)
);

```

### Criar tabela de carrinho
```
create table carrinho(
    id int not null auto_increment,
    id_usuario int not null,
    id_produto int not null,
    primary key(id),
    foreign key(id_usuario) references usuarios(id),
    foreign key(id_produto) references produtos(id)
)
```
* foreign key: chave estrangeira que recebe a referencia de outra tabela
* references: atributo para definir a tabela e o campo estrangeiro

### Inserir usuarios
```
insert into usuarios(nome, email, senha) values('Eduardo','teste@teste.com','secret');
```

### Inserir produto
```
insert into produtos(modelo ,nome, valor) values('nike','camiseta','199.99');
```

### Inserir carrinho
```
insert into carrinho(id_usuario, id_produto) values(1, 1);

```

### Listar todas as colunas de usuarios
```
select * from usuarios;
```

### Listar os nomes dos usuarios
```
select nome from usuarios:
```

### Listar os nomes e email dos usuarios
```
select nome, email from usuarios;
```

### Listar usuarios pelo id
```
select * from usuarios where id = 1;
```

### Verificar produto dno carrinho pelo id do usuario
```
select * from carrinho where id = 1;
```
### Verificar produtos no carrinho pelo id usuarios
```
select nome
from produtos p, carrinho c
where id_usuario = 1 AND p.id = c.id_produto;
```
