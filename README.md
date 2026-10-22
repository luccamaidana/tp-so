# Trabajo Práctico: Laboratorio de GNU/Linux
## Integrantes:
Martin Busnadiego 53020 martinbusnaisi@gmail.com
Juan Pablo Sacovechi 54431 juanpablosacovechiutn@gmail.com
Sofia Aylen Fleytas 52108 fleytassofiaaylen@gmail.com
Maidana Lucca 52407 luccamaidana03@gmail.com

## Etapa 2
### Creación de carpetas y archivos
```
maiden@Xubuntu:~/Desktop$ mkdir -p Departamentos/Contable/Balances
maiden@Xubuntu:~/Desktop$ mkdir -p Departamentos/Contable/Documentos
maiden@Xubuntu:~/Desktop$ mkdir -p Departamentos/Gerencia           
maiden@Xubuntu:~/Desktop$ mkdir -p Departamentos/Personal 
maiden@Xubuntu:~/Desktop$ mkdir -p Departamentos/Personal/Documentos
maiden@Xubuntu:~/Desktop$ mkdir -p Departamentos/Personal/Legajos   
maiden@Xubuntu:~/Desktop$ mkdir -p Departamentos/Ventas/Clientes 
maiden@Xubuntu:~/Desktop$ mkdir -p Departamentos/Ventas/Productos
maiden@Xubuntu:~/Desktop$ touch Departamentos/Gerencia/auditoria.log
maiden@Xubuntu:~/Desktop$ touch Departamentos/Contable/auditoria.log
maiden@Xubuntu:~/Desktop$ touch Departamentos/Personal/auditoria.log
maiden@Xubuntu:~/Desktop$ touch Departamentos/Ventas/auditoria.log
```
### tree
<img width="540" height="429" alt="image" src="https://github.com/user-attachments/assets/0fc90638-199c-4237-8212-07abab8ee863" />

## Etapa 3
Enlace simbólico (soft link):
```ln -s Departamentos/Contable/Balances Departamentos/Gerencia/acceso_balances.lnk```
Enlace físico (hard link):
```ln Departamentos/Contable/auditoria.log Departamentos/Contable/auditoria_espejo.log```

Comprobación de inodos:
```
ls -li Departamentos/Contable/
total 16
1735028 -r-xrwx--- 2 supervisor Contable    6 sep 29 19:43 auditoria_espejo.log
1735028 -r-xrwx--- 2 supervisor Contable    6 sep 29 19:43 auditoria.log
1735018 dr-xrwx--- 2 supervisor Contable 4096 sep 29 19:20 Balances
1735019 dr-xrwx--- 2 supervisor Contable 4096 sep 29 19:20 Documentos
```

```
ls -li Departamentos/Gerencia/
total 0
1735031 lrwxrwxrwx 1 supervisor Gerencia 31 sep 29 19:32 acceso_balances.lnk -> Departamentos/Contable/Balances
1735027 -rwx------ 1 supervisor Gerencia  0 sep 29 19:22 auditoria.log
```


## Etapa 4
### 1. Definición de la Estructura de Seguridad
### Creación de grupos
<img width="391" height="74" alt="image" src="https://github.com/user-attachments/assets/1cbcdc2d-efe5-4350-8d5b-b4c5d7249b45" />
<br>
Y con el comando ```tail -n 5 /etc/group``` verificamos los grupos creados:
<br>
<img width="373" height="114" alt="image" src="https://github.com/user-attachments/assets/d4611074-5bc5-43bd-91f9-1b754f519893" />

### Creación de cuentas de usuario
<img width="601" height="78" alt="image" src="https://github.com/user-attachments/assets/0c0340cc-691a-4cf5-9c9d-1fe929a9c08f" />
<br>
Verificamos los usuarios con ```id <nombre>```:
<br>
<img width="736" height="156" alt="image" src="https://github.com/user-attachments/assets/3676321c-ff0c-4e99-be21-14ec4073eec0" />

### Asignación de propiedades
<img width="797" height="96" alt="image" src="https://github.com/user-attachments/assets/d5bef25d-49c7-4213-a7e7-c78c44aee8cc" />
<br>
Verificamos que los permisos de propiedad se aplicaron correctamente:
<br>
<img width="583" height="116" alt="image" src="https://github.com/user-attachments/assets/834d7672-2269-4759-98bc-ebd1f8ac2f3a" />

### 2. Aplicación de la matriz de permisos
<img width="644" height="54" alt="image" src="https://github.com/user-attachments/assets/d6797f05-895e-4541-8cb9-d671f1f91465" />
<br>
Supervisor:
<br>
<img width="647" height="34" alt="image" src="https://github.com/user-attachments/assets/badadac0-6c35-41f4-bf56-8ebc297d7c3d" />
<br>
Verificamos:
<br>
<img width="586" height="118" alt="image" src="https://github.com/user-attachments/assets/c7844811-4adf-40f9-ab8e-368637deb359" />

## ETAPA 5: Entregables y Validación del Laboratorio
1- Demostramos fehacientemente que tanto auditoria.log como auditoria_espejo.log comparten de forma unívoca el mismo número de inodo.
<img width="770" height="115" alt="image" src="https://github.com/user-attachments/assets/92ec2db1-a4be-48ea-b8f5-ad9d01a61cbd" />
<br>
Número de inodo idéntico: La primera columna muestra el número de inodo (1735028). Ambos archivos comparten exactamente el mismo número, lo que prueba que apuntan al mismo bloque de datos físico en el disco.

Contador de enlaces (Link Count): La tercera columna (el número 2 ubicado después de los permisos) indica que existen 2 entradas en el sistema de archivos apuntando a ese mismo inodo.

2- Se aprecia la flecha indicativa de direccionamiento del enlace simbólico acceso_balances.lnk creado en el entorno de Gerencia.
<img width="772" height="94" alt="image" src="https://github.com/user-attachments/assets/b8ff0094-5f79-4a75-9ff4-3db1a4300d3a" />
<br>
La primera letra (l): Confirma que el objeto es un enlace simbólico (soft link).

La flecha (->): Muestra de forma explícita el direccionamiento desde el archivo acceso_balances.lnk hacia la carpeta destino /Departamentos/Contable/Balances.

Tamaño en bytes (ej. 31): Muestra que el enlace no contiene los datos reales, sino únicamente la cantidad de caracteres que componen la ruta del archivo o carpeta apuntada.

3- Prueba de Validación Cruzada Extrema:
<img width="727" height="99" alt="image" src="https://github.com/user-attachments/assets/ff8a5b37-820d-40d0-8bc0-d28bd19a5838" />
<br>
Principio de menor privilegio: Demuestra que las reglas octales aplicadas (570 en Contable) impiden que un usuario de un área ajena (juan de Ventas) pueda inspeccionar la información contable.

Redirección de flujo (STDERR): Confirma la captura correcta del canal 2 para auditar intentos fallidos de acceso a recursos protegidos.
