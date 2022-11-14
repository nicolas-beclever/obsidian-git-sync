```c#
public partial class ConsultaClient : object, System.Runtime.Serialization.IExtensibleDataObject
{
	private System.Runtime.Serialization.ExtensionDataObject extensionDataField;
	
	private string ApeField;
	private string DirField;
	private string DniField;
	private int EstadoClienteField;
	private System.DateTime FecNacField;
	private int IdClienteField;
	private string NomField;
	private string TelField;
	private string TipDocField;
	
	public System.Runtime.Serialization.ExtensionDataObject ExtensionData
	{
		get
		{
			return this.extensionDataField;
		}
		set
		{
			this.extensionDataField = value;
		}
	}
	
	[System.Runtime.Serialization.DataMemberAttribute()]
	public string Ape
	{
		get
		{
			return this.ApeField;
		}
		set
		{
			this.ApeField = value;
		}
	}
	
	[System.Runtime.Serialization.DataMemberAttribute()]
	public string Dir
	{
		get
		{
			return this.DirField;
		}
		set
		{
			this.DirField = value;
		}
	}
	
	[System.Runtime.Serialization.DataMemberAttribute()]
	public string Dni
	{
		get
		{
			return this.DniField;
		}
		set
		{
			this.DniField = value;
		}
	}
	
	[System.Runtime.Serialization.DataMemberAttribute()]
	public int EstadoCliente
	{
		get
		{
			return this.EstadoClienteField;
		}
		set
		{
			this.EstadoClienteField = value;
		}
	}
	
	[System.Runtime.Serialization.DataMemberAttribute()]
	public System.DateTime FecNac
	{
		get
		{
			return this.FecNacField;
		}
		set
		{
			this.FecNacField = value;
		}
	}
	
	[System.Runtime.Serialization.DataMemberAttribute()]
	public int IdCliente
	{
		get
		{
			return this.IdClienteField;
		}
		set
		{
			this.IdClienteField = value;
		}
	}
	
	[System.Runtime.Serialization.DataMemberAttribute()]
	public string Nom
	{
		get
		{
			return this.NomField;
		}
		set
		{
			this.NomField = value;
		}
	}
	
	[System.Runtime.Serialization.DataMemberAttribute()]
	public string Tel
	{
		get
		{
			return this.TelField;
		}
		set
		{
			this.TelField = value;
		}
	}
	
	[System.Runtime.Serialization.DataMemberAttribute()]
	public string TipDoc
	{
		get
		{
			return this.TipDocField;
		}
		set
		{
			this.TipDocField = value;
		}
	}
}
    
```