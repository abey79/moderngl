.. _texture-format-label:

Texture Format
==============

.. py:currentmodule:: moderngl

Description
-----------

The format of a texture can be described by the ``dtype`` parameter
during texture creation. For example the :py:meth:`moderngl.Context.texture`.
The default ``dtype`` is ``f1``. Each component is an unsigned byte (0-255)
that is normalized when read in a shader into a value from 0.0 to 1.0.

The formats are based on the string formats used in numpy.

Some quick example of texture creation::

    # RGBA (4 component) f1 texture
    texture = ctx.texture((100, 100), 4)  # dtype f1 is default

    # R (1 component) f4 texture (32 bit float)
    texture = ctx.texture((100, 100), 1, dype="f4")

    # RG (2 component) u2 texture (16 bit unsigned integer)
    texture = ctx.texture((100, 100), 2, dtype="u2")


Texture contents can be passed in using the ``data`` parameter during
creation or by using the ``write()`` method. The object passed in
``data`` can be bytes or any object supporting the buffer protocol.

Float Textures
--------------

``f1`` textures are just unsigned bytes (8 bits per component) (``GL_UNSIGNED_BYTE``)

+----------+---------------+---------------+-------------------+
| **dtype**|  *Components* | *Base Format* | *Internal Format* |
+==========+===============+===============+===================+
| f1       |  1            | GL_RED        | GL_R8             |
+----------+---------------+---------------+-------------------+
| f1       |  2            | GL_RG         | GL_RG8            |
+----------+---------------+---------------+-------------------+
| f1       |  3            | GL_RGB        | GL_RGB8           |
+----------+---------------+---------------+-------------------+
| f1       |  4            | GL_RGBA       | GL_RGBA8          |
+----------+---------------+---------------+-------------------+

``f2`` textures stores 16 bit float values (``GL_HALF_FLOAT```).

+----------+---------------+---------------+-------------------+
| **dtype**|  *Components* | *Base Format* | *Internal Format* |
+==========+===============+===============+===================+
| f2       |  1            | GL_RED        | GL_R16F           |
+----------+---------------+---------------+-------------------+
| f2       |  2            | GL_RG         | GL_RG16F          |
+----------+---------------+---------------+-------------------+
| f2       |  3            | GL_RGB        | GL_RGB16F         |
+----------+---------------+---------------+-------------------+
| f2       |  4            | GL_RGBA       | GL_RGBA16F        |
+----------+---------------+---------------+-------------------+

``f4`` textures store 32 bit float values. (``GL_FLOAT``)
Note that some drivers do not like 3 components because of alignment.

+----------+---------------+---------------+-------------------+
| **dtype**|  *Components* | *Base Format* | *Internal Format* |
+==========+===============+===============+===================+
| f4       |  1            | GL_RED        | GL_R32F           |
+----------+---------------+---------------+-------------------+
| f4       |  2            | GL_RG         | GL_RG32F          |
+----------+---------------+---------------+-------------------+
| f4       |  3            | GL_RGB        | GL_RGB32F         |
+----------+---------------+---------------+-------------------+
| f4       |  4            | GL_RGBA       | GL_RGBA32F        |
+----------+---------------+---------------+-------------------+

Integer Textures
----------------

Integer textures come in a signed and unsigned version. The advantage
with integer textures is that shader can read the raw integer values
from them using for example ``usampler2D`` (unsigned) or ``isampler2D``
(signed).

Unsigned
~~~~~~~~

``u1`` textures store unsigned byte values (``GL_UNSIGNED_BYTE``).

+----------+---------------+-----------------+-------------------+
| **dtype**|  *Components* | *Base Format*   | *Internal Format* |
+==========+===============+=================+===================+
| u1       |  1            | GL_RED_INTEGER  | GL_R8UI           |
+----------+---------------+-----------------+-------------------+
| u1       |  2            | GL_RG_INTEGER   | GL_RG8UI          |
+----------+---------------+-----------------+-------------------+
| u1       |  3            | GL_RGB_INTEGER  | GL_RGB8UI         |
+----------+---------------+-----------------+-------------------+
| u1       |  4            | GL_RGBA_INTEGER | GL_RGBA8UI        |
+----------+---------------+-----------------+-------------------+

``u2`` textures store 16 bit unsigned integers (``GL_UNSIGNED_SHORT``).

+----------+---------------+-----------------+-------------------+
| **dtype**|  *Components* | *Base Format*   | *Internal Format* |
+==========+===============+=================+===================+
| u2       |  1            | GL_RED_INTEGER  | GL_R16UI          |
+----------+---------------+-----------------+-------------------+
| u2       |  2            | GL_RG_INTEGER   | GL_RG16UI         |
+----------+---------------+-----------------+-------------------+
| u2       |  3            | GL_RGB_INTEGER  | GL_RGB16UI        |
+----------+---------------+-----------------+-------------------+
| u2       |  4            | GL_RGBA_INTEGER | GL_RGBA16UI       |
+----------+---------------+-----------------+-------------------+

``u4`` textures store 32 bit unsigned integers (``GL_UNSIGNED_INT``)

+----------+---------------+-----------------+-------------------+
| **dtype**|  *Components* | *Base Format*   | *Internal Format* |
+==========+===============+=================+===================+
| u4       |  1            | GL_RED_INTEGER  | GL_R32UI          |
+----------+---------------+-----------------+-------------------+
| u4       |  2            | GL_RG_INTEGER   | GL_RG32UI         |
+----------+---------------+-----------------+-------------------+
| u4       |  3            | GL_RGB_INTEGER  | GL_RGB32UI        |
+----------+---------------+-----------------+-------------------+
| u4       |  4            | GL_RGBA_INTEGER | GL_RGBA32UI       |
+----------+---------------+-----------------+-------------------+

Signed
~~~~~~

``i1`` textures store signed byte values (``GL_BYTE``).

+----------+---------------+-----------------+-------------------+
| **dtype**|  *Components* | *Base Format*   | *Internal Format* |
+==========+===============+=================+===================+
| i1       |  1            | GL_RED_INTEGER  | GL_R8I            |
+----------+---------------+-----------------+-------------------+
| i1       |  2            | GL_RG_INTEGER   | GL_RG8I           |
+----------+---------------+-----------------+-------------------+
| i1       |  3            | GL_RGB_INTEGER  | GL_RGB8I          |
+----------+---------------+-----------------+-------------------+
| i1       |  4            | GL_RGBA_INTEGER | GL_RGBA8I         |
+----------+---------------+-----------------+-------------------+

``i2`` textures store 16 bit integers (``GL_SHORT``).

+----------+---------------+-----------------+-------------------+
| **dtype**|  *Components* | *Base Format*   | *Internal Format* |
+==========+===============+=================+===================+
| i2       |  1            | GL_RED_INTEGER  | GL_R16I           |
+----------+---------------+-----------------+-------------------+
| i2       |  2            | GL_RG_INTEGER   | GL_RG16I          |
+----------+---------------+-----------------+-------------------+
| i2       |  3            | GL_RGB_INTEGER  | GL_RGB16I         |
+----------+---------------+-----------------+-------------------+
| i2       |  4            | GL_RGBA_INTEGER | GL_RGBA16I        |
+----------+---------------+-----------------+-------------------+

``i4`` textures store 32 bit integers (``GL_INT``)

+----------+---------------+-----------------+-------------------+
| **dtype**|  *Components* | *Base Format*   | *Internal Format* |
+==========+===============+=================+===================+
| i4       |  1            | GL_RED_INTEGER  | GL_R32I           |
+----------+---------------+-----------------+-------------------+
| i4       |  2            | GL_RG_INTEGER   | GL_RG32I          |
+----------+---------------+-----------------+-------------------+
| i4       |  3            | GL_RGB_INTEGER  | GL_RGB32I         |
+----------+---------------+-----------------+-------------------+
| i4       |  4            | GL_RGBA_INTEGER | GL_RGBA32I        |
+----------+---------------+-----------------+-------------------+

Overriding internalformat
-------------------------

:py:meth:`Context.texture` supports overriding the internalformat
of the texture. This is only necessary when needing a different
internalformats from the tables above. This can for
example be ``GL_SRGB8 = 0x8C41`` or some compressed format.
You may also need to look up in :py:attr:`Context.extensions`
to ensure the context supports internalformat you are using.
We do not provide the enum values for these alternative internalformats.
They can be looked up in the registry : https://raw.githubusercontent.com/KhronosGroup/OpenGL-Registry/master/xml/gl.xml

Example::

    texture = ctx.texture(image.size, 3, data=srbg_data, internal_format=GL_SRGB8)
