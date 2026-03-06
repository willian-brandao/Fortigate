
## Configurar IP estático 

```
config system interface
edit port1
set mode static
set ip 192.168.18.24 255.255.255.0
end
```

## Configurar gateway 
```
config router static
edit 1
set device port1
set gateway 192.168.18.1
end
```
