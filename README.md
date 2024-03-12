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

# Inglish.
# Documentation for Traffic Redirection and Blocking with iptables

## Identify the Target Traffic

Identifying the traffic we want to redirect or block is essential. For example, we may want to redirect all TCP and UDP traffic arriving at a specific port or a range of ports.

## Create a Rule to Redirect TCP Traffic

To redirect incoming TCP traffic to a different port, you can use the following rule:

```bash
iptables -t nat -A PREROUTING -p tcp --dport SOURCE_PORT -j REDIRECT --to-ports DESTINATION_PORT
```

Replace `SOURCE_PORT` with the source port you want to redirect and `DESTINATION_PORT` with the port you want to redirect the traffic to.

## Create a Rule to Redirect UDP Traffic

To redirect incoming UDP traffic to a different port, you can use a similar rule:

```bash
iptables -t nat -A PREROUTING -p udp --dport SOURCE_PORT -j REDIRECT --to-ports DESTINATION_PORT
```

Again, replace `SOURCE_PORT` with the source port you want to redirect and `DESTINATION_PORT` with the port you want to redirect the UDP traffic to.

## Save the Rules

On Debian/Ubuntu-based systems:

```bash
sudo iptables-save > /etc/iptables/rules.v4
```

On CentOS/RHEL-based systems:

```bash
sudo service iptables save
```

On systems with systemd:

```bash
sudo systemctl enable iptables
```

## Remove Unwanted Traffic (Optional)

If you prefer to block unwanted traffic instead of redirecting it, you can modify the action in the iptables rules. For example, to remove unwanted TCP traffic, you can use:

```bash
iptables -A INPUT -p tcp --dport PORT -j DROP
```

This will discard all incoming TCP packets on the specified port.

## TCP Redirection with DNAT

If you want to redirect TCP traffic with modified destination address, you can use the following rule:

```bash
iptables -t nat -A PREROUTING -p tcp --dport SOURCE_PORT -j DNAT --to-destination 192.0.2.255:9999
```

Replace `SOURCE_PORT` with the source port you want to redirect and `192.0.2.255:9999` with the IP address and port you want to redirect the TCP traffic to.

## UDP Redirection with DNAT

If you want to redirect UDP traffic with modified destination address, you can use the following rule:

```bash
iptables -t nat -A PREROUTING -p udp --dport SOURCE_PORT -j DNAT --to-destination 192.0.2.255:9999
```

Replace `SOURCE_PORT` with the source port you want to redirect and `192.0.2.255:9999` with the IP address and port you want to redirect the UDP traffic to.

Regards

# Русский язык.
# Документация по перенаправлению и блокировке трафика с помощью iptables

## Определение Целевого Трафика

Определение трафика, который мы хотим перенаправить или заблокировать, является важным. Например, мы можем захотеть перенаправить весь TCP и UDP трафик, поступающий на определенный порт или диапазон портов.

## Создание Правила для Перенаправления TCP Трафика

Чтобы перенаправить входящий TCP трафик на другой порт, вы можете использовать следующее правило:

```bash
iptables -t nat -A PREROUTING -p tcp --dport ИСХОДНЫЙ_ПОРТ -j REDIRECT --to-ports ЦЕЛЕВОЙ_ПОРТ
```

Замените `ИСХОДНЫЙ_ПОРТ` на порт отправителя, который вы хотите перенаправить, а `ЦЕЛЕВОЙ_ПОРТ` на порт, на который вы хотите перенаправить трафик.

## Создание Правила для Перенаправления UDP Трафика

Чтобы перенаправить входящий UDP трафик на другой порт, вы можете использовать аналогичное правило:

```bash
iptables -t nat -A PREROUTING -p udp --dport ИСХОДНЫЙ_ПОРТ -j REDIRECT --to-ports ЦЕЛЕВОЙ_ПОРТ
```

Снова замените `ИСХОДНЫЙ_ПОРТ` на порт отправителя, который вы хотите перенаправить, а `ЦЕЛЕВОЙ_ПОРТ` на порт, на который вы хотите перенаправить UDP трафик.

## Сохранение Правил

Для систем на основе Debian/Ubuntu:

```bash
sudo iptables-save > /etc/iptables/rules.v4
```

Для систем на основе CentOS/RHEL:

```bash
sudo service iptables save
```

Для систем с systemd:

```bash
sudo systemctl enable iptables
```

## Удаление Нежелательного Трафика (По Желанию)

Если вы предпочитаете блокировать нежелательный трафик вместо его перенаправления, вы можете изменить действие в правилах iptables. Например, чтобы удалить нежелательный TCP трафик, вы можете использовать:

```bash
iptables -A INPUT -p tcp --dport PORT -j DROP
```

Это отбросит все входящие TCP пакеты на указанном порту.

## Перенаправление TCP с помощью DNAT

Если вы хотите перенаправить TCP трафик с измененным адресом назначения, вы можете использовать следующее правило:

```bash
iptables -t nat -A PREROUTING -p tcp --dport ИСХОДНЫЙ_ПОРТ -j DNAT --to-destination 192.0.2.255:9999
```

Замените `ИСХОДНЫЙ_ПОРТ` на порт отправителя, который вы хотите перенаправить, а `192.0.2.255:9999` на IP-адрес и порт, на который вы хотите перенаправить TCP трафик.

## Перенаправление UDP с помощью DNAT

Если вы хотите перенаправить UDP трафик с измененным адресом назначения, вы можете использовать следующее правило:

```bash
iptables -t nat -A PREROUTING -p udp --dport ИСХОДНЫЙ_ПОРТ -j DNAT --to-destination 192.0.2.255:9999
```

Замените `ИСХОДНЫЙ_ПОРТ` на порт отправителя, который вы хотите перенаправить, а `192.0.2.255:9999` на IP-адрес и порт, на который вы хотите перенаправить UDP трафик.

С наилучшими пожеланиями
