# Proyecto_Factura
Factura
namespace Modelo
{
    public class Persona
    {
        public Persona(string strNombre)
        {

        }
        protected string strNombre;

        public string Nombre
        {
            get { return strNombre; }
            set { strNombre = value; }
        }

        public virtual string Imprimir()
        {
            return "Nombre: " + Nombre;
        }
    }
    
    public class Cliente: Persona
    {
        protected string strRut;

        public string Rut
        {
            get { return strRut; }
            set { strRut = value; }
        }

        protected int intNTelefono;

        public int Telefono
        {
            get { return intNTelefono; }
            set { intNTelefono = value; }
        }

        protected int intNMobil;

        public int Mobil
        {
            get { return intNMobil; }
            set { intNMobil = value; }
        }

        protected string Direccion { get; set; }
        protected Comuna Comuna { get; set; }
        public Factura factura { get; set; }

        public override string Imprimir()
        {
            return base.Imprimir()+
                "\nRut: "+Rut+
                "\nTelefono: "+Telefono+
                "\nMobil: "+Mobil+
                "\nComuna: "+Comuna;
        }
    }
    
    public enum Comuna
    {

    }
    
    public class Vendedor: Persona
    {
        private string strClave;

        public string Clave
        {
            get { return strClave; }
            set { strClave = value; }
        }

        public override string Imprimir()
        {
            return base.Imprimir();
        }
    }
    public class Factura
    {
        private int intNumero;

        public int Numero
        {
            get { return intNumero; }
            set { intNumero = value; }
        }

        public int Unidad { get; set; }
        public DateTime Fecha { get; set; }
        public Producto producto { get; set; }
    }
    
    interface IImpuesto
    {
        public const double IVA = 0.19;
        string Imprimir();
    }
    
    public class Producto: IImpuesto
    {
        private string strCodigo;

        public string Codigo
        {
            get { return strCodigo; }
            set { strCodigo = value; }
        }
        public string Marca { get; set; }
        public string Modelo { get; set; }
        public float Precio { get; set; }
        public string Descripcion { get; set; }
        public string Garantia { get; set; }

        public virtual string Imprimir()
        {
            return "Marca: " + Marca +
                "\nModelo: " + Modelo +
                "\nPrecio: " + (Precio*IImpuesto.IVA) +
                "\nGarantia: " + Garantia;
        }
    }
    
    public class Mobil: Producto
    {

    }
}
