![Static Badge](https://img.shields.io/badge/Python-3.11.4-blue)
![Static Badge](https://img.shields.io/badge/PostgreSQL-16-gray)
![Static Badge](https://img.shields.io/badge/FastAPI%200.111.0-blue)
![Static Badge](https://img.shields.io/badge/SQLAlchemy%202.0.30-red)
![Static Badge](https://img.shields.io/badge/Pydantic%202.7.3-pink)
![Static Badge](https://img.shields.io/badge/Uvicorn%200.30.1-blue)

## Swagger UI do FastAPI
![Swagger](/fastapi.png "Swagger do FastAPI")


# FastAPI
### O que é FastAPI?
FastAPI é um framework Python moderno, projetado para simplicidade, velocidade e eficiência. A combinação de diversas funcionalidades modernas do Python como anotações de tipo e suporte a concorrência, facilitando o desenvolvimento de APIs.

### Async
Código assíncrono apenas significa que a linguagem tem um jeito de dizer para o computador / programa que em certo ponto, ele terá que esperar por algo para finalizar em outro lugar

# Projeto
## WorkoutAPI

Esta é uma API de competição de crossfit chamada WorkoutAPI (isso mesmo rs, eu acabei unificando duas coisas que gosto: codar e treinar). É uma API pequena, devido a ser um projeto mais hands-on e simplificado nós desenvolveremos uma API de poucas tabelas, mas com o necessário para você aprender como utilizar o FastAPI.

## Modelagem de entidade e relacionamento - MER
![MER](/mer.jpg "Modelagem de entidade e relacionamento")

## Stack da API

A API foi desenvolvida utilizando o `fastapi` (async), junto das seguintes libs: `alembic`, `SQLAlchemy`, `pydantic`. Para salvar os dados está sendo utilizando o `postgres`.

## Execução da API

Para executar o projeto, utilizei o anaconda [anaconda](https://www.anaconda.com/download), com a versão 3.12.3 do `python` para o ambiente virtual.

Caso opte por usar pyenv, após instalar, execute:

```console
conda create -n workoutapi
conda activate workoutapi
pip install -r requirements.txt
```
Para subir o banco de dados, utilizei o [PostgreSQL](https://www.postgresql.org/download/).

Para executar o alembic
```console
(workoutapi) C:\Users\fernandes\Desktop\workout_api>alembic revision --autogenerate -m 'init_db'
INFO  [alembic.runtime.migration] Context impl PostgresqlImpl.
INFO  [alembic.runtime.migration] Will assume transactional DDL.
INFO  [alembic.autogenerate.compare] Detected added table 'categorias'
INFO  [alembic.autogenerate.compare] Detected added table 'centro_treinamentos'
INFO  [alembic.autogenerate.compare] Detected added table 'atletas'
Generating C:\Users\fernandes\Desktop\workout_api\alembic\versions\d1835754990c_init_db.py ...  done
```


Para executar o alembic migrations
```console
(workoutapi) C:\Users\fernandes\Desktop\workout_api>alembic upgrade head                        
INFO  [alembic.runtime.migration] Context impl PostgresqlImpl.
INFO  [alembic.runtime.migration] Will assume transactional DDL.
INFO  [alembic.runtime.migration] Running upgrade  -> d1835754990c, 'init_db'
`````

## API

Para subir a API, execute:
Para executar o fastapi usando uvicorn
```console
(workoutapi) C:\Users\fernandes\Desktop\workout_api>uvicorn src.main:app --reload
INFO:     Will watch for changes in these directories: ['C:\\Users\\fernandes\\Desktop\\workout_api']
INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
INFO:     Started reloader process [21428] using WatchFiles
INFO:     Started server process [15056]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
```
e acesse: http://127.0.0.1:8000/docs

# Desafio Final
    - adicionar query parameters nos endpoints
        - atleta
            - nome
            - cpf
    - customizar response de retorno de endpoints
        - get all
            - atleta
                - nome
                - centro_treinamento
                - categoria
    - Manipular exceção de integridade dos dados em cada módulo/tabela
        - sqlalchemy.exc.IntegrityError e devolver a seguinte mensagem: “Já existe um atleta cadastrado com o cpf: x”
        - status_code: 303
    - Adicionar paginação utilizando a lib: fastapi-pagination
        - limit e offset
# Referências

FastAPI: https://fastapi.tiangolo.com/

PostgreSQL: https://www.postgresql.org/download/

Pydantic: https://docs.pydantic.dev/latest/

SQLAlchemy: https://docs.sqlalchemy.org/en/20/

Alembic: https://alembic.sqlalchemy.org/en/latest/

Fastapi-pagination: https://uriyyo-fastapi-pagination.netlify.app/
