# Modelagem do Banco de Dados

## Diagrama 

![Diagrama do Banco de Dados](/imagens/diagrama.png)

## Tabelas e Atributos

### 1. **Usuario**
Armazena informações dos usuários do sistema.
- **id_usuario** (PK, INT, AI): Identificador único.  
- **nome** (VARCHAR(100), NOT NULL): Nome completo.  
- **email** (VARCHAR(100), UNIQUE, NOT NULL): E-mail único.  
- **senha** (VARCHAR(255), NOT NULL): Senha (hash).  
- **tipoUsuario** (VARCHAR(50), NOT NULL): Tipo de usuário (ex: admin, participante, etc.).  

---

### 2. **EdicaoProjeto**
Representa cada edição de um projeto (ano/semestre).
- **id_edicao** (PK, INT, AI): Identificador da edição.  
- **nome** (VARCHAR(100), NOT NULL): Nome da edição.  
- **ano** (INT, NOT NULL): Ano da edição.  
- **semestre** (INT, NOT NULL): Semestre da edição.  
- **descricao** (TEXT): Detalhes adicionais.  

---

### 3. **Equipe**
Equipes participantes vinculadas a uma edição de projeto.
- **id_equipe** (PK, INT, AI): Identificador da equipe.  
- **id_edicao** (FK → EdicaoProjeto.id_edicao): Relaciona a edição.  
- **nomeEquipe** (VARCHAR(100), NOT NULL): Nome da equipe.  

---

### 4. **EquipeUsuario**
Tabela de associação entre **Equipe** e **Usuario** (relacionamento N:N).
- **id_equipe** (FK → Equipe.id_equipe): Equipe vinculada.  
- **id_usuario** (FK → Usuario.id_usuario): Usuário vinculado.  
- **cargo** (VARCHAR(100)): Função do usuário na equipe.  
- **PRIMARY KEY (id_equipe, id_usuario)**.  

---

### 5. **TipoAtividade**
Define os tipos de atividades que podem ser realizadas.
- **id_tipoAtiv** (PK, INT, AI): Identificador do tipo.  
- **nome** (VARCHAR(100), NOT NULL): Nome do tipo.  
- **descricao** (TEXT): Descrição do tipo.  

---

### 6. **Atividade**
Atividades realizadas por uma equipe.
- **id_atividade** (PK, INT, AI): Identificador da atividade.  
- **id_equipe** (FK → Equipe.id_equipe): Equipe responsável.  
- **id_tipoAtiv** (FK → TipoAtividade.id_tipoAtiv): Tipo da atividade.  
- **nome** (VARCHAR(100), NOT NULL): Nome da atividade.  
- **descricao** (TEXT): Detalhes da atividade.  
- **data_inicio** (DATE): Data de início.  
- **data_fim** (DATE): Data de término.  
- **meta** (DECIMAL(10,2)): Valor da meta.  
- **unidade_meta** (VARCHAR(50)): Unidade da meta (ex: R$, kg, horas).  
- **valor_arrecadado** (DECIMAL(10,2)): Valor arrecadado.  
- **valor_fundo_utilizado** (DECIMAL(10,2)): Recursos do fundo utilizados.  

---


## Relacionamentos Principais

- **EdicaoProjeto (1) → (N) Equipe**  
Cada edição pode ter várias equipes.  

- **Equipe (N) ↔ (N) Usuario** através da tabela **EquipeUsuario**.  

- **Equipe (1) → (N) Atividade**  
Uma equipe pode realizar várias atividades.  

- **TipoAtividade (1) → (N) Atividade**  
Cada atividade pertence a um tipo específico.  

---
