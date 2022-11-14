```C#
public partial class ServiceAccessClient : System.ServiceModel.ClientBase<CleverChallenge.CleverChallengeConsultaClient.IServiceAccess>, CleverChallenge.CleverChallengeConsultaClient.IServiceAccess
    {
    public System.Collections.Generic.List<CleverChallenge.CleverChallengeConsultaClient.Usuario> UsuariosConsultaPorFiltros(string IdUsuario, string Nombre, string Apellido, System.Nullable<int> idEntidad, System.Nullable<int> idSucursal, int Todos, int idCatUsuario, int topMaxReg, string IdUsuarioLog)
        {
            return base.Channel.UsuariosConsultaPorFiltros(IdUsuario, Nombre, Apellido, idEntidad, idSucursal, Todos, idCatUsuario, topMaxReg, IdUsuarioLog);
        }
        
	public System.Collections.Generic.List<CleverChallenge.CleverChallengeConsultaClient.ConsultaClient> ClientInfo(string Dni)
	{
		return base.Channel.ClientInfo(Dni);
	}
    }
```

[ClientBase]
[[CleverChallenge.Web/Clients/CleverChallangeConsultaClient.cs/IServiceAccess]]
[UsuariosConsultaPorFiltros]
[ClientInfo]