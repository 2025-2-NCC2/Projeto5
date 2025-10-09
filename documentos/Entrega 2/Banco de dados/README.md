# 🧩 Banco de Dados – Segunda Entrega

Este arquivo contém a documentação e os scripts das tabelas implementadas. As tabelas contempladas aqui são: **Usuario**, **Equipe** e **EquipeUsuario**. Incluí também uma tabela de suporte **EdicaoProjeto** (mínima) para garantir que a chave estrangeira de `Equipe` funcione ao aplicar o script SQL

---

## Tabelas Implementadas

### 🧑‍💻 1. Tabela: `Usuario`

Armazena as informações dos usuários cadastrados no sistema

| Campo       | Tipo         | Restrições                  | Descrição                                          |
| ----------- | ------------ | --------------------------- | -------------------------------------------------- |
| id_usuario  | INT          | PRIMARY KEY, AUTO_INCREMENT | Identificador único do usuário                     |
| nome        | VARCHAR(100) | NOT NULL                    | Nome completo do usuário                           |
| email       | VARCHAR(100) | UNIQUE, NOT NULL            | E-mail único para login                            |
| senha       | VARCHAR(255) | NOT NULL                    | Senha armazenada em formato hash                   |
| tipoUsuario | VARCHAR(50)  | NOT NULL                    | Tipo de usuário (admin, participante, mentor etc.) |

---

### 🧠 2. Tabela: `Equipe`

Representa as equipes participantes do projeto, cada uma vinculada a uma edição.

| Campo      | Tipo         | Restrições                             | Descrição                                      |
| ---------- | ------------ | -------------------------------------- | ---------------------------------------------- |
| id_equipe  | INT          | PRIMARY KEY, AUTO_INCREMENT            | Identificador da equipe                        |
| id_edicao  | INT          | FOREIGN KEY → EdicaoProjeto(id_edicao) | Identifica a edição do projeto à qual pertence |
| nomeEquipe | VARCHAR(100) | NOT NULL                               | Nome da equipe participante                    |

---

### 👥 3. Tabela: `EquipeUsuario`

Faz o relacionamento N:N entre `Usuario` e `Equipe`.

| Campo      | Tipo         | Restrições                  | Descrição                                               |
| ---------- | ------------ | --------------------------- | ------------------------------------------------------- |
| id_equipe  | INT          | FK → Equipe.id_equipe, PK   | Identifica a equipe                                     |
| id_usuario | INT          | FK → Usuario.id_usuario, PK | Identifica o usuário                                    |
| cargo      | VARCHAR(100) | NULL                        | Função do usuário na equipe (ex: líder, membro, mentor) |

---

## 💾 Script SQL (MySQL)

```sql
-- BD/schema.sql (MySQL)

CREATE TABLE IF NOT EXISTS EdicaoProjeto (
  id_edicao INT AUTO_INCREMENT PRIMARY KEY,
  nome VARCHAR(100) NOT NULL,
  ano INT NOT NULL,
  semestre INT NOT NULL,
  descricao TEXT
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS Usuario (
  id_usuario INT AUTO_INCREMENT PRIMARY KEY,
  nome VARCHAR(100) NOT NULL,
  email VARCHAR(100) NOT NULL UNIQUE,
  senha VARCHAR(255) NOT NULL,
  tipoUsuario VARCHAR(50) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS Equipe (
  id_equipe INT AUTO_INCREMENT PRIMARY KEY,
  id_edicao INT,
  nomeEquipe VARCHAR(100) NOT NULL,
  CONSTRAINT fk_equipe_edicao FOREIGN KEY (id_edicao) REFERENCES EdicaoProjeto(id_edicao) ON DELETE SET NULL ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

CREATE TABLE IF NOT EXISTS EquipeUsuario (
  id_equipe INT NOT NULL,
  id_usuario INT NOT NULL,
  cargo VARCHAR(100),
  PRIMARY KEY (id_equipe, id_usuario),
  CONSTRAINT fk_equipeusuario_equipe FOREIGN KEY (id_equipe) REFERENCES Equipe(id_equipe) ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT fk_equipeusuario_usuario FOREIGN KEY (id_usuario) REFERENCES Usuario(id_usuario) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
```
