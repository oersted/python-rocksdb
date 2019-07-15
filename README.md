pyrocksdb
=========

Python bindings for RocksDB.

This project is under development, and more features are coming soon.

For any other usage, please follow https://twmht.github.io/pybind11-rocksdb/index.html 

Quick Install
-------------

Quick install for debian/ubuntu like linux distributions.


```
git clone https://github.com/twmht/pybind11-rocksdb.git --recursive -b pybind11
cd pybind11-rocksdb
python setup.py install
```

Quick Usage Guide
-----------------

```python
import pyrocksdb
db = pyrocksdb.DB()
opts = pyrocksdb.Options()
# for multi-thread
opts.IncreaseParallelism()
opts.OptimizeLevelStyleCompaction()
opts.create_if_missing = True
s = db.open(opts, '/path/to/db')
assert(s.ok())
# put
opts = pyrocksdb.WriteOptions()
s = db.put(opts, b"key1", b"value1")
assert (s.ok())
# get
opts = pyrocksdb.ReadOptions()
blob = db.get(opts, b"key1")
print (blob.data) # b"value1"
print (blob.status.ok()) # true
#delete
opts = pyrocksdb.WriteOptions()
s = db.delete(opts, b"key1")
assert(s.ok())
db.close()
```
