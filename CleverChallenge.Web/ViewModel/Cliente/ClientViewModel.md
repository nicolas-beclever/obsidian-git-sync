```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using CleverChallenge.Web.Common.Model;

namespace CleverChallenge.Web.ViewModel.Cliente
{
    public class ClientViewModel
    {
        public string CommandName { get; set; }
        public int WidthColumnActionButtons { get; set; }
        public string Dni { get; set; }
        public List<ClientModel> ClientModel;
    }
}
```

[[ClientModel]]
