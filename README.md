Simple 2D batch renderer example using PyOpenGL and pygame. See 'pygame-main.py' for details.

The `Batch` class creates two VBOs: one for quad vertices and texture coordinates, and one for indices.

`maxQuads` specifies the maximum number of quads that the VBO can contain. `batch.flush()` is called automatically when the buffer has been filled or explicitly by `batch.end()`.

**Note**: The batch does not support color. A color attribute could easily be added.

Setup:

```python
batch.setup_shaders(vpMatrix = numpy.dot(viewMatrix, projectionMatrix))
renderer = batch.Batch(maxQuads = 10000)
```

Render loop:

```python
...

GL.glClearColor(0, 0, 0, 1)
GL.glClear(GL.GL_COLOR_BUFFER_BIT)

renderer.begin()
renderer.draw(textureRegion, x, y)
renderer.end()

...
```

Cleanup: `gltexture.delete()` and `batch.delete()` will delete a texture and batch VBOs, respectively.

# Dependencies

`batch.py` depends on [PyOpenGL](http://pyopengl.sourceforge.net/) and [NumPy](http://www.numpy.org/). `pygame-main.py` depends on [Pygame](https://www.pygame.org/), but Pygame is not a requirement for using the batch itself.

# License

The code is released under public domain. "animation.png" is copyrighted.
