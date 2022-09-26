
conda activate geo # or another environment you want to use.

conda install -c conda-forge sqlalchemy psycopg2 pgspecial ipython-sql jupyterlab geopandas


# In case the python projection library used by GDAL does not find the correct projection parameter database you can set it manually.
# Open the Anaconda prompt and activate the environment you want to use (in my case `geo`).

# list operating system (Windows) environment variables 
Get-ChildItem -Path Env:\

# Search for the environment variable PROJ_LIB
# PROJ_LIB -> C:\OSGeo4W64\share\proj (wrong!)
echo $env:proj_lib


# set the new location of the proj folder (replace <ME> and <ENV> with your username and conda environment, resp.):
#$env:PROJ_LIB="C:\Users\<ME>\Anaconda3\envs\<ENV>\Library\share\proj"
# OR

$env:PROJ_LIB=$env:conda_prefix+"\Library\share\proj"

# Check again:
echo $env:proj_lib

