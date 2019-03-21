# CMIP6 catalogs

### my intake catalog nesting ideas

- The CMIP6 directories are many levels deep and therefore we need some kind of nesting of the catalogs. What I would like to do is to put a config.yaml file in each directory -  which just points to config.yaml files in each of the subdirectories until it gets a level at which I will reference the actual data.  In my case this is where I will read the zarr data, one for each variable pr, tas and huss. 

- With this setup,  `cat = intake.open_catalog('config.yaml')` in any directory will open a parent catalog and `cat.<subdir>` will open a child catalog or the actual data.

- This is all working in my example, but with ~~two~~ one uncomfortable ~~properties~~ property (thanks, @martindurant):

  1. \<tab\> completion will work to get from the parent to child catalog (sub-directory), but then will not get to the grandchild catalog (sub-sub-directory)
  
  ~~2. The path in each YAML file is relative to the `<dir>` in the initial `intake.open_catalog('<dir>/config.yaml')`. This means that if I `intake.open_catalog(config.yaml)` in a subdirectory, the paths are going to need to be relative to this subdirectory, but I have had to hard-wire them to an arbitrary initial parent directory.~~
