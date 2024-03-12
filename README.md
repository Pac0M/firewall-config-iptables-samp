# Español.
# Documentación para Redirección y Bloqueo de Tráfico con iptables

## Identificar el Tráfico Objetivo

Identificar el tráfico que deseamos redirigir o bloquear. Por ejemplo, podemos querer redirigir todo el tráfico TCP y UDP que llegue a un puerto específico o a una gama de puertos.

## Crear una Regla para Redirigir el Tráfico TCP

Para redirigir el tráfico TCP entrante a un puerto diferente, puedes utilizar la siguiente regla:

```bash
iptables -t nat -A PREROUTING -p tcp --dport PUERTO_ORIGEN -j REDIRECT --to-ports PUERTO_DESTINO
```

Reemplaza `PUERTO_ORIGEN` con el puerto de origen que deseas redirigir y `PUERTO_DESTINO` con el puerto al que deseas redirigir el tráfico.

## Crear una Regla para Redirigir el Tráfico UDP

Para redirigir el tráfico UDP entrante a un puerto diferente, puedes utilizar una regla similar:

```bash
iptables -t nat -A PREROUTING -p udp --dport PUERTO_ORIGEN -j REDIRECT --to-ports PUERTO_DESTINO
```

Nuevamente, reemplaza `PUERTO_ORIGEN` con el puerto de origen que deseas redirigir y `PUERTO_DESTINO` con el puerto al que deseas redirigir el tráfico UDP.

## Guardar las Reglas

En sistemas basados en Debian/Ubuntu:

```bash
sudo iptables-save > /etc/iptables/rules.v4
```

En sistemas basados en CentOS/RHEL:

```bash
sudo service iptables save
```

En sistemas con systemd:

```bash
sudo systemctl enable iptables
```

## Eliminar Tráfico No Deseado (Opcional)

Si deseas bloquear el tráfico no deseado en lugar de redirigirlo, puedes modificar la acción en las reglas de iptables. Por ejemplo, para eliminar el tráfico TCP no deseado, puedes usar:

```bash
iptables -A INPUT -p tcp --dport PUERTO -j DROP
```

Esto descartará todos los paquetes TCP entrantes en el puerto especificado.

## Redirección TCP con DNAT

Si deseas redirigir el tráfico TCP con la dirección de destino modificada, puedes usar la siguiente regla:

```bash
iptables -t nat -A PREROUTING -p tcp --dport PUERTO_ORIGEN -j DNAT --to-destination 192.0.2.255:9999
```

Reemplaza `PUERTO_ORIGEN` con el puerto de origen que deseas redirigir y `192.0.2.255:9999` con la dirección IP y puerto de destino al que deseas redirigir el tráfico TCP.

## Redirección UDP con DNAT

Si deseas redirigir el tráfico UDP con la dirección de destino modificada, puedes usar la siguiente regla:

```bash
iptables -t nat -A PREROUTING -p udp --dport PUERTO_ORIGEN -j DNAT --to-destination 192.0.2.255:9999
```

Reemplaza `PUERTO_ORIGEN` con el puerto de origen que deseas redirigir y `192.0.2.255:9999` con la dirección IP y puerto de destino al que deseas redirigir el tráfico UDP.

Saludos
