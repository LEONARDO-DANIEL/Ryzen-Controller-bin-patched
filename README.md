
# 🧩Ryzen Controller-bin-patched
**ES**

Versión adaptada de **Ryzen Controller para Arch Linux**, diseñada para ejecutarse sin privilegios elevados ni contraseña. Esta edición utiliza scripts personalizados, integración vía sudoers.d, acceso gráfico temporal para root, y empaquetado reproducible mediante PKGBUILD. Ideal para usuarios del grupo wheel que buscan compatibilidad directa con el menú del sistema y ejecución segura desde terminal o entorno gráfico.

# 📦 Archivos incluidos

     Ryzen Controller-bin-patched/
      ├── ryzencontroller               # Script principal que registra la app en sudoers.d
      ├── ryzen-launcher                # Script que habilita acceso gráfico y ejecuta vía sudo
      ├── remove-ryzen-controller.hook  # Hook opcional para limpieza post-desinstalación
      ├── PKGBUILD                      # Script de empaquetado para Arch Linux
      └── README.md                     # Este archivo



#  🛠️ Características

**✅ Ejecutable desde menú o terminal sin contraseña.**

**✅ Registro en /etc/sudoers.d/ para ejecución controlada.**

**✅ Acceso gráfico temporal para root mediante xhost.**

**✅ Integración directa al menú del sistema (categoría personalizada).**

**✅ Instalación reproducible con makepkg.**

**✅ Hook para limpieza segura al desinstalar o actualizar.**


# 🔐 Integración con sudoers.d

Durante la instalación, se crea un archivo en /etc/sudoers.d/ con la siguiente línea:

    BASH
    %wheel ALL=(ALL) NOPASSWD: /opt/Ryzen\ Controller/ryzen-controller
- Esto permite que cualquier usuario del grupo wheel ejecute Ryzen Controller sin contraseña, manteniendo control de privilegios y evitando el uso manual de sudo.
 

# 🚀 Instalación rápida

    git clone https://github.com/tuusuario/Ryzen-Controller-bin-patched.git
    cd Ryzen-Controller-bin-patched
    makepkg -si
- Una vez instalado, puedes lanzar la aplicación desde el menú de inicio, o desde la terminal  ejecutando ryzen-launcher.


# 🧠 Notas técnicas
- **ryzencontroller** registra la ruta del ejecutable en sudoers.d, permitiendo ejecución sin contraseña.

- **ryzen-launcher** habilita acceso gráfico temporal para root con xhost, ejecuta Ryzen Controller vía sudo, y luego revoca el acceso:

      #!/bin/bash  
      xhost +SI:localuser:root  
      sudo /opt/Ryzen\ Controller/ryzen-controller --no-sandbox
      xhost -SI:localuser:root

- El **PKGBUILD** automatiza la instalación, incluyendo la entrada en el menú y la gestión de permisos.

- El hook **remove-ryzen-controller.hook** es opcional y puede integrarse a tu sistema de paquetes para limpieza post-desinstalación.


# 🧾 Créditos y licencia

Basado en el proyecto original RyzenController bajo licencia MIT. El script PKGBUILD fue adaptado a partir del paquete original del autor, ajustado para integrar los scripts modificados, la entrada en sudoers.d, y la instalación reproducible en Arch Linux. Esta versión mantiene los créditos originales y añade documentación modular para compatibilidad extendida.
