# DesafioDados

## 1. Objetivo

O propósito é avaliar a proficiência no desenvolvimento de rotinas de manipulação de dados, configuração de ambientes isolados, conteinerização de infraestrutura e versionamento de código.

Uma pipeline simples de ETL (Extract, Transform, Load) utilizando Python, consumindo de um csv de origem para um banco de dados de destino hospedado localmente.

## 2. Requisitos/Escopo da Atividade

1. **Configuração de Ambiente Isolado:**
	- Inicializar e configurar um ambiente virtual Python (venv ou equivalente, como poetry ou pipenv, a recomendação uv) para isolar as dependências do projeto.
    
2. **Extração de Dados/Normalização:**
	- Utilizar bibliotecas de leitura de dados para extrair e tratar tipos de dados.
	- Fazer a inferência de tipo nas colunas, de objetivo para o tipo correto.
	- Elaborar e executar SQL para inserir o conjunto de dados.
    
3. **Infraestrutura Local (Target):**
	- Provisionar um banco de dados local utilizando Docker (docker-compose.yml).
    

4. **Carga de Dados (Load):**
	- Desenvolver o script Python responsável por ler os dados da origem e inseri-los no banco de dados local (Docker).
	- Garantir a integridade e atomicidade dos dados durante a transferência.
    
5. **Versionamento e Entrega:**
	- Inicializar um repositório local utilizando Git.
	- Commits semânticos para o código-fonte desenvolvido, arquivos de configuração (requirements.txt, docker-compose.yml).
	- Efetuar o envio (push) do código para o repositório remoto **em uma branch diferente da main**.

```mermaid
flowchart TB

subgraph subGraph0["Ambiente Virtual"]

A["Scripts de extração/transformação<br>"]

end

subgraph subGraph1["Origem dos Dados"]

DB_SRC["csv<br>"]

end

subgraph subGraph2["Database"]

DB_TGT[("Container Docker<br>(**Postgres**)")]

end

subgraph subGraph3["Controle de Versão"]

GIT["Repositório Git<br>Remoto"]

end

DB_SRC -- 1 Leitura dos dados (Extração) --> A

A -- 2 Inserção de Dados (Carga) --> DB_TGT

A -. 3 Commit & Push do Código .-> GIT

DB_TGT -. "docker-compose File" .-> GIT

  

DB_SRC@{ shape: card}

GIT@{ shape: braces}

DB_SRC:::Aqua

style DB_SRC stroke:#000000

style subGraph1 fill:#FFCDD2

style subGraph0 fill:#C8E6C9

style subGraph2 fill:#BBDEFB

style subGraph3 fill:#E1BEE7
```
