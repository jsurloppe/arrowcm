# arrowcm
Arrowcm is a Jupyter Content Manager that lets you use any pyarrow-supported filesystem as a Content Manager.

Arrowcm has been tested with JupyterLab 4, but it might also work with previous versions.

As Arrowcm relies on pyarrow, any pyarrow-supported filesystem should be available, and fsspec filesystems should work too.

It is based on the new jupyter-server content manager interface and will not work with the old notebook content manager interface.
