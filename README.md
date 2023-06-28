# admin-site
**NOMBRE: DANIELA ZAPATA MORA**
**FECHA: Jun 28**

**RETO CAMPUSLANDS**
SE REQUIERE CONSTRUIR UN MODULO DE ADMINISTRADOR PARA LA GESTION DE INFORMACION
DE LA EMPRESA CAMPUSLANDS. LA EMPRESA CUENTA CON UNA BASE DE DATOS DONDE
ALMACENA LA INFORMACIÓN DE CADA UNO DE LOS CAMPERS Y SUS CONTACTOS. EL DISEÑO DE
BASE DE DATOS QUE TIENE CAMPUS ES LA SIGUIENTE (LA BASE DE DATOS SE DEBE LLAMAR
campuslands)

CREAMOS LA  BASE DE DATOS
CREATE DATABASE campuslands;

USE campuslands;

CREATE TABLE pais ( idPais int, nombrePais varchar(50));

CREATE TABLE departamento (idDep int, nombreDep varchar(50), idPais int);

CREATE TABLE region (idReg int, nombreReg varchar(50), idDep int);

CREATE TABLE campers (idCamper int, nombreCamper varchar(50), apellidoCamper varchar(50), fechaNac date, idReg int);

Siguiendo con el procedimiento, a continuacion 
definimos las llaves principales, añadiendo tambien aquellas que son foraneas

ALTER TABLE campers ADD PRIMARY KEY (idCamper), ADD KEY idReg(idReg);

ALTER TABLE region ADD PRIMARY KEY (idReg), ADD KEY idDep(idDep);

ALTER TABLE departamento ADD PRIMARY KEY (idDep), ADD KEY idPais(idPais);

ALTER TABLE pais ADD PRIMARY KEY (idPais); 

//SE REALIZA LA RELACION EN LLAVES

ALTER TABLE campers ADD CONSTRAINT idCamper FOREIGN KEY (idReg) REFERENCES region(idReg);

ALTER TABLE region ADD CONSTRAINT idReg FOREIGN KEY (idDep) REFERENCES departamento(idDep);

ALTER TABLE departamento ADD CONSTRAINT idDep FOREIGN KEY (idPais) REFERENCES pais(idPais);
