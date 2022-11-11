```c#
public class ClaseCliente:ClaseEntidad
{
	public enum IndiceCampos { IdCliente, EstadoCliente, Nombre, Apellido, TipoDocumento, Dni, Direccion, FechaNacimiento, Telefono};
	public enum IndiceCamposPK { IdCliente, EstadoCliente };
	public ClaseCampo IdCliente { get; set; }
	public ClaseCampo EstadoCliente { get; set; }
	public ClaseCampo Nombre { get; set; }
	public ClaseCampo Apellido { get; set; }
	public ClaseCampo TipoDocumento { get; set; }
	public ClaseCampo Dni { get; set; }
	public ClaseCampo Direccion { get; set; }
	public ClaseCampo FechaNacimiento { get; set; }
	public ClaseCampo Telefono { get; set; }

	public ClaseCliente()
	{
		NombreTabla = "CLIENTE_NICO";
		IdCliente = new ClaseCampo();
		EstadoCliente = new ClaseCampo();
		Nombre = new ClaseCampo();
		Apellido = new ClaseCampo();
		TipoDocumento = new ClaseCampo();
		Dni = new ClaseCampo();
		Direccion = new ClaseCampo();
		FechaNacimiento = new ClaseCampo();
		Telefono = new ClaseCampo();

		Campos = new List<ClaseCampo>();
		CamposPK = new List<ClaseCampo>();
		CargarCampos();
	}

	private void CargarCampos()
	{
		CamposPK.Add(IdCliente);
		Campos.Add(IdCliente);
		Campos.Add(EstadoCliente);
		Campos.Add(Nombre);
		Campos.Add(Apellido);
		Campos.Add(TipoDocumento);
		Campos.Add(Dni);
		Campos.Add(Direccion);
		Campos.Add(FechaNacimiento);
		Campos.Add(Telefono);
	}
}
```
