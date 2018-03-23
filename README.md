Purpose:
----
An attempt to integrate Sirepo/SRW simulations with Bluesky/Ophyd.

Usage:
----
- make sure you have mongodb service running
- create conda environment:
```bash
conda create -n srw_bluesky python=3.6
conda activate
pip install -r requirements.txt
python -c "from ophyd.utils import make_dir_tree; make_dir_tree(2018, base_path='/tmp/data')"
```
- start ipython
- `%run -i re_config.py`
- `%run -i srw_detector.py`
- `RE(bp.grid_scan([srw_det], fs.xwidth, 0, 1e-3, 10, fs.ywidth, 0, 1e-3, 10, True))`
- get the data:
```py
hdr = db[-1]
imgs = list(hdr.data('srw_det_image'))
plt.imshow(imgs[31], aspect='equal')
```
