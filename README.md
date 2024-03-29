# arrowcm
Arrowcm is a Jupyter Content Manager that lets you use any pyarrow-supported filesystem as a Content Manager.

Arrowcm has been tested with JupyterLab 4, but it might also work with previous versions.

As Arrowcm relies on pyarrow, any pyarrow-supported filesystem should be available, and fsspec filesystems should work too.

It is based on the new jupyter-server content manager interface and will not work with the old notebook content manager interface.


It is available on PyPI:
```
pip install arrowcm
```

After installation, you need to configure the storage that you want to use.

This can be done in your Jupyter config file, where you will need to pass an instance of a PyArrow filesystem as a filesystem property.

```python
from pyarrow import fs

c.ServerApp.contents_manager_class = "arrowcm.ArrowContentsManager"

# S3 example
c.ArrowContentsManager.filesystem = fs.S3FileSystem(
    access_key="myaccesskey",
    secret_key="mysecretkey",
    region=fs.resolve_s3_region("mybucket"),
)
c.ArrowContentsManager.root_dir = "mybucket/notebooks"

# HDFS example
c.ArrowContentsManager.filesystem = fs.HadoopFileSystem("myhdfshost")
c.ArrowContentsManager.root_dir = "/user/jupyter/notebooks"
```

Arrowcm aims to be as compatible as possible with the default file content manager, so most of the options should work.