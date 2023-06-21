# Hotspot Analysis Plugin for QGIS

**THIS PLUGIN VERSION IS BASED ON PYSAL >= 2.0** ([previous version here])

A QGIS Plugin to perform Hotspot analysis based on the Python Spatial Analysis Library - [PySAL]. 
The Hotspot analysis plugin associates the **Z-scores** and **p-values** (under Complete Spatial Randomness hypothesis) of the Gi* local statistic ([Getis and Ord, 1992]; [Getis and Ord, 1996]), Anselin Local Moran's I ([Anselin, 1995]) and Local Moran Bivariate ([Wartenberg, 1985]; [Anselin et al., 2002]) for each feature of a shapefile, with an assigned **projected coordinate system** and (at least) an associated **numerical attribute**. Output layer allows to indentify spatial hot spots/cold spots) as well as clusters/outliers for the input vector spatial dataset. 

For what it concerns Gi* local statistic, positive and statistically significant Z-score indicates a cluster of high values (hotspot). Negative and statistically significant Z-score indicates a cluster of low values (coldspot). 
With respect to the Local Moran's I (and its bivariate counterpart, the Local Moran Bivariate), Z-scores are translated into quadrant values (q) which depict the presence of clusters or outliers within the dataset. Significance is computed, based on user's choice, against normality assumption or using random permutations. 
Please consider the aforementioned litterature references for detailed information.

Spatial relationship between point features is modeled using a Fixed Distance Band (expressed with the same unit of measure of the projected coordinate system of the input point shapefile) or optionally using the  K-nearest neighbours approach. For polygon shapefile analysis, the spatial relation is modelled using a 1st order queen's case contiguity matrix. For more information, please refer to [Geospatial Analysis - 5th Edition, 2015 - de Smith, Goodchild, Longley]

___
### Installation - Windows

**1)** Install dependencies:

If you are using **QGIS 3.18** or lower:

Open `OSGeo4W Shell` installed with QGIS as `Administrator` and type:
```sh
 $ py3_env
 $ python -m pip install --upgrade pip
 $ python -m pip install pysal==2.1.0
```

If you are using **QGIS >= 3.20**:

Open `OSGeo4W Shell` installed with QGIS as `Administrator` and type:
```sh
 $ o4w_env
 $ python3 -m pip install --upgrade pip
 $ python3 -m pip install pysal==2.1.0 -U --user
```

* A **video tutorial** for installation on Windows is available [here]

**2)** Open QGIS:

Go to `Plugins` -> `Manage and Install plugins` -> `Settings` -> `Show also experimental plugins` 

In `All plugins` tab, look for `Hotspot Analysis` and tick the checkbox.  
A new icon for Hotspot Analysis will appear on the QGIS main panel and in the Vector Menu.

**3)** If you are interested in the **latest unreleased version**:

Download the zip folder of the repository at:
https://github.com/danioxoli/HotSpotAnalysis_Plugin/archive/refs/heads/qgis3pysal2.zip

Open QGIS 3 and go to `Plugins` -> `Install from ZIP`

Select the downloaded zip folder and press `Install plugin`. The icon for the Hotspot Analysis plugin will appear in the list of the installed plugins. Tick the Checkbox to activate it. The plugin will appear in the Vector menu.

**Note**: In case of errors rising from the Scipy package, open `OSGeo4W Shell` installed with QGIS3 as `Administrator` and type:
```sh
 $ py3_env
 $ python -m pip install scipy -U
```

<!---
**4)** PySAL common error on Windows

Please, look at: https://github.com/danioxoli/HotSpotAnalysis_Plugin/issues/15
--->
___


### Installation - Ubuntu

**1)** Install dependencies:

Open a **Terminal** and type the command:

```sh
 $ apt-get install python3-pip
```
Open the **`QGIS Python Console`** and type the commands:

```sh
 $ import pip
 $ pip.main(['install', 'pysal==2.1.0'])
```

**2)** Open QGIS 3:

Go to `Plugins` -> `Manage and Install plugins` -> `Settings` -> `Show also experimental plugins` 

In `All plugins` tab, look for `Hotspot Analysis` and tick the Checkbox.  
A new icon for Hotspot Analysis will appear on the QGIS main panel and in the Vector Menu.

**3)** If you are interested in the **latest unreleased version**:

Open a **Terminal** and change directory to QGIS Plugins directory, default is: 

```sh
 $ cd /usr/share/qgis/python/plugins 
``` 
**Clone** the `GitHub` repository into the earlier mentioned path:

```sh
 $  sudo git clone -b qgis3pysal2 https://github.com/danioxoli/HotSpotAnalysis_Plugin
```

***Alternatively***

Download the zip folder of the repository at:
https://github.com/danioxoli/HotSpotAnalysis_Plugin/archive/refs/heads/qgis3pysal2.zip

Open QGIS 3 and go to `Plugins` -> `Install from ZIP`

Select the downloaded zip folder and press `Install plugin`. The icon for the Hotspot Analysis plugin will appear in the list of the installed plugins. Tick the Checkbox to activate it. The plugin will appear in the Vector menu.

___
### Installation - macOS

**1)** PySAL 2 may be included in the core libraries of the current LTR QGIS version, otherwise install the package `pysal==2.0.0` using `pip3`  following these instructions: https://www.lutraconsulting.co.uk/blog/2020/10/01/qgis-macos-package

**Note**: If dependencies errors show up, check this workaround: https://github.com/danioxoli/HotSpotAnalysis_Plugin/issues/61

**2)** Open QGIS 3:

Go to `Plugins` -> `Manage and Install plugins` -> `Settings` -> `Show also experimental plugins` 

In `All plugins` tab, look for `Hotspot Analysis` and tick the Checkbox.  
A new icon for Hotspot Analysis will appear on the QGIS main panel and in the Vector Menu.

**3)** If you are interested in the **latest unreleased version**:

Download the zip of the repository folder:
https://github.com/danioxoli/HotSpotAnalysis_Plugin/archive/refs/heads/qgis3pysal2.zip

https://github.com/danioxoli/HotSpotAnalysis_Plugin/issues/61

Go to `Plugins` -> `Install from ZIP`

Select the downloaded zip folder and press `Install plugin`. The icon for the Hotspot Analysis plugin will appear in the list of the installed plugins. Tick the Checkbox to activate it. The plugin will appear in the Vector menu.

___

### Additional Material 

An user guide with demo exercises is included here: https://github.com/danioxoli/HotSpotAnalysis_Plugin/blob/master/test_data/Hotspot_Analysis_UserGuide.pdf

Plese cite this as: 

_Oxoli, D., Prestifilippo, G., Bertocchi, D., Zurbaràn, M. (2017). Enabling spatial autocorrelation mapping  in QGIS: The Hotspot Analysis Plugin. GEAM. GEOINGEGNERIA AMBIENTALE E MINERARIA, 151(2), 45-50._

Latest presentation available here: http://www.slideshare.net/danieleoxoli/hotspot-analysis-with-qgis-foss4git-2017

**Note**: part of this material might be based on the **old version of the plugin**! 

___

### Changeset

##### Changeset 04/2021
- Bug import fix for LTR 3.16
- Fix of PySAL functions import paths

##### Changeset 02/2020
- Port to PySAL 2

##### Changeset 10/2018
- Enhancement to Gi* computation with negative values
- Icon fixed

##### Changeset 03/2018
- Plugin translation to QGIS 3 

##### Changeset 06/2017
- Enabled the use of k-nearest neighbor spatial weights matrix for point shapefiles
- Minor bugs fixed

##### Changeset 03/2017
- Enabled Anselin Local Moran's I and Bivariate Local Moran computation
- Minor bugs fixed

##### Changeset 02/2017
- The plugin has been **officially published** on the QGIS plugin repository
- Minor bugs fixed

##### Changeset 01/2017
- Enabled the use of negative numerical attributes [Getis and Ord, 1996] 
- Enabled polygon shapefiles as input using queen's case contiguity spatial weight matrix. 
- Enabled the possibility of selecting between normality assumption (default) and standard normal approximation from permutations to compute Gi* Z-scores and associated p-values. 

##### Changeset 12/2016
New check botton to eneable the usage of **row standardized** spatial weights

##### Changeset 11/2016
With this new version, the output layer is displayed with an **automatic style** which enables hotspot and coldspot visualization. Moreover, a **default Fixed Distance Band** is dispalyed. This latter represents the minimum distance to ensure 
at least 1 neighbor to any element of the dataset in order to compute spatial weights for Gi* 

##### Changeset 10/2016
The current version does not require Pyshp as well as to specify the feature coordinates as two separate fields in the attribute table of the input shapefile. Only the numerical attribute must be included and selected using the graphical interface on QGIS. Nevertheless, be sure that your input shapefile is projected. The unit of measure in which you express the analysis distance must agree with the one of the projected coordinate system of your input layer. 

___
### Future work

 - Test on the new functionalities addedd
 - improve GUI appereance
 - Update User guide and documentation for Anselin Local Moran's I and Bivariate Local Moran computation
 
___

Bug tracker and Wiki

##### License

_The Hotspot Analysis plugin is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation_

Copyright © 2021 Daniele Oxoli - [Politecnico Di Milano] | Gabriele Prestifilippo - [GISdevio]

E-mail: daniele.oxoli@polimi.it

 [GISdevio]: <https://gisdev.io/en?lang=en>
 [Politecnico Di Milano]: <https://www.polimi.it/>
 [PySAL]: <https://pysal.org/>
 [Getis and Ord, 1992]: <http://onlinelibrary.wiley.com/doi/10.1111/j.1538-4632.1992.tb00261.x/full>
 [Geospatial Analysis - 5th Edition, 2015 - de Smith, Goodchild, Longley]: <http://www.spatialanalysisonline.com/HTML/index.html?local_indicators_of_spatial_as.htm>
 [OSGeo4W Shell]:<http://trac.osgeo.org/osgeo4w/>
 [OSGeo-Live]:<https://live.osgeo.org>
 [Getis and Ord, 1996]: <http://onlinelibrary.wiley.com/doi/10.1111/j.1538-4632.1995.tb00912.x/pdf>
 [Anselin, 1995]: <http://onlinelibrary.wiley.com/store/10.1111/j.1538-4632.1995.tb00338.x/asset/j.1538-4632.1995.tb00338.x.pdf;jsessionid=A8B95BCA3E3DAFED243732CC66B31B63.f02t01?v=1&t=j0hvb8t7&s=c3f30861dca953c035e5b1dbbc24ea6b659a82c5>
 [Wartenberg, 1985]:<http://onlinelibrary.wiley.com/store/10.1111/j.1538-4632.1985.tb00849.x/asset/j.1538-4632.1985.tb00849.x.pdf?v=1&t=j0uyit1b&s=7ad70b665f08164ec74068d58eedf6f65e072dfa>
 [Anselin et al., 2002]:<https://pdfs.semanticscholar.org/4e34/bd70317377971ba8df7259288b972ad6a239.pdf>
 [previous version here]:<https://github.com/danioxoli/HotSpotAnalysis_Plugin/tree/qgis3>
 [here]:<https://www.youtube.com/watch?v=lnDkbdKKJXM&ab_channel=AMDGS>
