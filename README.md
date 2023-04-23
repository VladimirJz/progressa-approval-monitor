PROGRESSA APPROVAL MONITOR (pgssam).

Servicio initd para monitorear las autorizaciones de Lineas de Crédito en SAFI.


1 : Instalar el servicio initd
copiar:
    
    pgssam.service 
    (Controla el inicio y administración del servicio Linux)

    
a:
    /etc/systemd/system/

2: Copiar los Scripts de Ejecución
    pgssam.py
    (Es ejecutado al iniciar el servicio pgssam.service,administra la ejecución de un script python cada determinado tiempo, como parte del loop del servicio.)

    approval_monitor.py
    (Es la rutina principal, todo cambio en la lógica de ejecución debe ser realizado aqui o mediante el archivo de configuración safi.cfg)


Inciar servicio

#> service pgssam start

Verificar el estatus del servicio:

#> service pgssam status

        ● pgssam.service - Progressa - Approval Monitor Service
            Loaded: loaded (/etc/systemd/system/pgssam.service; disabled; vendor preset: enabl>
            Active: active (running) since Wed 2023-04-19 12:16:54 CST; 3 days ago
        Main PID: 2546875 (python3)
            Tasks: 1 (limit: 19115)
            Memory: 19.9M
            CGroup: /system.slice/pgssam.service
                    └─2546875 /opt/progressa/srv/approval-monitor/dev/bin/python3 /opt/progres>


