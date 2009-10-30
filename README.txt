Introduction
============

raptus.mercurialstorage depends on Products.ExternalStorage 0.7 which has some flaws and
needs to be patched in order to work correctly. The patch may be applied by using the
following snipped in your buildout:

[patch_es_storage]
recipe = iw.recipe.cmd:py
on_install = true
on_update = true
cmds =
    >>> import os
    >>> patch = os.path.join("""${buildout:directory}""".strip(), 'eggs/raptus.mercurialstorage-0.1-py2.4.egg/raptus/mercurialstorage', 'es.patch')
    >>> file = os.path.join("""${buildout:directory}""".strip(), 'eggs/Products.ExternalStorage-0.7-py2.4.egg/Products/ExternalStorage/ExternalStorage.py')
    >>> if os.path.exists(file):
    >>>     os.system('patch -N %s %s' % (file, patch))


