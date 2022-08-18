/\* edit this file to customize the monobook skin for the entire site
\*/

/\*

` UFO:AI Wiki Custom CSS`
` This CSS is live`
` Please be nice.`

` Code partly taken from `` of the Blender wiki.`

- /

/\* ============================================= \*/

- \> html \#column-one {

`   position: absolute;`
`   left: 0;`
`   top: 10em;`

}

1.  column-one {

`   margin: 0;`
`   padding: 0;`

}

1.  column-content {

`   float: none;`
`   /*margin: 0;*/`
`   margin: 0px auto;`
`   margin-top: 12.5em;`
`   max-width: 66em;`
`   width: auto;`

}

1.  content {

`   position: static;`
`   top:0;`
`   left:0;`
`   margin: 1em;`
`   margin-top: 0;`
`   background-color: transparent;`
`   border: none;`

}

/\* for the hotkey templates \*/ span.hotkeybg {

` background-color: #EAEAEA;`
` padding: 2px 1px 2px 1px;`
` white-space: nowrap;`

}

span.hotkey {

` color:black;`
` padding: 0px 3px 0px 3px;`
` background-color: #D8D8D8;`
` border-width: 1px;`
` border-style: solid;`
` border-color: #f2f2f2 #a7a7a7 #838383 #e3e3e3;`

} /\* to position the mouse icon properly in the hotkey template \*/
span.hotkeybg img {

`margin-bottom: 5px;`
`padding-right: 1px;`
`border: 0px;`

} /\* ============================================= \*/

/\* Nice formatting of the todo lists \*/ table.todolist {

` border: 1px solid white;`
` white-space: nowrap;`
` empty-cells: show;`
` /* testing border-top: border-collapse: collapse; */`

}

table.todolist th {

` background-color: #000022;`
` padding: 2px;`

}

table.todolist td {

` background-color: black;`
` vertical-align:top;`
` /* testing border-top: 3px solid #555555; */`

}

.infobox {

` border: 1px solid #aaa;`
` background-color: #f9f9f9;`
` color: black;`

}

/\* ============================================

`     FIX HEADER ACCORDING TO UFOAI HEADER`

============================================ \*/

body {

`   font-family: verdana, helvetica, arial, sans-serif;`
`   font: x-small sans-serif;`
`   background-color: #262626;`
`   color: white;`
`   margin: 0;`
`   padding: 0;`

}

/\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*/

1.  p-project-navigation {

`   position: absolute;`
`   top: 6.6em;`
`   left: 0em;`
`   margin: 0;`
`   white-space: nowrap;`
`   width: 100%;`
`   line-height: 1.1em;`
`   overflow: visible;`
`   background: none;`
`   border-collapse: collapse;`
`   padding: 0;`
`   list-style: none;`

}

1.  p-project-navigation ul {

`   list-style: none;`
`   position: relative;`
`   list-style-type: none;`
`   list-style-position: outside;`
`   margin: 0;`
`   padding: 0;`
`   padding-bottom: 3px;`
`   padding-left: 266px;`

}

1.  p-project-navigation li {

` line-height: 1.75em;`
` margin: 0;`
` padding: 0;`
` display: inline;`

}

1.  p-project-navigation li a {

` color: white;`
` background-color: transparent;`
` text-decoration: none;`
` font-weight: bold;`
` margin: 0;`
` padding: 0.5ex 0.5em 1ex 0.5em;`
` border: 1px solid #FFD800;`

}

1.  p-project-navigation li.selected a {

` color: black;`
` background-color: #ffd800;`
` text-decoration: none;`
` padding-bottom: 0.8ex;`
` border-top: 1px solid black;`
` border-right: 1px solid black;`
` border-left: 1px solid black;`
` position: relative;`
` left: 1px;`
` top: 1px;`

}

1.  p-project-navigation li a:hover {

` color: black;`
` background-color: #ffd800;`
` text-decoration: none;`
` padding-bottom: 0.8ex;`
` border-top: 1px solid black;`
` border-right: 1px solid black;`
` border-left: 1px solid black;`
` position: relative;`
` left: 1px;`
` top: 1px;`

}

1.  p-project-navigation h5 {

`   display: none;`

}

1.  p-project-navigation .pBody {

`   font-size: 1em;`
`   background-color: transparent;`
`   color: inherit;`
`   border-collapse: inherit;`
`   border: 0;`
`   padding: 0;`
`   margin: 0;`
`   border-bottom: 10px solid #FFD800;  /* 'steelblue' not recognised here by Opera */`

}

1.  p-project-navigation .hiddenStructure {

`   display: none;`

}

/\* Search portlet \*/

1.  p-search {

`   position: absolute;`
`   right: 0;`
`   top: 9.6em;`
`   z-index: 5;`
`   width: auto;`

}

1.  p-search h5 {

`   display: none;`

}

1.  p-search .pBody {

`   z-index: 0;`
`   padding: 0;`
`   margin: 0;`
`   border: none;`
`   overflow: visible;`
`   background: none;`

}

/\* Navigation portlet \*/

1.  p-wiki-navigation {

`   position: absolute;`
`   left: 0;`
`   top: 9.6em;`
`   z-index: 5;`

}

1.  p-wiki-navigation {

`   width: 100%;`
`   white-space: nowrap;`
`   padding: 0;`
`   margin: 0;`
`   border: none;`
`   background: none;`
`   overflow: visible;`
`   line-height: 1.2em;`

}

1.  p-wiki-navigation h5 {

`   display: none;`

}

1.  p-wiki-navigationh .portlet,
2.  p-wiki-navigation .pBody {

`   z-index: 0;`
`   padding: 0;`
`   margin: 0;`
`   border: none;`
`   overflow: visible;`
`   background: none;`

}

1.  p-wiki-navigation ul {

`   border: none;`
`   line-height: 1.4em;`
`   color: #2f6fab;`
`   padding: 0 2em 0 3em;`
`   margin: 0;`
`   text-align: left;`
`   list-style: none;`
`   z-index: 0;`
`   background: none;`
`   cursor: default;`

}

1.  p-wiki-navigation li {

`   z-index: 0;`
`   border: none;`
`   padding: 0;`
`   display: inline;`
`   color: #2f6fab;`
`   margin-left: 1em;`
`   line-height: 1.2em;`
`   background: none;`

}

/\* Toolbox portlet \*/

1.  p-tb {

`   margin: 1em auto;`
`   max-width: 66em;`
`   width: auto;`
`   white-space: nowrap;`
`   padding: 0;`
`   border: none;`
`   background: none;`
`   overflow: visible;`
`   line-height: 1.2em;`

}

1.  p-tb \> h5 {

`   display:none;`

}

1.  p-tb \> .pBody {

`   z-index: 0;`
`   margin: 0;`
`   border: none;`
`   overflow: visible;`
`   background: none;`
`   background-color: #303030;`
`   border-radius: 10px; -moz-border-radius: 10px;`
`   padding: 0.5em;`
`   margin-top:1px;`

}

1.  p-tb ul {

`   border: none;`
`   line-height: 1.4em;`
`   color: #2f6fab;`
`   padding: 0 2em 0 3em;`
`   margin: 0;`
`   text-align: left;`
`   list-style: none;`
`   z-index: 0;`
`   background: none;`
`   cursor: default;`

}

1.  p-tb li {

`   z-index: 0;`
`   border: none;`
`   padding: 0;`
`   display: inline;`
`   color: #2f6fab;`
`   margin-left: 1em;`
`   line-height: 1.2em;`
`   background: none;`

}

1.  p-cactions {

`   position: absolute;`
`   top: 16.8em;`
`   left: 0em;`
`   width: 100%;`
`   z-index: 2;`
`   display: none;`
`   padding: 0;`

}

1.  p-cactions .pBody {

`   margin: 0px auto;`
`   max-width: 66em;`
`   width: auto;`

}

1.  p-cactions li {

`   background-color: transparent;`
`   border: 0px;`

}

1.  p-cactions li a {

`   background-color: #101010;`
`   padding: 5px;`
`   border-radius: 5px; -moz-border-radius: 5px;`
`   border: 0px;`

}

1.  p-cactions li a:hover,
2.  p-cactions li.selected a {

`   background-color: #FFD800;`
`   color: black;`
`   padding: 5px;`

}

1.  firstHeading {

`background-color: #303030;`
`border-radius: 10px; -moz-border-radius: 10px;`
`border: none;`
`padding: 0.5em;`

}

table {

`background-color:transparent;`

}

1.  footer {

`border: none;`
`background-color: #101010;`
`padding: 10px;`
`padding-top: 20px !important;`
`margin: 0;`

}

/\* Gallery and images\*/

table.gallery {

`background-color: transparent !important;`
`border: 0 !important;`

}

table.gallery td {

`background-color: transparent !important;`
`border: 0 !important;`

}

div.thumbinner .image, table.gallery .thumb {

`border: 0 !important;`
`background-color: #303030;`
`border-top-right-radius: 10px; -moz-border-radius-topright: 10px;`
`border-top-left-radius: 10px; -moz-border-radius-topleft: 10px;`
`width: 100% !important;`
`margin: 0 !important;`
`margin-bottom: 1px !important;`

}

div.thumbinner .thumbcaption, table.gallery .gallerytext {

`background-color: #101010;`
`border-bottom-right-radius: 10px; -moz-border-radius-bottomright: 10px;`
`border-bottom-left-radius: 10px; -moz-border-radius-bottomleft: 10px;`
`padding: 5px !important;`

}

html .thumbimage, div.thumbinner {

`border:0 !important;`

}

1.  toc {

`background-color: #101010;`
`border-radius: 10px; -moz-border-radius: 10px;`
`border: none;`

}

.catlinks { background-color: \#101010;

`border: none;`
`border-radius: 10px; -moz-border-radius: 10px;`
`margin: -1em;`
`margin-top: 1em;`
`padding-left: 4em;`

}

div.mw-warning-with-logexcerpt {

`background-color: #101010;`
`border: none;`
`border-radius: 10px; -moz-border-radius: 10px;`
`padding: 10px;`

}

1.  wikiPreview \> h2:first-child {

`background-color: #101010;`
`padding: 10px;`
`margin: 0px;`
`margin-top: 10px;`
`border-top-left-radius: 10px; -moz-border-radius-topleft: 10px;`
`border-top-right-radius: 10px; -moz-border-radius-topright: 10px;`
`border: none;`

}

.previewnote {

`background-color: #101010;`
`padding: 10px;`
`border: none;`
`margin: 0px;`
`border-bottom-left-radius: 10px; -moz-border-radius-bottomleft: 10px;`
`border-bottom-right-radius: 10px; -moz-border-radius-bottomright: 10px;`

}

1.  filetoc {

`display: none;`

}

div.noarticletext, .fullMedia {

`padding: 5px;`
`border-radius: 10px; -moz-border-radius: 10px;`
`background-color: #101010;`
`border: none;`

}

/\* history \*/

1.  pagehistory li {

`   border: 0px solid transparent !important;`

}

1.  pagehistory li.selected {

`   background-color: transparent !important;`

}

/\* mediawiki 1.16 \*/

h4.mw-specialpagesgroup {

`   padding: 5px;`
`   padding-left: 1em;`
`   background-color: black;`
`   border-radius: 10px; -moz-border-radius: 10px;`
`   border-radius: 10px; -moz-border-radius: 10px;`

}

table.diff, td.diff-otitle, td.diff-ntitle {

`   background-color: #101010 !important;`

}

td.diff-context {

`   background-color: transparent !important;`

}

td.diff-deletedline {

`   background-color: #503030 !important;`

}

td.diff-addedline {

`   background-color: #305030 !important;`

}

/\* search \*/

.mw-search-formheader {

`   background-color: black;`
`   border-top-right-radius: 10px; -moz-border-radius-topright: 10px;`
`   border-top-left-radius: 10px; -moz-border-radius-topleft: 10px;`
`   border: 0;`

}

.mw-search-formheader li.current a {

`   color: white !important;`
`   font-weight:bold;`

}

1.  mw-searchoptions {

`   border: 0px solid transparent !important;`
`   background-color: black !important;`
`   border-bottom-right-radius: 10px; -moz-border-radius-bottomright: 10px;`
`   border-bottom-left-radius: 10px; -moz-border-radius-bottomleft: 10px;`

}

/\* table \*/

.wikitable {

`   background-color: transparent !important;`

} .wikitable th {

`   background-color: #000000 !important;`

}

.ufotable th { background-color: \#101010; padding: 10px; } .ufotable td
{ background-color: \#303030; padding: 10px; }

.ufotable tbody \> \*:first-child \> \*:first-child {
border-top-left-radius: 10px; -moz-border-radius-topleft: 10px; }
.ufotable tbody \> \*:first-child \> \*:last-child {
border-top-right-radius: 10px; -moz-border-radius-topright: 10px; }
.ufotable tbody \> \*:last-child \> \*:first-child {
border-bottom-left-radius: 10px; -moz-border-radius-bottomleft: 10px;}
.ufotable tbody \> \*:last-child \> \*:last-child {
border-bottom-right-radius: 10px; -moz-border-radius-bottomright: 10px;}

.feed-atom a {

`   background: url("/w/skins/common/images/feed-icon.png") center left no-repeat !important;`
`   padding-left: 16px !important;`
`   padding-right: 0px !important;`

}

/\*
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

`           STYLE FOR TALK PAGE DISCUSSION`

- - \*/

.ns-1 dd, .ns-3 dd, .ns-talk dd, .ns-5 dd, .ns-7 dd, .ns-9 dd, .ns-11
dd, .ns-13 dd,.ns-15 dd, .ns-101 dd, .ns-103 dd, .ns-105 dd {

`margin:0;`
`padding:0;`

}

.ns-1 dl, .ns-3 dl, .ns-talk dl, .ns-5 dl, .ns-7 dl, .ns-9 dl, .ns-11
dl, .ns-13 dl, .ns-15 dl, .ns-101 dl, .ns-103 dl, .ns-105 dl { /\*
border-top:solid 1px black; \*/

`border-left:solid 2px black;`
`padding-top:.5em;`
`padding-left:.5em;`
`padding-right:.2em;`
`padding-bottom:.2em;`
`margin-left:1em; `

}

.ns-1 dl, .ns-3 dl, .ns-talk dl, .ns-5 dl, .ns-7 dl, .ns-9 dl, .ns-11
dl, .ns-13 dl, .ns-15 dl, .ns-101 dl, .ns-103 dl, .ns-105 dl,

.ns-1 dl dl dl, .ns-3 dl dl dl, .ns-talk dl dl dl, .ns-5 dl dl dl, .ns-7
dl dl dl, .ns-9 dl dl dl, .ns-11 dl dl dl, .ns-13 dl dl dl, .ns-15 dl dl
dl, .ns-101 dl dl dl, .ns-103 dl dl dl, .ns-105 dl dl dl,

.ns-1 dl dl dl dl dl, .ns-3 dl dl dl dl dl, .ns-talk dl dl dl dl dl,
.ns-5 dl dl dl dl dl, .ns-7 dl dl dl dl dl, .ns-9 dl dl dl dl dl, .ns-11
dl dl dl dl dl, .ns-13 dl dl dl dl dl, .ns-15 dl dl dl dl dl, .ns-101 dl
dl dl dl dl, .ns-103 dl dl dl dl dl, .ns-105 dl dl dl dl dl,

.ns-1 dl dl dl dl dl dl dl, .ns-3 dl dl dl dl dl dl dl, .ns-talk dl dl
dl dl dl dl dl, .ns-5 dl dl dl dl dl dl dl, .ns-7 dl dl dl dl dl dl dl,
.ns-9 dl dl dl dl dl dl dl, .ns-11 dl dl dl dl dl dl dl, .ns-13 dl dl dl
dl dl dl dl, .ns-15 dl dl dl dl dl dl dl, .ns-101 dl dl dl dl dl dl dl,
.ns-103 dl dl dl dl dl dl dl, .ns-105 dl dl dl dl dl dl dl,

.ns-1 dl dl dl dl dl dl dl dl dl, .ns-3 dl dl dl dl dl dl dl dl dl,
.ns-talk dl dl dl dl dl dl dl dl dl, .ns-5 dl dl dl dl dl dl dl dl dl,
.ns-7 dl dl dl dl dl dl dl dl dl, .ns-9 dl dl dl dl dl dl dl dl dl,
.ns-11 dl dl dl dl dl dl dl dl dl, .ns-13 dl dl dl dl dl dl dl dl dl,
.ns-15 dl dl dl dl dl dl dl dl dl, .ns-101 dl dl dl dl dl dl dl dl dl,
.ns-103 dl dl dl dl dl dl dl dl dl, .ns-105 dl dl dl dl dl dl dl dl dl {
background:#262626; }

.ns-1 dl dl, .ns-3 dl dl, .ns-talk dl dl, .ns-5 dl dl, .ns-7 dl dl,
.ns-9 dl dl, .ns-11 dl dl, .ns-13 dl dl, .ns-15 dl dl, .ns-101 dl dl,
.ns-103 dl dl, .ns-105 dl dl,

.ns-1 dl dl dl dl, .ns-3 dl dl dl dl, .ns-talk dl dl dl dl, .ns-5 dl dl
dl dl, .ns-7 dl dl dl dl, .ns-9 dl dl dl dl, .ns-11 dl dl dl dl, .ns-13
dl dl dl dl, .ns-15 dl dl dl dl, .ns-101 dl dl dl dl, .ns-103 dl dl dl
dl, .ns-105 dl dl dl dl,

.ns-1 dl dl dl dl dl dl, .ns-3 dl dl dl dl dl dl, .ns-talk dl dl dl dl
dl dl, .ns-5 dl dl dl dl dl dl, .ns-7 dl dl dl dl dl dl, .ns-9 dl dl dl
dl dl dl, .ns-11 dl dl dl dl dl dl, .ns-13 dl dl dl dl dl dl, .ns-15 dl
dl dl dl dl dl, .ns-101 dl dl dl dl dl dl, .ns-103 dl dl dl dl dl dl,
.ns-105 dl dl dl dl dl dl,

.ns-1 dl dl dl dl dl dl dl dl, .ns-3 dl dl dl dl dl dl dl dl, .ns-talk
dl dl dl dl dl dl dl dl, .ns-5 dl dl dl dl dl dl dl dl, .ns-7 dl dl dl
dl dl dl dl dl, .ns-9 dl dl dl dl dl dl dl dl, .ns-11 dl dl dl dl dl dl
dl dl, .ns-13 dl dl dl dl dl dl dl dl, .ns-15 dl dl dl dl dl dl dl dl,
.ns-101 dl dl dl dl dl dl dl dl, .ns-103 dl dl dl dl dl dl dl dl,
.ns-105 dl dl dl dl dl dl dl dl,

.ns-1 dl dl dl dl dl dl dl dl dl dl, .ns-3 dl dl dl dl dl dl dl dl dl
dl, .ns-talk dl dl dl dl dl dl dl dl dl dl, .ns-5 dl dl dl dl dl dl dl
dl dl dl, .ns-7 dl dl dl dl dl dl dl dl dl dl, .ns-9 dl dl dl dl dl dl
dl dl dl dl, .ns-11 dl dl dl dl dl dl dl dl dl dl, .ns-13 dl dl dl dl dl
dl dl dl dl dl, .ns-15 dl dl dl dl dl dl dl dl dl dl, .ns-101 dl dl dl
dl dl dl dl dl dl dl, .ns-103 dl dl dl dl dl dl dl dl dl dl, .ns-105 dl
dl dl dl dl dl dl dl dl dl { background:#303030; }

/\* translation \*/

.mw-sp-translate-table th {

`   background-color: black !important;`

}

.mw-sp-translate-table tr {

`   background-color: #303030 !important;`

}

.mw-translate-edit-tmsugs {

`   background-color: #000000 !important;`
`   border-radius: 10px; -moz-border-radius: 10px;`
`   margin-bottom: 0.5em !important;`

}

/\* august 2013 - darkoneko \*/

div \#mw-content-text div#userloginForm, div \#mw-content-text
div#userlogin {

` background:transparent!important;`
` border: 0;`

}

1.  prefcontrol {

` padding:5px;`

}