# AULA 01 - 21/03/25

Conectando no MySql por terminal:
```bash
mysql -h 127.0.0.1 -P 3306 -u root -p
mysql -h 127.0.0.1 -P 3306 -u kaique -p
```

Visualizar todos os bancos já criados

``` sql 
SHOW DATABASES;
```

# Usuários

Comandos para gerenciamento de usuários:
```sql
--- Criar um novo usuário
CREATE USER 'username'@'host' IDENTIFIED BY 'senha';
CREATE USER 'kaique'@'localhost' IDENTIFIED BY '123456';

--- Conceder todos os privilégios a um BD
GRANT ALL PRIVILEGES ON database.* TO 'username'@'host';
GRANT ALL PRIVILEGES ON mysql.* TO 'kaique'@'localhost';

--- Conceder apenas alguns privilegios
GRANT SELECT, INSERT, UPDATE ON database.table TO 'username'@'host';

--- Remover privilégios
REVOKE ALL PRIVILEGES ON database.* FROM 'username'@'host';

--- Aplica as alterações de privilegios imediatamente
FLUSH PRIVILEGES;

--- Alterar a senha de usuário
ALTER TABLE 'username'@'host' IDENTIFIED BY 'nova_senha';

--- Excluir um usuário
DROP USER 'username'@'host';

--- Mostrar os privilégios do usuário
SHOW GRANTS FOR 'username'@'host';
SHOW GRANTS FOR 'kaique'@'localhost';

--- Em caso de erro ao aplicar privilégios ou efetivar eles:
mysqlcheck --repair --database mysql -u root

-- Visualizar todos os usuários (precisa ter privilegio SELECT ao bd mysql):
SELECT User, Host FROM mysql.user;

```