# Ejemplo 2

Este ejemplo muestra la **instalación de la pila LAMP** utilizando el módulo [`command`][1].

Recuerde que la diferencia que existe entre los módulos [`command`][1] y [`shell`][2] es que en el módulo [`command`][1] los comandos no se ejecutan a través de una shell, por lo tanto, no podremos hacer uso de variables de entorno ni de las operaciones:  `<`, `>`, `|`, `;` y  `&`.

> **NOTA:** Las buenas prácticas de Ansible recomiendan evitar el uso de los módulos [`command`][1] y [`shell`][2] en el caso de que existan módulos específicos que permitan realizar la misma tarea que el comando.

[1]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/command_module.html
[2]: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/shell_module.html