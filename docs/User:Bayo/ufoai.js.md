/\* function UseTranslationStatus(data) {

`   var table = document.getElementById("ufoaitranslationtable");`
`   var body = table.tBodies[0];`
`   var tr = body.rows[0];`

`   var title = document.createElement('th');`
`   title.appendChild(document.createTextNode('Status'));`
`   tr.appendChild(title);`

`   tr = body.rows[1];`
`   var lang = tr.cells[body.rows[1].length - 1];`
`   alert(lang.text);`

}

function RequestTranslationStatus() {

`   request = null;`
`   if (window.XMLHttpRequest) { `
`       request = new XMLHttpRequest();`
`   } else if (window.ActiveXObject) {`
`       request = new ActiveXObject("Microsoft.XMLHTTP");`
`   }`
`   if (!request)`
`       return;`

`   request.onreadystatechange = function() {`
`       if (this.readyState != 4)`
`           return;`
`       data = this.responseText;`
`       if (!JSON)`
`           return;`
`       // TODO catch error`
`       data = JSON.parse(data);`
`       UseTranslationStatus(data);`
`   }; `
`   request.open('GET', '/postats.json', true);`
`   request.send(null);`

}

function UpdateTranslationTable() {

`   var node = document.getElementById("ufoaitranslationtable");`
`   if (node)`
`       RequestTranslationStatus();`

}

addOnloadHook(UpdateTranslationTable);

- /