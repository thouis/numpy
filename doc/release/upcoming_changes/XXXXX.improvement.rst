``numpy.lib.format.open_memmap`` accepts NumPy integers in ``shape``
-------------------------------------------------------------------
Passing a ``shape`` containing NumPy integer scalars (for example
``np.int64``) or a NumPy boolean for ``fortran_order`` to
`numpy.lib.format.open_memmap` previously wrote entries such as
``np.int64(3)`` into the ``.npy`` header.  Such a file could not be read
back, failing with ``ValueError: malformed node or string``.  These values
are now coerced to plain Python types, so the resulting file is loadable.
