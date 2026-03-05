# Actividad1U2
## Elaborado por: Mendoza Suarez Ivan Gustavo 
## No. de Control: 22210910

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace @abstract
{
    public abstract class MaterialFactory
    {
        public abstract Guia CrearGuia();

        public abstract Examen CrearExamen();

    }

    public abstract class Guia
    {
        public abstract void Mostrar();
    }

    public abstract class Examen
    {
        public abstract void Aplicar();
    }
}

namespace @abstract
{
    public class GuiaImpresa : Guia
    {
        public override void Mostrar()
        {
            Console.WriteLine("Mostrando la guia impresa...");
        }
    }

    public class ExamenEnPapel : Examen
    {
        public override void Aplicar()
        {
            Console.WriteLine("Se aplica examen en papel...");
        }
    }
}

namespace @abstract
{
    public class GuiaPDF : Guia
    {
        public override void Mostrar()
        {
            Console.WriteLine("Mostrando la guia PDF...");
        }
    }
    public class ExamenOnline : Examen
    {
        public override void Aplicar()
        {
            Console.WriteLine("Se aplica examen en linea...");
        }
    }
}

namespace @abstract
{
    public class GuiaSemi : Guia
    {
        public override void Mostrar()
        {
            Console.WriteLine("Mostrando la guia en Modalidad Hibrida (semipresencial)...");
        }
    }
    public class ExamenMixto : Examen
    {
        public override void Aplicar()
        {
            Console.WriteLine("Se aplica examen mixto...");
        }
    }
}

namespace @abstract
{
    public class MaterialPresencialFactory : MaterialFactory
    {
        public override Guia CrearGuia()
        {
            return new GuiaImpresa();
        }
    
        public override Examen CrearExamen()
        {
            return new ExamenEnPapel();
        }
    }
}

namespace @abstract
{
    public class MaterialVirtualFactory : MaterialFactory
    {
        public override Guia CrearGuia()
        {
            return new GuiaPDF();
        }

        public override Examen CrearExamen()
        {
            return new ExamenOnline();
        }
    }
}

namespace @abstract
{
    public class MaterialHibridoFactory : MaterialFactory
    {
        public override Guia CrearGuia()
        {
            return new GuiaSemi();
        }

        public override Examen CrearExamen()
        {
            return new ExamenMixto();
        }
    }
}
namespace @abstract
{
    internal class Program
    {
        static void Main(string[] args)
        {
            MaterialFactory fabrica;
            fabrica = new MaterialPresencialFactory();

            Guia guia = fabrica.CrearGuia();
            Examen examen = fabrica.CrearExamen();

            guia.Mostrar();
            examen.Aplicar();

            Console.WriteLine("");

            fabrica = new MaterialVirtualFactory();

            guia = fabrica.CrearGuia();
            examen = fabrica.CrearExamen();

            guia.Mostrar();
            examen.Aplicar();

            Console.WriteLine("");

            fabrica = new MaterialHibridoFactory();

            guia = fabrica.CrearGuia();
            examen = fabrica.CrearExamen();

            guia.Mostrar();
            examen.Aplicar();
        }
    }
}
```
