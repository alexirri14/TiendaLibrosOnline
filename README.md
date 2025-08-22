namespace TiendaLibrosOnline
{ 
    public class Libro
    {
       
        public string Titulo { get; set; }
        public string Autor { get; set; }
        public double Precio { get; set; }

        
        public Libro(string titulo, string autor, double precio)
        {
            Titulo = titulo;
            Autor = autor;
            Precio = precio;
        }

        
        public void MostrarInfo()
        {
            Console.WriteLine($"Título: {Titulo}, Autor: {Autor}, Precio: {Precio:C}");
        }

        public void ActualizarPrecio(double nuevoPrecio)
        {
            Precio = nuevoPrecio;
        }

        public string ObtenerAutor()
        {
            return Autor;
        }
    }
    public class Cliente
    {
       
        public string Nombre { get; set; }
        public string Email { get; set; }
        public string Direccion { get; set; }

       
        public Cliente(string nombre, string email, string direccion)
        {
            Nombre = nombre;
            Email = email;
            Direccion = direccion;
        }

        
        public void Registrar()
        {
            Console.WriteLine($"Cliente {Nombre} registrado con éxito.");
        }

        public void ActualizarDatos(string nuevoEmail, string nuevaDireccion)
        {
            Email = nuevoEmail;
            Direccion = nuevaDireccion;
        }

        public void MostrarCliente()
        {
            Console.WriteLine($"Nombre: {Nombre}, Email: {Email}, Dirección: {Direccion}");
        }
    }

 
    public class Pedido
    {
        public int NumeroPedido { get; set; }
        public DateTime Fecha { get; set; }
        public string Estado { get; set; }

       
        public Pedido(int numeroPedido, DateTime fecha)
        {
            NumeroPedido = numeroPedido;
            Fecha = fecha;
            Estado = "Pendiente";
        }

       
        public void ConfirmarPedido()
        {
            Estado = "Confirmado";
            Console.WriteLine($"Pedido #{NumeroPedido} confirmado.");
        }

        public void CancelarPedido()
        {
            Estado = "Cancelado";
            Console.WriteLine($"Pedido #{NumeroPedido} cancelado.");
        }

        public void MostrarPedido()
        {
            Console.WriteLine($"Pedido #{NumeroPedido} - Fecha: {Fecha.ToShortDateString()} - Estado: {Estado}");
        }
    }

 
    public class Carrito
    {
       
        public List<Libro> ListaLibros { get; set; }
        public double Total { get; private set; }
        public int IdCarrito { get; set; }

        
        public Carrito(int idCarrito)
        {
            IdCarrito = idCarrito;
            ListaLibros = new List<Libro>();
            Total = 0.0;
        }

      
        public void AgregarLibro(Libro libro)
        {
            ListaLibros.Add(libro);
            Console.WriteLine($"Libro '{libro.Titulo}' agregado al carrito.");
        }

        public double CalcularTotal()
        {
            Total = 0;
            foreach (var libro in ListaLibros)
            {
                Total += libro.Precio;
            }
            return Total;
        }

        public void VaciarCarrito()
        {
            ListaLibros.Clear();
            Total = 0;
            Console.WriteLine("El carrito ha sido vaciado.");
        }
    }
    class Program
    {
        static void Main(string[] args)
        {
            
            Libro libro1 = new Libro("El Quijote", "Cervantes", 50.0);
            Libro libro2 = new Libro("Cien Años de Soledad", "García Márquez", 70.0);

         
            Cliente cliente = new Cliente("Ana Pérez", "ana@mail.com", "Av. Los Olivos 123");
            cliente.Registrar();

            
            Carrito carrito = new Carrito(1);
            carrito.AgregarLibro(libro1);
            carrito.AgregarLibro(libro2);

            Console.WriteLine($"Total carrito: {carrito.CalcularTotal():C}");

        
            Pedido pedido = new Pedido(101, DateTime.Now);
            pedido.ConfirmarPedido();
            pedido.MostrarPedido();
        }
    }
}
