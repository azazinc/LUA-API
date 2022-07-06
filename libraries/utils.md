# utils

#### **find\_signature(** string module\_name, string signature **)** <a href="#find_signature-string-module_name-string-signature" id="find_signature-string-module_name-string-signature"></a>

Return a pointer

```lua
local clantag_change_fn = utils.find_signature("engine.dll", "53 56 57 8B DA 8B F9 FF 15")
```

#### **create\_interface(** string module\_name, string interface\_name (short) **)** <a href="#create_interface-string-module_name-string-interface_name" id="create_interface-string-module_name-string-interface_name"></a>

Return a pointer

```
local entity_list = utils.create_interface("client.dll", "VClientEntityList")
```

