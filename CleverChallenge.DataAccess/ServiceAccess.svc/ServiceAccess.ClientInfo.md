```C#
public List<ConsultaClient> ClientInfo(string Dni)
{
	CVClientes dtVista = new CVClientes();
	List<ConsultaClient> resultado = new List<ConsultaClient>();

	using (DataBase db = new DataBase())
	{
		using (DbDataReader reader = dtVista.LeerReader(db))
		{
			while (reader.Read()) {
				ConsultaClient consultaclient = new ConsultaClient();

				consultaclient.IdCliente = FunctionsHelper.GetValueDataBase<int>(reader, (int)CVClientes.IndiceSeleccion.SlIdcliente);
				consultaclient.Nom = FunctionsHelper.GetValueDataBase<string>(reader, (int)CVClientes.IndiceSeleccion.SlNom);
				consultaclient.Ape = FunctionsHelper.GetValueDataBase<string>(reader, (int)CVClientes.IndiceSeleccion.SlApe);
				consultaclient.TipDoc = FunctionsHelper.GetValueDataBase<string>(reader, (int)CVClientes.IndiceSeleccion.SlIdtipodoc);
				consultaclient.Dni = FunctionsHelper.GetValueDataBase<string>(reader, (int)CVClientes.IndiceSeleccion.SlDni);
				consultaclient.Dir = FunctionsHelper.GetValueDataBase<string>(reader, (int)CVClientes.IndiceSeleccion.SlDir);
				consultaclient.FecNac = FunctionsHelper.GetValueDataBase<DateTime>(reader, (int)CVClientes.IndiceSeleccion.SlFecnac);
				consultaclient.Tel = FunctionsHelper.GetValueDataBase<string>(reader, (int)CVClientes.IndiceSeleccion.SlTel);
				consultaclient.EstadoCliente = FunctionsHelper.GetValueDataBase<int>(reader, (int)CVClientes.IndiceSeleccion.SlIdestadocliente);
				resultado.Add(consultaclient);
			}
		}
	}
	return resultado;
}
```

[[CleverChallenge.DataAccess/Model/ConsultaClient.cs/ConsultaClient]] [[CVClientes]] [[CleverChallenge.DataAccess/IServiceAccess.cs/IServiceAccess|ClientInfo]]
