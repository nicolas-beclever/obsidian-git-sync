---
aliases: [MenuGeneral]
---
```html
@using BeClever.Helper
@using CleverChallenge.Security.Common
@using System.Linq
@using CleverChallenge.Web.Common

<ul class="dropdown-menu" role="menu">
    <li>
        <div class="navbar-collapse collapse " style="padding: 0px 0px 0px !important;">
            <div class="panel-group" id="accordion">
                @if (SessionData.Instance.IsValidLicense)
                {
                    //Lista de todos los permisos que tiene el usuario sin un elemento padre (en this.IdSeguObjetoPre) y opera sobre ellos
                    List<BeClever.Helper.Model.SeguPerfilFuncionClient> seguridadesMenu = SessionData.Instance.FunctionsSecurity.Where(m => string.IsNullOrEmpty(m.IdSeguObjetoPre) && m.Order > 0).OrderBy(c => c.Order).ToList();
                    foreach (var mnuBtn in seguridadesMenu)
                    {
                        //Sigo sin entender este punto de corte prematuro en el foreach
                        if (mnuBtn.IdSeguObjeto.Equals(ObjectsSecurity.SubMnuSeguPreguntas))
                        {
                            continue;
                        }
                        //Dibujamos un div con el contenedor
                        <div class="panel panel-default">
                            <!-- Div con el boton del elemento del menú-->
                            <div id="@("Boton" + @mnuBtn.IdSeguObjeto)" class="panel-header menubar" onclick="actualizoContadores(this)">
                                <h4 class="panel-title">
                                    <a class="btn btn_menugral" data-toggle="collapse" data-parent="#accordion" href="#@mnuBtn.IdSeguObjeto">
                                        @Functions.ReemplazarPalabraMenu(mnuBtn.IdSeguObjetoDes)
                                    </a>
                                </h4>
                            </div>

                            <!--Debajo otro div para los elementos hijos de el botón del menú-->
                            <div id="@mnuBtn.IdSeguObjeto" class="panel-collapse collapse">
                                @foreach (var mnu in SessionData.Instance.FunctionsSecurity.Where(m => !string.IsNullOrEmpty(m.IdSeguObjetoPre) && m.IdSeguObjetoPre.Equals(mnuBtn.IdSeguObjeto) && m.Order > 0).OrderBy(c => c.Order))
                                {
                                    //Si tiene url, crea un link, que se encarga de hacer un metodo get y pedir las cosas.
                                    if (!string.IsNullOrEmpty(mnu.Url))
                                    {
                                        <a id="@("lnk" + @mnu.IdSeguObjeto)" class="btn btn_submenu" data-ajax="true" data-ajax-begin="$('#modal-loader').modal('show');" data-ajax-loading="#modal-loader"
                                           data-ajax-method="GET" data-ajax-mode="replace" data-ajax-success="ResetValidationsForm();" data-ajax-update="#Content"
                                           data-ajax-url="@mnu.Url.Replace(Constants.UrlExternaReplace, BeClever.Configuration.ConfigManager.GetAppSetting(AppSettingsKeys.URLCleverChallenge)).Replace(Constants.UrlCleverChallengeReplace, BeClever.Configuration.ConfigManager.GetAppSetting(AppSettingsKeys.URLCleverChallenge))">@Functions.ReemplazarPalabraMenu(mnu.IdSeguObjetoDes)</a>
                                        <br />
                                    }
                                    else
                                    {
                                    //Si no tiene un url, crea un boton.
                                        <a class="btn btn_menu" data-toggle="collapse" data-parent="#@mnuBtn.IdSeguObjeto" href="#@mnu.IdSeguObjeto">
                                            @Functions.ReemplazarPalabraMenu(mnu.IdSeguObjetoDes)
                                        </a>
                                        //Tambien crea un div que se trae los componentes hijos del sub menú
                                        //Este foreach no se puede meter en una funcion que reciba una lambda?
                                        <div id="@mnu.IdSeguObjeto" class="panel-collapse collapse ">
                                            @foreach (var subMnu in SessionData.Instance.FunctionsSecurity.Where(m => !string.IsNullOrEmpty(m.IdSeguObjetoPre) && m.IdSeguObjetoPre.Equals(mnu.IdSeguObjeto) && m.Order > 0).OrderBy(c => c.Order))
                                            {
                                                //Si los elementos hijos de el sub menú tienen un url, crea un link hacia donde esta apuntando.
                                                if (!string.IsNullOrEmpty(subMnu.Url))
                                                {
                                                <a id="@("lnk" + @mnu.IdSeguObjeto)" class="btn btn_submenu" data-ajax="true" data-ajax-begin="$('#modal-loader').modal('show');" data-ajax-loading="#modal-loader"
                                                   data-ajax-method="GET" data-ajax-mode="replace" data-ajax-success="ResetValidationsForm();" data-ajax-update="#Content"
                                                   data-ajax-url="@subMnu.Url.Replace(Constants.UrlExternaReplace, BeClever.Configuration.ConfigManager.GetAppSetting(AppSettingsKeys.URLCleverChallenge)).Replace(Constants.UrlCleverChallengeReplace, BeClever.Configuration.ConfigManager.GetAppSetting(AppSettingsKeys.URLCleverChallenge))">@Functions.ReemplazarPalabraMenu(subMnu.IdSeguObjetoDes)</a>
                                                <br />
                                                }
                                            }
                                        </div>
                                    }
                                }
                            </div>
                        </div>
                    }
                }
                else
                {
                    //Mismo foreach que se encarga de traer los permisos de la sesión actual, pero tambien se fija que su IdSeguObjeto sea ObjectsSecurity.MnuLicenciamiento
                    foreach (var mnuBtn in SessionData.Instance.FunctionsSecurity.Where(m => string.IsNullOrEmpty(m.IdSeguObjetoPre) && m.IdSeguObjeto.Equals(ObjectsSecurity.MnuLicenciamiento) && m.Order > 0).OrderBy(c => c.Order))
                    {
                        //Sigo sin entender por que esto es necesario.
                        if (mnuBtn.IdSeguObjeto.Equals(ObjectsSecurity.SubMnuSeguPreguntas))
                        {
                            continue;
                        }
                        //Panel para contener todo
                        <div class="panel panel-default">
                            <!--Div con el botón de el menú-->
                            <div id="@("Boton" + @mnuBtn.IdSeguObjeto)" class="panel-header menubar" onclick="actualizoContadores(this)">
                                <h4 class="panel-title">
                                    <a class="btn btn_menugral" data-toggle="collapse" data-parent="#accordion" href="#@mnuBtn.IdSeguObjeto">
                                        @Functions.ReemplazarPalabraMenu(mnuBtn.IdSeguObjetoDes)
                                    </a>
                                </h4>
                            </div>
                            <!--Div que contiene los botones que van dentro del menú-->
                            <div id="@mnuBtn.IdSeguObjeto" class="panel-collapse collapse">
                                <!--A este foreach algun día lo voy a meter adentro de una lambda-->
                                @foreach (var mnu in SessionData.Instance.FunctionsSecurity.Where(m => !string.IsNullOrEmpty(m.IdSeguObjetoPre) && m.IdSeguObjetoPre.Equals(mnuBtn.IdSeguObjeto) && m.Order > 0).OrderBy(c => c.Order))
                                {
                                    //Si tiene url, hacemos un link
                                    if (!string.IsNullOrEmpty(mnu.Url))
                                    {
                                        <a id="@(" lnk" + @mnu.IdSeguObjeto)" class="btn btn_submenu" data-ajax="true" data-ajax-begin="$('#modal-loader').modal('show');" data-ajax-loading="#modal-loader"
                                            data-ajax-method="GET" data-ajax-mode="replace" data-ajax-success="ResetValidationsForm();" data-ajax-update="#Content"
                                            data-ajax-url="@mnu.Url.Replace(Constants.UrlExternaReplace, BeClever.Configuration.ConfigManager.GetAppSetting(AppSettingsKeys.URLCleverChallenge)).Replace(Constants.UrlCleverChallengeReplace, BeClever.Configuration.ConfigManager.GetAppSetting(AppSettingsKeys.URLCleverChallenge))">@Functions.ReemplazarPalabraMenu(mnu.IdSeguObjetoDes)</a>
                                        <br />
                                    }
                                }
                            </div>
                        </div>
                    }
                }

            </div>
        </div>
    </li>
</ul>

<script type="text/javascript">
    var xhrActualizarContador = null;

    $(function () {
        $('.dropdown-accordion').on('show.bs.dropdown', function (event) {
            var accordion = $(this).find($(this).data('accordion'));
            accordion.find('.panel-collapse.in').collapse('hide');
        });

        // Prevent dropdown to be closed when we click on an accordion link
        $('.dropdown-accordion').on('click', 'a[data-toggle="collapse"]', function (event) {
            event.preventDefault();
            event.stopPropagation();
            $($(this).data('parent')).find('.panel-collapse.in').collapse('hide');
            $($(this).attr('href')).collapse('show');
        })

        $('ul.dropdown-menu-filter [data-toggle=dropdown]').on('click', function (event) {
            // Avoid following the href location when clicking
            event.preventDefault();

            // Avoid having the menu to close when clicking
            event.stopPropagation();

            // opening the one you clicked on
            $(this).parent().addClass('open');

            var menu = $(this).parent().find("ul");
            var menupos = menu.offset();

            if ((menupos.left + menu.width()) + 30 > $(window).width()) {
                var newpos = -menu.width();
            } else {
                var newpos = $(this).parent().width();
            }
            menu.css({ left: newpos });

        });

        $('#accordion > .panel').each(function (index, element) {
            var $element = $(element),
                $header = $element.find('.panel-header').eq(0),
                $body = $element.find('.panel-collapse').eq(0),
                $dropdown_menu = null,
                html = '';

            html += '<li class="dropdown">' +
                '<a href="#" class="dropdown-toggle" data-toggle="dropdown" role="button" aria-haspopup="true" aria-expanded="false">' + $header.find('a').eq(0).text() + ' <span class="caret"></span></a>' +
                '<ul class="dropdown-menu">' +
                '</ul>' +
                '</li>';

            $('#menu-mobile').append(html);

            $dropdown_menu = $('#menu-mobile').find('.dropdown-menu').last();

            $body.find('a').each(function (indexBody, elementBody) {
                $dropdown_menu.append('<li></li>');

                $dropdown_menu.find('li').last().append($(elementBody).clone());
            });
        });

        var mnuOriginaciones = $("#lnkMnuOriginaciones").prop('text');
        var spanOriginaciones = $("#spanOriginaciones").text();
        if (mnuOriginaciones && spanOriginaciones == "") {
            $("#lnkMnuOriginaciones").append("<span id='spanOriginaciones'></span>")
        }
        var mnuDevoluciones = $("#lnkMnuDevoluciones").prop('text');
        var spanDevoluciones = $("#spanDevoluciones").text();
        if (mnuDevoluciones && spanDevoluciones == "") {
            $("#lnkMnuDevoluciones").append("<span id='spanDevoluciones'></span>")
        }
        var mnuTramites = $("#lnkMnuTramites").prop('text');
        var spanTramites = $("#spanTramites").text();
        if (mnuTramites && spanTramites == "") {
            $("#lnkMnuTramites").append("<span id='spanTramites'></span>")
        }
    });

    RecuperoOriginaciones = function () {
        var mnuOriginaciones = $("#lnkMnuOriginaciones").prop('text');
        var mnuDevoluciones = $("#lnkMnuDevoluciones").prop('text');
        var mnuTramites = $("#lnkMnuTramites").prop('text');
        bc.forms.setAjaxLoader(false);

        try {
            xhrActualizarContador.abort();
        }
        catch (ex) {
        }

        xhrActualizarContador = $.ajax({
            type: "GET",
            url: bc.common.strings.format("/" + bc.__BC_HOST_NAME + "/api/ApiFunctions/CountOriginaciones?llamaOriginaciones={0}&llamaReclamos={1}&llamaTramites={2}",
                mnuOriginaciones != undefined && mnuOriginaciones.length > 0,
                mnuDevoluciones != undefined && mnuDevoluciones.length > 0,
                mnuTramites != undefined && mnuTramites.length > 0),
            HttpMethod: "GET",
            success: function (data) {
                var array = String(data).split(',');


                if (mnuOriginaciones) {
                    var spanOriginaciones = $("#spanOriginaciones").text();
                    if (spanOriginaciones != '') {
                        $("#spanOriginaciones").text(' (' + array[0] + ')');
                    }
                    else {
                        $("#lnkMnuOriginaciones").append("<span id='spanOriginaciones'></span>")
                        $("#spanOriginaciones").text(' (' + array[0] + ')');
                    }

                }

                if (mnuDevoluciones) {
                    var spanDevoluciones = $("#spanDevoluciones").text();
                    if (spanDevoluciones != '') {
                        $("#spanDevoluciones").text(' (' + array[1] + ')');
                    }
                    else {
                        $("#lnkMnuDevoluciones").append("<span id='spanDevoluciones'></span>")
                        $("#spanDevoluciones").text(' (' + array[1] + ')');
                    }
                }

                if (mnuTramites) {
                    var spanTramites = $("#spanTramites").text();
                    if (spanTramites != '') {
                        $("#spanTramites").text(' (' + array[2] + ')');
                    }
                    else {
                        $("#lnkMnuTramites").append("<span id='spanTramites'></span>")
                        $("#spanTramites").text(' (' + array[2] + ')');
                    }
                }

                $("#spanOriginaciones").removeClass('MasVenc');
                $("#spanDevoluciones").removeClass('MasVenc');
                $("#spanTramites").removeClass('MasVenc');
                if (data[3] == 1) {
                    $('#spanOriginaciones').addClass('MasVenc')
                }
                if (data[3] == 2) {
                    $('#spanDevoluciones').addClass('MasVenc')
                }
                if (data[3] == 3) {
                    $('#spanTramites').addClass('MasVenc')
                }
                return;
            },
            always: function () {
                bc.forms.setAjaxLoader(true);
            }
        });
    }

    actualizoContadores = function (element) {
        var $element = $(element),
            $a = $element.find('a').eq(0);

        if (element.id == 'BotonMnuBtnOriginaciones' && ($a.attr('aria-expanded') == undefined || $a.attr('aria-expanded') == 'false')) {
            RecuperoOriginaciones();
        }
    }
</script>
```

[[ObjectsSecurity]]
[[SubMnuSeguPreguntas]]
