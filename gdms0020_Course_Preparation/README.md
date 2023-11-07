# Course Preparation

We will use the following free and open sources software packages:

Software we will be using during the course:

1. QGIS Geographical Information System: http://qgis.org/en/site/
1. PostgreSQL Database Management System: https://www.postgresql.org/
1. PostGIS Spatial Database Extension for PostgreSQL: http://postgis.net/  
1. Anaconda Python distribution: https://www.anaconda.com/
1. notepad++ Text Editor (for Windows users only): https://notepad-plus-plus.org/
1. FileZilla Free FTP, FTP over TLS, ans SFTP client: https://filezilla-project.org/
1. WinSCP Free FTP, SFTP, SCP client for Windows: https://winscp.net/

We will use several special Python packages to process geodata and to interact with geodatabases. The following list is not comprehensive:

* pandas
* geopandas
* shapely
* fiona
* pyproj
* rasterio
* sqlalchemy 
* psycopg2
* ftplib
* ipython-sql # SQL magic function

```
Hello
```

## git 

We use git to provide the course material. You should familiarize yourself with git. A short introduction on how to use git is given [here](git.md).

## Conda Environments  

In Python software development often the concept of _environments_ is used. Environments are  fully separated Python installations. An environment consists of a combination of Python packages with specific version numbers including the Python interpreter itself. Separate environment variables and configuration files can also be provided. In fact the separated environments are individual independent directory sub-trees on the file system. The developer can activate an environment and work with the particular software versions installed in the environment. 

The Anaconda Python distribution provides its own envrironment management and software installation system. The name of the command line interface (the command to be called on a terminal window prompt) is `conda`.

**Create a new Anaconda environment. Do NOT install the packages in the base environment!**

**Go to [Set up your conda environment](gdal_conda_env.md)**

For more information see [conda-cheatsheet.pdf](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf)

