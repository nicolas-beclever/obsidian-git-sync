```c#
public class ClaseCredito : ClaseEntidad
{
	public enum IndiceCampos { IdCliente, EstadoCliente, Nombre, Apellido, TipoDocumento, Dni, Direccion, FechaNacimiento, Telefono };
	public enum IndiceCamposPK { IdCredito, IdCliente };
	public ClaseCampo IdCredito { get; set; }
	public ClaseCampo IdCliente { get; set; }
	public ClaseCampo MontoSolicitado { get; set; }
	public ClaseCampo CuotasMaximas { get; set; }
	public ClaseCampo CuotasPagas { get; set; }
	public ClaseCampo Interes { get; set; }

	public ClaseCredito()
	{
		NombreTabla = "CREDITO_NICO";
		IdCredito = new ClaseCampo();
		IdCliente = new ClaseCampo();
		MontoSolicitado = new ClaseCampo();
		CuotasMaximas = new ClaseCampo();
		CuotasPagas = new ClaseCampo();
		Interes = new ClaseCampo();

		Campos = new List<ClaseCampo>();
		CamposPK = new List<ClaseCampo>();
		CargarCampos();
	}

	private void CargarCampos()
	{
		CamposPK.Add(IdCredito);
		CamposPK.Add(IdCliente);
		Campos.Add(MontoSolicitado);
		Campos.Add(CuotasMaximas);
		Campos.Add(CuotasPagas);
		Campos.Add(Interes);
	}
}
```

