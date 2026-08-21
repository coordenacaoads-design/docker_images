# MySQL Server - 2o Periodo
FROM mysql:8.0

LABEL description="MySQL Server para uso didatico"

# Scripts .sql colocados aqui sao executados automaticamente na primeira
# inicializacao do banco (crie suas tabelas/seed de exemplo se quiser).
COPY init/ /docker-entrypoint-initdb.d/

EXPOSE 3306

# Nao definimos senha aqui por seguranca. Ao rodar o container, informe:
#   docker run -e MYSQL_ROOT_PASSWORD=suasenha -e MYSQL_DATABASE=aula_db ...
