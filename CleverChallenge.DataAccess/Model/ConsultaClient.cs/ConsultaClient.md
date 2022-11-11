```c#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Runtime.Serialization;

namespace CleverChallenge.DataAccess.Model
{
    [DataContract]
    public class ConsultaClient
    {

        [DataMember()]
        public int IdCliente { get; set; }

        [DataMember()]
        public int EstadoCliente { get; set; }

        [DataMember()]
        public string Nom { get; set; }

        [DataMember()]
        public string Ape { get; set; }

        [DataMember()]
        public string TipDoc { get; set; }

        [DataMember()]
        public string Dni { get; set; }

        [DataMember()]
        public string Dir { get; set; }

        [DataMember()]
        public DateTime FecNac { get; set; }

        [DataMember()]
        public string Tel { get; set; }

    }
}