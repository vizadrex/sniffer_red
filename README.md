🕵️‍♂️ Proyecto 1: Sniffer de Red con Python
🔍 Objetivo
Detectar actividad sospechosa en la red local, como:

🛑 ARP Spoofing: Intentos de suplantación de direcciones MAC en la red.

🔎 Escaneo de puertos (SYN Scan): Detección de escaneos de puertos típicos utilizados por atacantes para encontrar vulnerabilidades.

Este sniffer analiza los paquetes en tiempo real usando la librería scapy y emite alertas cuando detecta alguna actividad sospechosa.

🛠️ Tecnologías usadas
Python 3.8+: Lenguaje de programación principal para el desarrollo.

Scapy: Herramienta para captura, análisis y manipulación de paquetes de red.

Librerías estándar de Python: time, collections, entre otras para funcionalidades adicionales.

📁 Estructura del Proyecto

sniffer_red/
├── sniffer/
│   ├── __init__.py
│   ├── arp_detector.py    # Detecta ARP Spoofing
│   ├── syn_detector.py    # Detecta escaneos de puertos
│   └── core.py            # Funcionalidad principal del sniffer
├── logs/
│   └── alertas.log        # Archivo de registro de alertas
├── main.py                # Script principal para ejecutar el sniffer
├── requirements.txt       # Dependencias del proyecto
└── README.md              # Instrucciones del proyecto


🔧 Instrucciones de Instalación y Configuración
1. Instalar Python 3.8+
Si no tienes Python 3.8 o superior, descárgalo e instálalo desde el sitio oficial.

Asegúrate de seleccionar la opción "Add Python to PATH" al instalarlo.

2. Descargar e instalar Npcap (Reemplazo de WinPcap)
Scapy en Windows necesita un adaptador de captura de paquetes como Npcap (que es compatible con WinPcap). Sigue estos pasos:

Descargar Npcap desde aquí.(https://www.winpcap.org/install/bin/WinPcap_4_1_3.exe)

Durante la instalación, selecciona la opción "WinPcap API-compatible Mode" para asegurar la compatibilidad con Scapy.

Reinicia tu computadora para aplicar los cambios.

3. Crear y activar el entorno virtual
Para evitar conflictos de dependencias, es recomendable crear un entorno virtual. Sigue estos pasos:

Abre PowerShell (como administrador si es necesario) o la terminal de tu elección y navega a la carpeta del proyecto:

cd C:\Users\vizad\Desktop\sniffer_red

Crea un entorno virtual:

bash
Copiar
Editar
python -m venv .venv
Activa el entorno virtual:

Windows (PowerShell):

bash
Copiar
Editar
.\.venv\Scripts\Activate.ps1
Linux/Mac:

bash
Copiar
Editar
source .venv/bin/activate
Cuando el entorno esté activo, deberías ver algo como (.venv) en tu terminal.

4. Instalar las dependencias del proyecto
Con el entorno virtual activado, instala las dependencias necesarias desde el archivo requirements.txt:

bash
Copiar
Editar
pip install -r requirements.txt
Este comando instalará scapy y otras dependencias del proyecto.

5. Ejecutar el Sniffer
Una vez que el entorno virtual esté configurado y las dependencias estén instaladas, puedes ejecutar el sniffer con el siguiente comando:

bash
Copiar
Editar
python main.py
🧠 Funcionamiento del Sniffer
Cuando ejecutas main.py, el sniffer comienza a capturar paquetes de red en tiempo real. Aquí te explico los componentes principales del código:

core.py
Este archivo contiene la lógica principal para capturar y analizar paquetes. Utiliza la función sniff() de scapy, que empieza a capturar paquetes hasta que se detiene manualmente. Cada paquete es procesado por la función packet_callback, que es donde se verifica si es sospechoso.

arp_detector.py
Este módulo detecta ARP Spoofing, que es cuando un atacante envía paquetes ARP falsificados para suplantar la dirección MAC de otro dispositivo en la red. Si se detecta una discrepancia entre las direcciones MAC, se genera una alerta.

syn_detector.py
Este módulo detecta escaneos de puertos utilizando paquetes SYN. Si detecta una cantidad inusual de intentos de conexión (indicativos de un escaneo), genera una alerta.

main.py
Este es el archivo principal. Al ejecutar python main.py, se inicia el sniffer, que captura los paquetes y pasa cada uno a packet_callback. Dependiendo del análisis de cada paquete, se emiten alertas.

Registro de alertas
Las alertas generadas durante la ejecución del sniffer se guardan en un archivo de log en la carpeta logs/alertas.log.

📝 Mejoras Futuras
Interfaz gráfica (GUI): Puedes añadir una interfaz visual para mostrar las alertas de forma más interactiva.

Notificaciones automáticas: Añadir notificaciones emergentes o por correo electrónico cuando se detecte actividad sospechosa.

Detección de más ataques: Ampliar la funcionalidad para detectar otros tipos de ataques de red, como DDoS o sniffing de contraseñas.

📚 Referencias
Scapy Documentation

Npcap Official Website







