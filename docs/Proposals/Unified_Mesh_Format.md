# Unified mesh format

## Motivation

As of now, UFO:AI rendering engine does not have an unified mesh format,
instead relying on every part of engine to have its own unique
representation; this results in massive code duplication, irregular
approach to rendering some effects (such as glow), and generally
complicates the engine. So, there is a reason for implementing simple
and universal container for all meshes.

## Environment

Technically, we are limited by requirement of being compatible to OpenGL
1.3 and OpenGL ES 1.1 (which are mostly the same), meaning that we have
2 guaranteed texture units and a very limited set of blending options,
therefore it seems that, for a minimal configuration, two texture
coordinates should suffice; also, from a design point of view, we do not
use complicated effects which require more than two texture coordinates
per vertex. So, that should be enough. Obviously, we should have a
position and (optional) normal for each vertex. Also, we could (and do)
use a vertex color for a material system, and tangents in case of GLSL
rendering path; those should be included, but kept as optional.

Compatibility with vertex buffers will require using separate arrays,
rather than one interleaved array. Compatibility with GL ES 1.1 requires
16-bit indices, so vertex count is limited at 65536.

## Universality

While using triangle strips reduces index array size, a lot of geometry
in current engine is better represented by triangle lists (aka "triangle
soup"), so latter is the preferred format. Also, some data is already
expanded to the triangle vertex list, so index array could be optional
(no point in having an identity index).

## Reducing data duplication

Sometimes (actually rather often for the current engine) we have to use
a partially edited copy of the mesh -- like replacing vertex colors for
material system's extra layers, or changing vertex positions for the MD2
model animations. It calls for the ability to share some arrays between
mesh instances, including some mechanism to check which arrays are
currently in use and deleting the unused ones.

(not currently included in implementation proposal)

## Implementation proposal

    struct UniMesh {
        int vertexCount; // size of vertex arrays; 0 means dummy (non-renderable) mesh
        int triangleCount; // amount of triangles in the mesh; 0 means that index array is not present and triangle count is vertexCount/3

        AABB bbox; // bounding box for this mesh

        // vertex arrays
        vec3_t *positionArray; // vertex positions
        vec3_t *normalArray; // vertex normals; optional
        vec3_t *tangentArray; // vertex tangents; optional
        vec3_t *bitangentArray; // vertex bitangents; optional
        vec2_t *baseTexCoordArray; // texture coordinates of base texture (diffuse+normal+glow)
        vec2_t *auxTexCoordArray; // texture coordinates of auxillary texture (lightmap, noisemap, etc); optional, this texture will be disabled if no coord array provided
        vec3_t *colorArray; // per-vertex color; optional, will use global OpenGL color if no color array provided (all ones by default)

        // vertex index array; size is triangleCount*3
        short *indexArray;

        // vertex buffer objects; 0 means not allocated
        int positionBuffer; // VBO handle for vertex positions
        int normalBuffer; // VBO handle for vertex normals
        int tangentBuffer; // VBO handle for vertex tangents
        int bitangentBuffer; // VBO handle for vertex bitangents
        int baseTexCoordBuffer; // VBO handle for texture coordinates of base texture
        int auxTexCoordBuffer; // VBO handle for texture coordinates of auxillary texture
        int colorBuffer; // VBO handle for per-vertex color

        int indexBuffer; // VBO handle for index array
    }

## Questions & unsolved problems (please discuss at the talk page, not here)

- Naming: TextureCoordinate is way too long, TexCoord is still long,
  Texc is not clear, and ST even more opaque. What is better?

  - nothing, use long descriptive names please.
    --[Mattn](User:Mattn "wikilink") 16:00, 30 November 2012 (SAST)
    - Considering that TexCoord is the most common abbreviation, it
      should be the best option to avoid way too long
      "TextureCoordinate"? [Sandro](User:Sandro "wikilink") 23:18, 1
      December 2012 (SAST)

- BSP and advanced model formats allow switching textures mid-mesh.
  Should we support it in this class or separately?

- If so, how?

- Do we have to keep bitangents or compute them in shader (as currently
  done)?

- (Re)build normals and tangents in this class or in the model loader?

- Tangents and bitangents should be bound only if appropriate shader is
  present; any ideas on how to do it transparently?