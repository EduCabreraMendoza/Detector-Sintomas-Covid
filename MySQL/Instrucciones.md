# Instrucciones para configurar la base de datos

1. Instalar mysql server
    - `sudo apt update`
    - `sudo apt install mysql-server`
2. Abrir MySQL
    - `sudo mysql`
3. Crear una nueva base de datos
    - `CREATE DATABASE detectorsintomas;`
4. Seleccionar base de datos
    - `use detectorsintomas;`
5. Crear una tabla llamada registro que contenga todos los campos necesarios
    - `CREATE TABLE registro (id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY, fecha TIMESTAMP DEFAULT CURRENT_TIMESTAMP, nombre CHAR (248) NOT NULL, crreo CHAR (248) NOT NULL, temp FLOAT(4,2) NOT NULL, bpm INT(1) UNSIGNED NOT NULL, sp02 INT(1) UNSIGNED NOT NULL, protodiagnostico CHAR (248) NOT NULL);`
6. Crear un usuario y darle privilegios con los comandos:
    - `CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';`
    - `GRANT ALL PRIVILEGES ON *.* TO 'newuser'@'localhost';`
7. El comando para registrar informacion desde Node-Red en la base de datos es:
    - `msg.topic = "INSERT INTO registro (nombre,correo,temp,bpm,sp02,protodiagnostico) VALUES ('" + global.get ("paciente") + "','" + global.get ("correo") + "'," + global.get ("temp") + "," + global.get ("hr") + "," + global.get ("spo2") + ",'" + global.get("protodiagnostico") + "');";`
    - `return msg;`
8. Puedes consultar el los datos dentro de la base de datos con el comando
    - `SELECT FROM * registro;`

Para salir de los comandos de MySQL, usar el comando exit;
