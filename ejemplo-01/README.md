# Ejemplo 01

Este ejemplo muestra la **instalación de la pila LAMP** utilizando el módulo [`command`][1].

Recuerde que la diferencia que existe entre los módulos [`command`][1] y [`shell`][2] es que en el módulo [`command`][1] los comandos no se ejecutan a través de una shell, por lo tanto, no podremos hacer uso de variables de entorno ni de las operaciones:  `<`, `>`, `|`, `;` y  `&`.

> **NOTA:** Las buenas prácticas de Ansible recomiendan evitar el uso de los módulos [`command`][1] y [`shell`][2] en el caso de que existan módulos específicos que permitan realizar la misma tarea que el comando.

## Cómo indicar el usuario y la clave privada SSH

**Desde la línea de comandos**

Podemos utilizar los parámetros `--user` y ` --private-key`.

Ejemplo:

```bash
ansible-playbook -i inventario install_lamp.yaml --user ubuntu --private-key /home/josejuan/Lab/vockey.pem
```

**Desde el archivo de inventario**

Podemos utilizar las variables `ansible_user` y `ansible_ssh_private_key_file`.

Ejemplo:

```
[aws]
34.226.122.155
44.206.245.114

[all:vars]
ansible_user=ubuntuhttps://docs.ansible.com/ansible/latest/collections/ansible/builtin/shell_module.html
ansible_ssh_private_key_file=/home/josejuan/Lab/vockey.pem
```

## Cómo gestionar la validación del _fingerprint_ de las clave pública SSH

Al conectar por SSH por primera vez con una instancia tendremos que aceptar el _fingerprint_ de la clave SSH pública de la instancia remota.

Si en el archivo de inventario tiene varias instancias, al ejecutar nuestro playbook tendremos un error porque no podemos aceptar el _fingerprint_ de todas las instancias.

En el siguiente ejemplo se muestra lo que ocurre cuando ejecutamos un playbook sobre un archivo de inventario que tiene dos instancias. En este ejemplo, solo podemos aceptar el _fingerprint_ de la última instancia del inventario.

```
TASK [Gathering Facts] ******************************************************************************************************************
The authenticity of host '34.226.122.155 (34.226.122.155)' can't be established.
ECDSA key fingerprint is SHA256:AjA3b6U0HwxjtJ3PhhelcplOf0u5xoY8fiEuSATMAJg.

The authenticity of host '44.206.245.114 (44.206.245.114)' can't be established.
ECDSA key fingerprint is SHA256:FJS7iV7GpDIuZPykQ9VQfGRj8l0dfLU1FiZVYJ+gIjI.
Are you sure you want to continue connecting (yes/no/[fingerprint])? 
```

Existen varias soluciones para solucionar este problema, veamos algunas.

### Configurar la variable de entorno `ANSIBLE_HOST_KEY_CHECKING`

La primera solución es configurar la variable de entorno `ANSIBLE_HOST_KEY_CHECKING` a `False` para que no saltarnos el paso de aceptar el _fingerprint_ de las instancias remotas.

Para ejecutar nuestro playbook realizaríamos los siguientes pasos:


```bash
export ANSIBLE_HOST_KEY_CHECKING=False
```

```bash
ansible-playbook -i inventario install_lamp.yaml --user ubuntu --private-key /home/josejuan/Lab/vockey.pem
```

### Configurar SSH para que acepte por defecto el _fingerprint_ de las nuevas instancias

Podemos utilizar un parámetro en la conexión SSH para aceptar por defecto el _fingerprint_ de las nuevas instancias a las que vamos a conectarnos.

**Desde la línea de comandos**

Si lo hacemos desde la línea de comandos tendríamos que añadir el siguiente parámetro `--ssh-common-args '-o StrictHostKeyChecking=accept-new'` al comando de ejecución del playbook.

Por ejemplo:

```
ansible-playbook -i inventario install_lamp.yaml --user ubuntu --private-key /home/josejuan/Lab/vockey.pem --ssh-common-args '-o StrictHostKeyChecking=accept-new'
```

**Desde el archivo de inventario**

En el archivo de inventario podemos utilizar el parámetro `ansible_ssh_common_args` para configurar SSH y aceptar por defecto el _fingerprint_ de las nuevas instancias a las que vamos a conectarnos.

```
[aws]
34.226.122.155
44.206.245.114

[all:vars]
ansible_user=ubuntu
ansible_ssh_private_key_file=/home/josejuan/Lab/vockey.pem
ansible_ssh_common_args='-o StrictHostKeyChecking=accept-new'
```

[1]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/command_module.html
[2]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/shell_module.html