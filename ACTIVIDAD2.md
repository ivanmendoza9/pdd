# Actividad2U2
## Elaborado por: Mendoza Suarez Ivan Gustavo 
## No. de Control: 22210910

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace singleton
{
    public class Central_911
    {
        private static Central_911 _instance;
        private static readonly object _lock = new object();

        public string Central { get; private set; }

        private Central_911()
        {
            Central = "Central 911";
        }

        public static Central_911 Obtener_Instancia()
        {
            if (_instance == null)
            {
                lock (_lock)
                {
                    if (_instance == null)
                    {
                        _instance = new Central_911();
                    }
                }
            }

            return _instance;
        }
        public void ConectarLlamada(Operador operador, string tipoEmergencia)
        {
            Console.WriteLine("\nLlamada conectada con el operador " + operador.Nombre);
            operador.AtiendeEmergencia(tipoEmergencia);
        }
    }

    public class Operador
    {
        public int Id_Operador { get; set; }
        public string Nombre { get; set; }

        public Operador(int id, string nombre)
        {
            Id_Operador = id;
            Nombre = nombre;
        }

        public void AtiendeEmergencia(string tipoEmergencia)
        {
            Console.WriteLine($"Operador {Nombre} atendiendo emergencia de tipo: {tipoEmergencia}");

            switch (tipoEmergencia)
            {
                case "Intento de suicidio":
                    Console.WriteLine("Enviando unidades de apoyo y rescate");
                    break;

                case "Incendio":
                    Console.WriteLine("Enviando bomberos.");
                    break;

                case "Accidente":
                    Console.WriteLine("Enviado paramedicos y oficiales.");
                    break;

                case "Violeta":
                    Console.WriteLine("Enviando una patrulla.");
                    break;

                case "Disturbios Via Publica":
                    Console.WriteLine("Enviando unidades locales.");
                    break;

                case "Asalto":
                    Console.WriteLine("Enviando unidades Fuerza Estatal.");
                    break;

                case "Terrorismo":
                    Console.WriteLine("Claudia Sheinbaum abre carpeta de investigacion.");
                    break;

                default:
                    Console.WriteLine("Tipo de emergencia no reconocido.");
                    break;
            }
        }
    }

    internal class Program
    {
        static void Main(string[] args)
        {
            Central_911 llamada1 = Central_911.Obtener_Instancia();
            Central_911 llamada2 = Central_911.Obtener_Instancia();
            Central_911 llamada3 = Central_911.Obtener_Instancia();

            // Operadores
            Operador op1 = new Operador(1, "Maribel");
            Operador op2 = new Operador(2, "Ivan");
            Operador op3 = new Operador(3, "Gonzalo");
            Operador op4 = new Operador(4, "Julio");
            Operador op5 = new Operador(5, "Moyra");

            // Llamadas
            llamada1.ConectarLlamada(op1, "Incendio");
            llamada2.ConectarLlamada(op2, "Accidente");
            llamada3.ConectarLlamada(op3, "Violeta");
            llamada1.ConectarLlamada(op4, "Intento de suicidio");
            llamada2.ConectarLlamada(op5, "Asalto");
            llamada3.ConectarLlamada(op1, "Disturbios Via Publica");
            llamada1.ConectarLlamada(op2, "Terrorismo");

            // Verificación de instancia única
            Console.WriteLine("\nVerificación de instancia única:");
            Console.WriteLine("llamada1 == llamada2 : " + ReferenceEquals(llamada1, llamada2));
            Console.WriteLine("llamada2 == llamada3 : " + ReferenceEquals(llamada2, llamada3));
            Console.WriteLine("llamada1 == llamada3 : " + ReferenceEquals(llamada1, llamada3));


            Console.ReadKey();
        }
    }
}
```
