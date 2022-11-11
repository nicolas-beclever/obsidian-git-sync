```C#
public class CVClientes : ClaseVista
    {
        public enum IndiceFiltro { FlDni };

        public enum IndiceSeleccion { SlIdcliente, SlNom, SlApe, SlDni, SlDir, SlFecnac, SlTel, SlIdtipodoc, SlIdestadocliente };

        private ClaseDatoFiltro _flDni;

        private ClaseDatoSeleccion _slIdcliente;
        private ClaseDatoSeleccion _slNom;
        private ClaseDatoSeleccion _slApe;
        private ClaseDatoSeleccion _slDni;
        private ClaseDatoSeleccion _slDir;
        private ClaseDatoSeleccion _slFecnac;
        private ClaseDatoSeleccion _slTel;
        private ClaseDatoSeleccion _slIdtipodoc;
        private ClaseDatoSeleccion _slIdestadocliente;

        public ClaseDatoFiltro FlDni
        {
            get { return _flDni; }
            set { _flDni = value; }
        }

        public ClaseDatoSeleccion SlIdcliente
        {
            get { return _slIdcliente; }
            set { _slIdcliente = value; }
        }

        public ClaseDatoSeleccion SlNom
        {
            get { return _slNom; }
            set { _slNom = value; }
        }

        public ClaseDatoSeleccion SlApe
        {
            get { return _slApe; }
            set { _slApe = value; }
        }

        public ClaseDatoSeleccion SlDni
        {
            get { return _slDni; }
            set { _slDni = value; }
        }

        public ClaseDatoSeleccion SlDir
        {
            get { return _slDir; }
            set { _slDir = value; }
        }

        public ClaseDatoSeleccion SlFecnac
        {
            get { return _slFecnac; }
            set { _slFecnac = value; }
        }

        public ClaseDatoSeleccion SlTel
        {
            get { return _slTel; }
            set { _slTel = value; }
        }

        public ClaseDatoSeleccion SlIdtipodoc
        {
            get { return _slIdtipodoc; }
            set { _slIdtipodoc = value; }
        }

        public ClaseDatoSeleccion SlIdestadocliente
        {
            get { return _slIdestadocliente; }
            set { _slIdestadocliente = value; }
        }

        public CVClientes()
        {
            _flDni = new ClaseDatoFiltro(null, ConstantesData.TipoDato.VARCHAR2, "flDni");

            _slIdcliente = new ClaseDatoSeleccion("slIdcliente", " C0.Idcliente");
            _slNom = new ClaseDatoSeleccion("slNom", " C0.Nom");
            _slApe = new ClaseDatoSeleccion("slApe", " C0.Ape");
            _slDni = new ClaseDatoSeleccion("slDni", " C0.Dni");
            _slDir = new ClaseDatoSeleccion("slDir", " C0.Dir");
            _slFecnac = new ClaseDatoSeleccion("slFecnac", " C0.Fecnac");
            _slTel = new ClaseDatoSeleccion("slTel", " C0.Tel");
            _slIdtipodoc = new ClaseDatoSeleccion("slIdtipodoc", " C0.Idtipodoc");
            _slIdestadocliente = new ClaseDatoSeleccion("slIdestadocliente", " C0.Idestadocliente");

            Tablas = new List<ClaseDatoTabla>();
            Selecciones = new List<ClaseDatoSeleccion>();
            Condiciones = new List<string>();
            Relaciones = new List<ClaseDatoRelacion>();
            Filtros = new List<ClaseDatoFiltro>();
            Ordenes = new List<ClaseDatoOrden>();
            CargarTablas();
            CargarSelecciones();
            CargarCondiciones();
            CargarRelaciones();
            CargarFiltros();
            CargarOrdenes();
        }

        private void CargarTablas()
        {
            Tablas.Add(new ClaseDatoTabla("CLIENTES", "C0"));
            Tablas.Add(new ClaseDatoTabla("CREDITOS", "C1"));
        }

        private void CargarSelecciones()
        {
            Selecciones.Add(_slIdcliente);
            Selecciones.Add(_slNom);
            Selecciones.Add(_slApe);
            Selecciones.Add(_slDni);
            Selecciones.Add(_slDir);
            Selecciones.Add(_slFecnac);
            Selecciones.Add(_slTel);
            Selecciones.Add(_slIdtipodoc);
            Selecciones.Add(_slIdestadocliente);
        }

        private void CargarCondiciones()
        {
            Condiciones.Add("C0.Dni like upper('%' || flDni || '%') or flDni is null ");
        }

        private void CargarRelaciones()
        {
            Relaciones.Add(new ClaseDatoRelacion("CLIENTES", "CREDITOS", "C0.Idcliente", "C1.Idcliente", true));
        }

        private void CargarFiltros()
        {
            Filtros.Add(_flDni);
        }

        private void CargarOrdenes()
        {
        }

    }