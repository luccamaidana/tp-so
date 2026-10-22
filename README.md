# tp-so
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

## Etapa 4
### 1. Definición de la Estructura de Seguridad
### Creación de grupos
<img width="391" height="74" alt="image" src="https://github.com/user-attachments/assets/1cbcdc2d-efe5-4350-8d5b-b4c5d7249b45" />

Y con el comando ```tail -n 5 /etc/group``` verificamos los grupos creados:
<img width="373" height="114" alt="image" src="https://github.com/user-attachments/assets/d4611074-5bc5-43bd-91f9-1b754f519893" />

### Creación de cuentas de usuario
<img width="601" height="78" alt="image" src="https://github.com/user-attachments/assets/0c0340cc-691a-4cf5-9c9d-1fe929a9c08f" />
Verificamos los usuarios con ```id <nombre>```:
<img width="736" height="156" alt="image" src="https://github.com/user-attachments/assets/3676321c-ff0c-4e99-be21-14ec4073eec0" />

### Asignación de propiedades
<img width="797" height="96" alt="image" src="https://github.com/user-attachments/assets/d5bef25d-49c7-4213-a7e7-c78c44aee8cc" />

Verificamos que los permisos de propiedad se aplicaron correctamente:
<img width="583" height="116" alt="image" src="https://github.com/user-attachments/assets/834d7672-2269-4759-98bc-ebd1f8ac2f3a" />

### 2. Aplicación de la matriz de permisos
<img width="644" height="54" alt="image" src="https://github.com/user-attachments/assets/d6797f05-895e-4541-8cb9-d671f1f91465" />
Supervisor:
<img width="647" height="34" alt="image" src="https://github.com/user-attachments/assets/badadac0-6c35-41f4-bf56-8ebc297d7c3d" />
Verificamos:
<img width="586" height="118" alt="image" src="https://github.com/user-attachments/assets/c7844811-4adf-40f9-ab8e-368637deb359" />

