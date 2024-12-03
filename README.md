# esmf-test-data
Grids and data files used for ESMF regression testing

Note that this was set up to use git lfs, but we have changed the files currently in use in the ESMPy testing to be stored directly rather than managed by git lfs. (This can be accomplished by temporarily uninstalling git lfs on your machine before committing a file.) This is needed so that a 'make download' from ESMPy works in the presence of these diffs:

```diff
diff --git a/src/addon/esmpy/src/esmpy/util/cache_data.py b/src/addon/esmpy/src/esmpy/util/cache_data.py
index e2bc0f0395..da852e79b3 100644
--- a/src/addon/esmpy/src/esmpy/util/cache_data.py
+++ b/src/addon/esmpy/src/esmpy/util/cache_data.py
@@ -10,8 +10,8 @@ def _data_dir():
         return os.path.join(site.getsitepackages()[0], "esmpy/data")
 
 DATA_DIR = _data_dir()
-DATA_URL = 'http://data.earthsystemmodeling.org/download/data/'
-# DATA_URL = 'https://raw.github.com/esmf-org/esmf-test-data/main/grids/'
+# DATA_URL = 'http://data.earthsystemmodeling.org/download/data/'
+DATA_URL = 'https://raw.github.com/esmf-org/esmf-test-data/main/grids/'
 
 def do_download():
     """
```

(Otherwise, 'make download' just gets the pointer to the file rather than the actual file stored via git lfs.)