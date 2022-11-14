```C#
public class ClientModel
{
	[Export("IdCliente")]
	public int IdCliente { get; set; }
	[Export("EstadoCliente")]
	public string EstadoCliente { get; set; }
	[Export("Nombre")]
	public string Nombre { get; set; }
	[Export("Apellido")]
	public string Apellido { get; set; }
	[Export("TipoDocumento")]
	public string TipoDocumento { get; set; }
	[Export("Dni")]
	public string Dni { get; set; }
	[Export("Direccion")]
	public string Direccion { get; set; }
	[Export("FechaNacimiento")]
	public DateTime FechaNacimiento { get; set; }
	[Export("Telefono")]
	public string Telefono { get; set; }
}
```