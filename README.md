# 💼 Java JDBC DAO - Seller & Department

Projeto Java desenvolvido com foco em **acesso a dados utilizando JDBC** e aplicação do padrão **DAO (Data Access Object)**.

O sistema realiza operações CRUD em entidades de vendedores (`Seller`) e departamentos (`Department`), conectando-se a um banco de dados relacional.

---

## 🚀 Tecnologias utilizadas

* Java
* JDBC
* MySQL (ou compatível)
* Padrão DAO
* Programação Orientada a Objetos (POO)

---

## 📁 Estrutura do Projeto

```
src/
 ├── application
 │    └── Program.java
 │
 ├── db
 │    ├── Db.java
 │    └── DbException.java
 │
 ├── model
 │    ├── entities
 │    │    ├── Department.java
 │    │    └── Seller.java
 │    │
 │    ├── dao
 │    │    ├── DaoFactory.java
 │    │    ├── DepartmentDao.java
 │    │    └── SellerDao.java
 │    │
 │    └── impl
 │         └── SellerDaoJDBC.java
 │
 ├── db.properties
 └── .gitignore
```

---

## 🧠 Conceitos aplicados

* Separação de responsabilidades (DAO, entidades, aplicação)
* Injeção de dependência via fábrica (`DaoFactory`)
* Reutilização de objetos com `Map` (evitando duplicação de entidades)
* Tratamento de exceções com `DbException`
* Manipulação de banco com `PreparedStatement`

---

## 🗃️ Modelo de Dados

### 🏢 Department

* `id`
* `name`

### 🧑‍💼 Seller

* `id`
* `name`
* `email`
* `birthDate`
* `baseSalary`
* `department`

---

## ⚙️ Funcionalidades

O projeto implementa operações CRUD para `Seller`:

* ✅ Buscar vendedor por ID
* ✅ Buscar vendedores por departamento
* ✅ Listar todos os vendedores
* ✅ Inserir novo vendedor
* ✅ Atualizar vendedor
* ✅ Deletar vendedor

---

## ▶️ Como executar

### 1. Configurar o banco de dados

Crie um banco com as tabelas:

```sql
CREATE TABLE department (
  Id INT PRIMARY KEY AUTO_INCREMENT,
  Name VARCHAR(60)
);

CREATE TABLE seller (
  Id INT PRIMARY KEY AUTO_INCREMENT,
  Name VARCHAR(60),
  Email VARCHAR(100),
  BirthDate DATE,
  BaseSalary DOUBLE,
  DepartmentId INT,
  FOREIGN KEY (DepartmentId) REFERENCES department(Id)
);
```

---

### 2. Configurar conexão

No arquivo `db.properties`, configure:

```
user=seu_usuario
password=sua_senha
dburl=jdbc:mysql://localhost:3306/seu_banco
useSSL=false
```

---

### 3. Executar o projeto

Execute a classe:

```
application.Program
```

---

## 🧪 Testes implementados

O `Program.java` realiza testes de:

```java
findById
findByDepartment
findAll
insert
update
delete
```

---

## 💡 Destaques técnicos

* Uso de `Statement.RETURN_GENERATED_KEYS` para recuperar ID gerado
* Uso de `Map<Integer, Department>` para evitar múltiplas instâncias do mesmo departamento
* Conversão de `java.util.Date` para `java.sql.Date`
* Queries com `INNER JOIN`

---

## 📌 Futuras melhorias

* Implementar `DepartmentDao`
* Adicionar camada de Service
* Utilizar `LocalDate` ao invés de `Date`
* Criar interface gráfica ou API REST
* Implementar testes automatizados (JUnit)

---

## 👨‍💻 Autor

Daniel Cardoso

---

## 📎 Observação

Este projeto tem fins educacionais, focado na prática de JDBC e padrão DAO.
