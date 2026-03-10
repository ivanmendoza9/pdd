#
```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace PatronPrototipoExamen
{
    class Program
    {
        static void Main(string[] args)
        {

            ExamenPrototype prototipoPatrones = new PatronesPrototype();
            ExamenPrototype prototipoBD = new BDPrototype();
            ExamenPrototype prototipoPOO = new POOPrototype();
            ExamenPrototype prototipoRedes = new RedesPrototype();

            ExamenPrototype examen1 = prototipoPatrones.Clone();
            examen1.Docente = "Maribel Guerrero";
            examen1.Grupo = "A";
            examen1.Salon = "9205";
            Console.WriteLine(examen1.VerExamen());

            ExamenPrototype examen2 = prototipoPatrones.Clone();
            examen2.Docente = "Rene Solis";
            examen2.Grupo = "B";
            examen2.Salon = "Lab D";
            Console.WriteLine(examen2.VerExamen());

            ExamenPrototype examen3 = prototipoBD.Clone();
            examen3.Docente = "Gabriela Tapia";
            examen3.Grupo = "A";
            examen3.Salon = "91L6";
            Console.WriteLine(examen3.VerExamen());

            ExamenPrototype examen4 = prototipoBD.Clone();
            examen4.Docente = "Rene Solis";
            examen4.Grupo = "B";
            examen4.Salon = "Lab D";
            Console.WriteLine(examen4.VerExamen());

            ExamenPrototype examen5 = prototipoPOO.Clone();
            examen5.Docente = "Adolfo Ruiz";
            examen5.Grupo = "A";
            examen5.Salon = "91L4";
            Console.WriteLine(examen5.VerExamen());

            ExamenPrototype examen6 = prototipoPOO.Clone();
            examen6.Docente = "Marco Rodriguez";
            examen6.Grupo = "B";
            examen6.Salon = "Lab I";
            Console.WriteLine(examen6.VerExamen());

            ExamenPrototype examen7 = prototipoRedes.Clone();
            examen7.Docente = "Diego Saul";
            examen7.Grupo = "A";
            examen7.Salon = "9202";
            Console.WriteLine(examen7.VerExamen());

            ExamenPrototype examen8 = prototipoRedes.Clone();
            examen8.Docente = "Jesus Ricardo Palma";
            examen8.Grupo = "B";
            examen8.Salon = "9308";
            Console.WriteLine(examen8.VerExamen());

            Console.ReadKey();

        }
    }


    // CLASE ABSTRACTA PROTOTYPE

    public abstract class ExamenPrototype
    {

        protected string _materia;
        protected string _clave;
        protected string _docente;
        protected string _grupo;
        protected string _salon;

        public string Docente { set => _docente = value; }
        public string Grupo { set => _grupo = value; }
        public string Salon { set => _salon = value; }

        public abstract ExamenPrototype Clone();

        public abstract string VerExamen();

    }


    // PROTOTIPO PATRONES DE DISEÑO

    public class PatronesPrototype : ExamenPrototype
    {

        public PatronesPrototype()
        {
            _materia = "Patrones de Diseño";
            _clave = "DS-001";
        }

        public override ExamenPrototype Clone()
        {
            return (PatronesPrototype)this.MemberwiseClone();
        }

        public override string VerExamen()
        {
            return $"Examen {_materia} Clave {_clave} Docente {_docente} Grupo {_grupo} Salon {_salon}";
        }

    }


    // PROTOTIPO BASES DE DATOS

    public class BDPrototype : ExamenPrototype
    {

        public BDPrototype()
        {
            _materia = "Bases de Datos";
            _clave = "BD-002";
        }

        public override ExamenPrototype Clone()
        {
            return (BDPrototype)this.MemberwiseClone();
        }

        public override string VerExamen()
        {
            return $"Examen {_materia} Clave {_clave} Docente {_docente} Grupo {_grupo} Salon {_salon}";
        }

    }


    // PROTOTIPO PROGRAMACION ORIENTADA A OBJETOS

    public class POOPrototype : ExamenPrototype
    {

        public POOPrototype()
        {
            _materia = "Programación Orientada a Objetos";
            _clave = "POO-003";
        }

        public override ExamenPrototype Clone()
        {
            return (POOPrototype)this.MemberwiseClone();
        }

        public override string VerExamen()
        {
            return $"Examen {_materia} Clave {_clave} Docente {_docente} Grupo {_grupo} Salon {_salon}";
        }

    }


    // PROTOTIPO REDES

    public class RedesPrototype : ExamenPrototype
    {

        public RedesPrototype()
        {
            _materia = "Redes";
            _clave = "RED-004";
        }

        public override ExamenPrototype Clone()
        {
            return (RedesPrototype)this.MemberwiseClone();
        }

        public override string VerExamen()
        {
            return $"Examen {_materia} Clave {_clave} Docente {_docente} Grupo {_grupo} Salon {_salon}";
        }

    }

}
```
