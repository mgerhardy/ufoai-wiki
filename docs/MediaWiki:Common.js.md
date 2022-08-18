function SelectPortletItem(id) {

`   var node = document.getElementById(id);`
`   node.setAttribute('class', 'selected');`

}

function FixSelectedTab() {

`   e = wgTitle.split("/");`
`   if (wgPageName == "Manual:FAQ")`
`       SelectPortletItem("n-FAQ-item");`
`   else if (e[0] == "Media")`
`       SelectPortletItem("n-Media");`
`   else if (e[0] == "Download")`
`       SelectPortletItem("n-Download-item");`
`   else if (e[0] == "News")`
`       SelectPortletItem("n-News-item");`
`   else if (e[0] == "About")`
`       SelectPortletItem("n-About");`
`   else if (e[0] == "Contact")`
`       SelectPortletItem("n-Contact");`
`   else`
`       SelectPortletItem("n-Contribute-item");`

}

function HideMetadataFromFilePage() {

`   // only for non connected people`
`   if (wgNamespaceNumber != 6 || wgUserName != null)`
`       return;`

`   var node = document.getElementById("filehistory")`

`   // is style feature supported?`
`   if (node && !node.style)`
`       return;`

`   while (node) {`
`       if (node.id == "catlinks")`
`           break;`
`       if (node.nodeType == 1) {`
`           node.style.display = "none";`
`       } else if (node.nodeType == 3) {`
`           node.nodeValue = "";`
`       }`
`       node = node.nextSibling;`
`   }`
`   `

}

addOnloadHook(FixSelectedTab); addOnloadHook(HideMetadataFromFilePage);

var caction = null;

function CactionAnimation() {

`   c = caction.pos / caction.duration;`
`   caction.title.style.paddingBottom = (0.5 + 1 * c) + "em";`
`   caction.caction.style.opacity = c;`
`   caction.caction.style.display = "block";`
`   if (caction.pos >= caction.duration)`
`       return;`
`   caction.pos++;`
`   setTimeout(CactionAnimation, 50);`

}

function StartCactionAnimation() {

`   if (wgUserName == null)`
`       return;`
`   caction = {};`
`   caction.duration = 20;`
`   caction.pos = caction.duration;`
`   displayedcaction = cookies.get("cactiondisplayed");`
`   if (!displayedcaction) {`
`       caction.pos = 0;`
`       cookies.set("cactiondisplayed", 1);`
`   }`
`   caction.title = document.getElementById("firstHeading");`
`   caction.caction = document.getElementById("p-cactions");`
`   CactionAnimation();`

}

addOnloadHook(StartCactionAnimation);

var cookies = {}

cookies.set = function (cookieName, cookieValue, expires, path) {

`   document.cookie = escape(cookieName) + '='`
`       + escape(cookieValue) + (expires ? '; EXPIRES=' + expires.toGMTString() : '')`
`       + "; PATH=/";`

}

cookies.get = function (cookieName) {

`   var cookieValue = null;`
`   var posName = document.cookie.indexOf(escape(cookieName) + '=' );`
`   if (posName != -1) {`
`       posValue = posName + (escape(cookieName) + '=' ).length;`
`       endPos = document.cookie.indexOf(';', posValue) ;`
`       if (endPos != -1) {`
`           cookieValue = unescape(document.cookie.substring(posValue, endPos));`
`       } else {`
`           cookieValue = unescape(document.cookie.substring(posValue));`
`       }`
`   }`
`   return cookieValue;`

}