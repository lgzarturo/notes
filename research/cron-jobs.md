# cron-jobs

## Trabajando con Crontab

En Linux se puede hacer uso de un programador de tareas ubicado en /var/spool/cron/crontabs. No se puede acceder de forma directa a este archivo, el sistema operativo nos ofrece un comando.

```bash
crontrab -e * * * * * /usr/app/server.sh
```

Las expresiones cron tienen 6 valores obligatorios.

- Segundos. En nuestro ejemplo tiene el valor 0. Acepta valores del 0-59 y caracteres especiales como , `- * /`
- Minutos. En nuestro ejemplo tiene el valor 9. Acepta valores del 0-59 y caracteres especiales como , `- * /`
- Hora. En nuestro ejemplo tiene el valor 23. Acepta valores del 0-23 y caracteres especiales como , `- * /`
- Día del mes. En nuestro ejemplo tiene el carácter especial “?” el cual significa no definido ya que no deseamos que se ejecute un determinado día del mes, en su lugar deseamos que se ejecute un determinado día de la semana. Acepta valores del 1-31 y caracteres especiales como , `- * ? /`
- Mes. En nuestro ejemplo tiene el carácter especial `*` el cuál significa todos , es decir, deseamos se ejecute todos los meses. Acepta valores del 1-12 o abreviaturas JAN-DEC y caracteres especiales como , `- * /`
- Día de la semana. En nuestro ejemplo tiene el valor 5, es decir, deseamos se ejecute el quinto día (Viernes). Acepta valores del 1-7 o abreviaturas SUN-SAT y caracteres especiales como , `- * ? /`

> Quartz es un framework de scheduling que puede ser usado con Spring, sin embargo, en la mayoría de los casos el scheduling de spring será suficiente para nuestras tareas. Si deseamos una mayor potencia y flexibilidad como el soporte a tareas persistentes, transaccionales y distribuidas, entonces podemos considerar usar Quartz, aunque debo decir que usarlo es algo engorroso comparado con la sencillez de usar la anotación @Scheduling de Spring.

### Enlaces de interés

- [Herramienta para generar expresiones de Quartz][1]
- [Ejecutando tareas con Spring Scheduler][2]
- [Código de ejemplo usando Quartz con Spring Boot][3]
- [Expresiones Cron usando Spring Boot 2][4]

[1]:	https://crontab.cronhub.io
[2]:	https://windoctor7.github.io/Tareas-con-Spring-Scheduler.html
[3]:	https://github.com/windoctor7/codigo-tutoriales-blog/tree/master/spring-scheduler
[4]:	https://www.baeldung.com/cron-expressions