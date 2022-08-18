We had some problems with broken savegames between some trunk versions.

So we looked forward into using a new library to save the data in xml
Format, which will help us using savegames between other versions. The
savegame will be position independent, so we can easily load older
versions of the game using default values for newly added variables.

I'm using a version of \[\], with some changes to make it fit, for our
savegames. The library will be compiled in the game, so we do not need
another external dependenci. I'm currently on implementing the save/load
functions, but it will take some more time.

Structure will be: <code>

`headerdata (not in XML)`
`<xml version="1.0" -- some global data -->`
`< SAVESYSTEM1 SAVESYSTEM1 DATA>`<structures>`< /SAVESYSTEM1>`
`< SAVESYSTEM2 SAVESYSTEM2 DATA>`<structures>`< /SAVESYSTEM2>`
`...`
</code>

The header looks like:

<code>
`typedef struct saveFileHeaderXml_s {`
`   int version; /**< which savegame version */`
`   int compressed; /**< is this file compressed via zlib */`
`   int dummy[14]; /**< maybe we have to extend this later */`
`   char gameVersion[16]; /**< game version that was used to save this file */`
`   char name[32]; /**< savefile name */`
`   char gameDate[32]; /**< internal game date */`
`   char realDate[32]; /**< real datestring when the user saved this game */`
`   long xml_size;`
`} saveFileHeaderXml_t;`

</code> Here we can/will store the length of the savegame, the other
parts haven't changed.

The XML Functions for writing data: <code>

`mxml_node_t * mxmlNewElement(mxml_node_t *parent, const char *name);            /* creates a new Node */`
`void mxml_AddString(mxml_node_t *parent, const char *name, const char *value);  /* Adds a string */`
`void mxml_AddBool(mxml_node_t *parent, const char *name, qboolean value);`
`void mxml_AddFloat(mxml_node_t *parent, const char *name, float value);`
`void mxml_AddDouble(mxml_node_t *parent, const char *name, double value);`
`void mxml_AddByte(mxml_node_t *parent, const char *name, byte value);`
`void mxml_AddShort(mxml_node_t *parent, const char *name, short value);`
`void mxml_AddInt(mxml_node_t *parent, const char *name, int value);`
`void mxml_AddLong(mxml_node_t *parent, const char *name, long value);`
`void mxml_AddPos3(mxml_node_t *parent, const char *name, const vec3_t pos);`
`void mxml_AddPos2(mxml_node_t *parent, const char *name, const vec2_t pos); `

</code> <code>

`mxml_AddInt(parent,"count", 5) `

</code> would create the structure: (parent node must exist) <code>

<parent count="5" />

</code>

</code> <code>

`mxml_AddPos3(parent,"position", pos) `

</code> would create the structure: (parent node must exist) <code>

<parent><position x="2" y="3" z=4" /></parent>

</code> Int, Short and Long will be written as long values (for
compatibility reasons with later versions), float will be stored as
double.

Functions to retrieve: <code>

`mxml_node_t * mxml_GetBoolean(mxml_node_t *parent, const char *name, qboolean * value, const qboolean defaultval);`
`mxml_node_t * mxml_GetByte(mxml_node_t *parent, const char *name, byte * value, const byte defaultval);`
`mxml_node_t * mxml_GetNextByte(mxml_node_t *actual, mxml_node_t *parent, const char *name, byte *value, const byte defaultval);`
`mxml_node_t * mxml_GetShort(mxml_node_t *parent, const char *name, short * value, const short defaultval);`
`mxml_node_t * mxml_GetNextShort(mxml_node_t *actual, mxml_node_t *parent, const char *name, short *value, const short defaultval);`
`mxml_node_t * mxml_GetInt(mxml_node_t *parent, const char *name, int * value, const int defaultval);`
`mxml_node_t * mxml_GetNextInt(mxml_node_t *actual, mxml_node_t *parent, const char *name, int *value, const int defaultval);`
`mxml_node_t * mxml_GetLong(mxml_node_t *parent, const char *name, long * value, const long defaultval);`
`mxml_node_t * mxml_GetNextLong(mxml_node_t *actual, mxml_node_t *parent, const char *name, long *value, const long defaultval);`
`mxml_node_t * mxml_GetNode(mxml_node_t *parent, const char *name);`
`mxml_node_t * mxml_GetNextNode(mxml_node_t *current, mxml_node_t *parent, const char *name);`
`const char * mxml_GetString(mxml_node_t *parent, const char *name);`

`mxml_node_t * mxml_GetDouble (mxml_node_t *parent, const char *name, double *value, const double defaultval);`
`mxml_node_t * mxml_GetFloat (mxml_node_t *parent, const char *name, float *value, const float defaultval);`

</code> Every Getter Function (except the node ones) has as last
parameter a defaultvalue.

Ok, i'm not good at explaining s.th. like that, but perhaps you can give
me some more hints, what to do :)

I changed s.th. with the node structure, so some additional infos will
be required.

Some of the saving functions should be checked, if they can be stored
much more effecienly..