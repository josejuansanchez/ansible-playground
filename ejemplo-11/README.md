# Ejemplo 11

Comando para crear la estructura de directorios y archivos de un rol.

```
ansible-galaxy role init <nombre_rol>
```

Ejemplo:

```
ansible-galaxy role init lamp
```

```
.
├── README.md
├── defaults
│   └── main.yml
├── files
├── handlers
│   └── main.yml
├── meta
│   └── main.yml
├── tasks
│   └── main.yml
├── templates
├── tests
│   ├── inventory
│   └── test.yml
└── vars
    └── main.yml
```