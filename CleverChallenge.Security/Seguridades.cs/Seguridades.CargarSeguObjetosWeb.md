```c#
public static void CargarSeguObjetosWeb()
	{
	//Clientes
	_seguObjetosIni.Add(new SeguObjetosIni(SeguPrograma.ChallengeWeb, ObjectsSecurity.SubMnuClientParametros, "Clientes", TipoSeguObjeto.Menu, ObjectsSecurity.MnuSeguGeneral, UrlObjectsSecurity.MnuSeguClientParametrosUrl, ObjectsSecurityOrder.SubMnuClientParametros, GeneralModule));
	_seguObjetosIni.Add(new SeguObjetosIni(SeguPrograma.ChallengeWeb, ObjectsSecurity.GrillaClientParametros, "Pantalla Clientes", TipoSeguObjeto.Grilla, ObjectsSecurity.SubMnuClientParametros, null, 0, GeneralModule));

	//Creditos
	_seguObjetosIni.Add(new SeguObjetosIni(SeguPrograma.ChallengeWeb, ObjectsSecurity.SubMnuCreditParametros, "Creditos", TipoSeguObjeto.Menu, ObjectsSecurity.MnuSeguGeneral, UrlObjectsSecurity.MnuCreditParametrosUrl, ObjectsSecurityOrder.SubMnuCreditParametros, GeneralModule));
	_seguObjetosIni.Add(new SeguObjetosIni(SeguPrograma.ChallengeWeb, ObjectsSecurity.GrillaCreditParametros, "Pantalla Creditos", TipoSeguObjeto.Grilla, ObjectsSecurity.SubMnuCreditParametros, null, 0, GeneralModule));
	}
```

[[SeguObjetosIni]]
[[SeguPrograma]]
[[ObjectsSecurity]]
[[TipoSeguObjeto]]
[[UrlObjectsSecurity]]
[[ObjectSecurityOrder]]
