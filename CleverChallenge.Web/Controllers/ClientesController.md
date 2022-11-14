```C#
using CleverChallenge.CleverChallengeConsultaClient;
using CleverChallenge.Web.Filters;
using System.Web.Mvc;
using CleverChallenge.Web.ViewModel.Cliente;
using BeClever.Helper;
using CleverChallenge.Web.Common.Model;
using CleverChallenge.Security.Common;
using System.Collections.Generic;

namespace CleverChallenge.Web.Controllers
{
    [SessionExpireFilter]
    public class ClientesController : BeClever.Web.Mvc.BeCleverController
    {
        private ServiceAccessClient dataAccess = new ServiceAccessClient("IServiceAccess");

        public ActionResult Index()
        {
            return View();
        }

        public ActionResult Cgr_ClientParametros(ClientViewModel model)
        {
            //Si el viewmodel tiene el comando de la accion refrescar,
            if (!string.IsNullOrEmpty(model.CommandName) && model.CommandName.Equals(ActionCommands.Refrescar))
                //Hace algo con esto
                SessionData.SaveFilterSession(model);
            //Seteamos el FilterSession a el del modelo
            SessionData.SetFilterSession(model);

            //HabilitaCargaGrilla controla si el querystring de nuestro sea paginado. Y le pasamos el commandname del modelo. Solo chequea que sea un string no vacío
            if (FunctionsHelper.HabilitaCargaGrilla(this.Request.QueryString, model.CommandName))
            {
                //Creamos una nueva instancia de nuestro modelo
                ClientModel SeguParamsModel = new ClientModel();
                //Creamos una lista de ConsultaClient (datos) utilizando el metodo ClientInfo (info) ambos autogenerados en Web\Clients\CleverChallangeConsultaClient
                List<ConsultaClient> SeguParamsClient = dataAccess.ClientInfo(model.Dni);
                //
                model.ClientModel = FunctionsHelper.ParseModel(SeguParamsModel, SeguParamsClient);
            }

            model.WidthColumnActionButtons = Constants.WIDTH_BUTTON_GRID * FunctionsHelper.GetFunctionsSecurityExistent(SessionData.Instance.FunctionsSecurity
                , ObjectsSecurity.GrillaClientParametros
                , FunctionsSecurity.btnModificar
                , FunctionsSecurity.btnConsultar
                , FunctionsSecurity.btnAlta
                , FunctionsSecurity.btnEliminar).Count;

            if (!string.IsNullOrEmpty(model.CommandName)
                && model.CommandName.Equals(ActionCommands.Exportar))
            {
                ViewBag.PathToExport = FunctionsHelper.ExportGrid(FunctionsHelper.GetPathExportTmp(Request.PhysicalApplicationPath), model.ClientModel);
            }
            return PartialView(model);
        } 
        public ActionResult Cdat_ClientParametros()
        {
            return View();
        }

    }
}
```

[[Cgr_ClientParametros]]
[[ClientViewModel]]
[[Cdat_ClientParametros]]
[[Cgr_ClientParametros]]
[[ServiceAccessClient]]
[[ClientModel]]
[[ObjectsSecurity]]
[[FunctionsSecurity]] 
[[btnModificar]]
[[btnConsultar]]
[[btnAlta]]
[[btnEliminar]]

