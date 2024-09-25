# Energia_sis

## Configuración del Puerto Serial

Para establecer la comunicación serial, es importante considerar dos propiedades claves:
1. **PortName**: Esta propiedad especifica el nombre del puerto serial al que se conectará el dispositivo. En Windows, los puertos seriales se identifican como `COM1`, `COM2`, etc. En Unix/Linux, se identifican como `/dev/ttyS0`, `/dev/ttyS1`, etc. Es esencial especificar el puerto correcto para establecer la comunicación con el dispositivo deseado.

2. **BaudRate**: Esta propiedad especifica la velocidad de transmisión de datos en bits por segundo (baudios). Es crucial que esta velocidad coincida con la configuración del dispositivo conectado. Si el dispositivo está configurado para comunicarse a una velocidad de 115200 baudios, como en este ejemplo, entonces la propiedad `BaudRate` debe establecerse en 115200 para que la comunicación sea exitosa.

## Relación con el Microcontrolador

Estas propiedades son fundamentales para establecer una comunicación correcta entre Unity y el microcontrolador. Si no se configuran correctamente, la comunicación puede no establecerse o puede ser inestable, lo que dificultaría la transmisión de datos entre ambos dispositivos Configurar correctamente es un paso importante para su correcto funcionamiento.

# Conexión entre Raspberry Pi Pico y Unity para Intercambio de Datos 
Estamos desarrollando una aplicación que establece una conexión entre un microcontrolador Raspberry Pi Pico y el motor gráfico Unity. Esta conexión permite intercambiar datos entre ambos sistemas, lo que nos permite controlar y monitorear dispositivos físicos desde una interfaz personalizada creada en Unity.

## Inclusiones de bibliotecas y declaración de enumeración
```c#
using System.Collections;
using System.Collections.Generic;
using System.IO.Ports;
using TMPro;
using UnityEngine;

// Enum para representar los estados de la tarea
enum TaskState
{
    INIT,               // Estado inicial
    WAIT_COMMANDS       // Esperando comandos
}
```
- Se incluyen las bibliotecas necesarias para el funcionamiento del código.
- Se declara una enumeración TaskState que define los posibles estados de la tarea.
- ##  Declaración de la clase y variables miembro
```c#
  public class ClassSerial : MonoBehaviour
{
    // Estado actual de la tarea
    private static TaskState taskState = TaskState.INIT;
    // Puerto serial
    private SerialPort _serialPort;
    // Buffer para datos del puerto serial
    private byte[] buffer;
    // Texto para mostrar información en la interfaz
    public TextMeshProUGUI myText;
    // Contador de frames
    private int counter = 0;
    // Texto para mostrar la respuesta del puerto serial en la interfaz
    [SerializeField] TextMeshProUGUI respuesta;
```

- Se declara la clase ClassSerial que hereda de MonoBehaviour, lo que permite que sea un componente de Unity.
- Se definen las variables miembro que se utilizarán en la clase, incluyendo el estado de la tarea, el puerto serial, un buffer para datos, objetos de texto para la interfaz, y un contador de frames.



# Documentos adicionales
[Narrativa](https://docs.google.com/document/d/1K9gSFbnjA_XSKQC1Gic211ZKTpIuZoDDYk1m6I1IJZ4/edit?usp=sharing)
