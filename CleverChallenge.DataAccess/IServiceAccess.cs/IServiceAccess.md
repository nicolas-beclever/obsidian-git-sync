```c#
[ServiceContract]
public interface IServiceAccess
{
	[OperationContract]
    List<ConsultaClient> ClientInfo(string Dni);
}
```
[ClientInfo]