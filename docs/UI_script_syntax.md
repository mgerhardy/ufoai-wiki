***quoted-text*** : '"' \[^\n\]\* '"'

***const*** : \[A-Z\]\[A-Z0-9_\]\*

***number*** : \[0-9\]+(\\.\[0-9\]+)?

***boolean*** : 'true' \| 'false'

***property-name*** : \[a-z\]\[a-zA-Z0-9_\]+

***node-name*** : \[a-zA-Z0-9_\]+

***component-name*** : \[a-zA-Z0-9_\]+

***window-name*** : \[a-zA-Z0-9_\]+

***instruction*** : thing to define

***instruction-block*** : '{' ( *instruction* \| *instruction-block* )\*
'}'

***property*** : *property-name* \s+ ( *quotedtext* \| *const* \|
*number* \| *boolean* \| *instruction-block* )

***behaviour-name*** : everything from C++ code else
*func-behaviour-name*

***func-behaviour-name*** : 'func' \| 'confunc' \| 'cvarfunc'

***node-type*** : *behaviour-name* \| *component-name*

***node*** :


*node-type* \s+ *node-name* '{' *nodebody* '}'

\| *func-behaviour-name* \s+ *node-name* *instruction-block*

***node-body*** :


*property*\*

\| *node*\*

\| '{' *property*\* '}' *node*\*

***component*** : 'component' \s+ *component-name* \s+ 'extends' \s+
*node-type* '{' *node-body* '}'

***window*** :


'window' \s+ *window-name* \s+ 'extends' \s+ *window-name* '{'
*node-body* '}'

\| :'window' \s+ *window-name* \s+ '{' *node-body* '}'

***main*** : *component* \| *window*

[Category:GUIs](Category:GUIs "wikilink")