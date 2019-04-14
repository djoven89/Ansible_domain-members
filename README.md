# Domain Members en Zentyal con Ansible

Mediante el uso del playbook '**join-domain.yaml**' se pretende unir clientes Ubuntu con entorno gráfico a un dominio gestionado por Zentyal.

**El playbook ha sido comprobado con las siguientes versiones:**

* **Servidor donde está instalado el Controlador de Dominio:** Zentyal 6 y Zentyal 5
* **Equipos clientes:** Ubuntu Desktop 18.04, Linux Mint 18

### **Variables a completar:**

* **domain_name** -> Nombre del dominio gestionado por Zentyal.
* **domain_admin** -> Nombre de un usuario con permisos de administrador del Controlador de Dominio.
* **domain_admin_password** -> Contraseña del usuario administrador del Controlador de Dominio.
* **domain_user** -> Nombre de un usuario del Controlador de Dominio.

### **Pasos a realizar**

1. Primero se han de establecer las variables en la parte superior del archivo de configuración '**join-domain.yaml**'.

2. Después, se ha de indicar la dirección IP o nombre de la máquina que queremos unir al dominio en el archivo '**hosts**'.

3. A continuación, habrá que modificar los valores de acceso a la máquina del cliente en el archivo '**ansible.cfg**'.


4. Una vez establecidas las configuraciones, se ha de comprobar la conectividad con el equipo cliente antes de proceder a lanzar el playbook:

        ansible -m ping linux-clients

5. Por último, ya sólo quedará ejecutar el playbook:

        ansible-playbook join-domain.yaml

**NOTA:** Para los 2 últimos pasos, recordad que están disponibles las opciones: 

* **'-k'** para indicar la contraseña del usuario cuando se conecte Ansible al equipo cliente (se omite este parámetro si se usan claves SSH).
* **'-K'** para la contraseña de sudo del usuario (se omite este parámetro si el usuario está configurado en el 'sudoers' para no pedirle la contraseña).