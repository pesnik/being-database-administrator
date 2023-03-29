up:
        # docker run -d --name oracle_db -v $(PWD)/data:/opt/oracle/oradata -p 103.199.168.136:1521:1521 -p 103.199.168.136:5500:5500 -p 103.199.168.136:2484:2484 -e ORACLE_PDB=database -e ORACLE_PWD=password oracle/database:21.3.0-xe
        docker run -d --name oracle_db \
        -p 103.199.168.136:1521:1521 -p 103.199.168.136:5500:5500 \
        -e ORACLE_PWD=password \
        oracle/database:21.3.0-xe
        # -v $(PWD)/data:/opt/oracle/oradata \

stop:
        docker container stop oracle_db
        docker container rm oracle_db

logs:
        docker logs oracle_db

exec:
        docker exec -it oracle_db bash

db_script:
        perl -p -i.bak -e 's#/home/oracle/db-sample-schemas#'$(pwd)'#g' *.sql */*.sql */*.dat
        # perl -p -i.bak -e 's#__SUB__CWD__#'$(pwd)'#g' *.sql */*.sql */*.dat

db_make:
        # @mksample password password password password password password password password users temp /home/oracle/logs/ localhost:1521/XE
        @/home/oracle/db-sample-schemas/mksample password password password password password password password password users temp /home/oracle/logs/ localhost:1521/XEPDB1
        # @/home/oracle/db-sample-schemas/mksample password password password password password password password password users temp /home/oracle/logs/ SYS@//103.199.168.136:1521/XE
