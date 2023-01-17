# ansible-playground

Repositorio para hacer experimentos con _playbooks_ de Ansible.

- [Ejemplo 01](ejemplo-01/). Módulo [`command`][1].
- [Ejemplo 02](ejemplo-02/). Módulo [`shell`][2].
- [Ejemplo 03](ejemplo-03/). Módulos [`apt`][3], [`service`][4] y [`copy`][5].
- [Ejemplo 04](ejemplo-04/). Uso de variables definidas en un _playbook_.
- [Ejemplo 05](ejemplo-05/). Uso de variables definidas en un archivo externo.
- [Ejemplo 06](ejemplo-06/). Uso de *handlers* en un _playbook_.
- [Ejemplo 07](ejemplo-07/). Módulos  [`mysql_db`][6] y [`mysql_user`][7].
- [Ejemplo 08](ejemplo-08/). Despliegue de phpMyAdmin.
- [Ejemplo 09](ejemplo-09/). Despliegue de una aplicación LAMP sencilla.
- [Ejemplo 10](ejemplo-10/). Ejecución condicional de tareas (Incompleto).
- [Ejemplo 11](ejemplo-11/). Uso de roles (Incompleto).

Ejemplos de Infraestructura como Código (IaC) en AWS.

- [Ejemplo 12](ejemplo-12/). Creación de un grupo de seguridad y una instancia EC2.
- [Ejemplo 13](ejemplo-13/). Creación y borrado de un grupo de seguridad, una instancia EC2 y una IP elástica.

[1]: https://docs.aws.amazon.com/es_es/cli/index.html
[2]: https://josejuansanchez.org/iaw/practica-aws-cli/index.html
[3]: https://josejuansanchez.org/iaw/

[1]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/command_module.html
[2]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/shell_module.html
[3]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html
[4]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/service_module.html
[5]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/copy_module.html
[6]: https://docs.ansible.com/ansible/2.9/modules/mysql_db_module.html
[7]: https://docs.ansible.com/ansible/latest/collections/community/mysql/mysql_user_module.html