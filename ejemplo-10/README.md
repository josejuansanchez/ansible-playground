# Ejemplo 10

Para configurar variables de entorno desde la línea de comandos podemos utilizar el modificador `-e` o `--extra-vars`. 

Por ejemplo, si queremos configurar la variable `my_var` con el valor `my_value` podríamos ejecutar el siguiente comando:

```
ansible-playbook main.yaml -e "my_var=my_value"
```

Si queremos configurar una tarea que solo se ejecute cuando una variable de entorno tiene un valor determinado, podemos configurar la condición `when` de la tarea de la siguiente forma:

```yaml
- name: Ejecutar certbot
  command:
    cmd: certbot --apache -d {{ domain }} -m {{ email }} --agree-tos --non-interactive
  when: certbot=="true"
  #when: certbot is defined
```

Para ejecutar el playbook desde la lína de comandos ejecutaríamos alguna de las siguientes opciones:

```
ansible-playbook main.yaml -e "certbot=true"
```

```
ansible-playbook main.yaml --extra-vars "certbot=true"
```