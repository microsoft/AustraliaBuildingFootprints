## Introduction
Bing Maps is releasing country wide open building footprints datasets in Australia. This dataset contains 11,334,866 computer generated building footprints. The data is freely available for download and use under applicable license.

![](/images/example.jpg)

## License
This data is licensed by Microsoft under the [Open Data Commons Open Database License (ODbL)](https://opendatacommons.org/licenses/odbl/).

## FAQ
### What does the data include?
11,334,866‬ building footprint polygon geometries in Australia in GeoJSON format. You may download the data in GeoJSON format here:

| Country       | Number of Buildings  | Zipped MB | Unzipped MB |
| ------------- |:-------------:|:-----:|:-----:|
| [Australia](https://usbuildingdata.blob.core.windows.net/australia-buildings/Australia_2020-06-21.geojson.zip)|11,334,866‬|845|6,410|

### What is the GeoJSON format?
GeoJSON is a format for encoding a variety of geographic data structures. 
For intensive documentation and tutorials, refer to [GeoJson blog](http://geojson.org/).

### Why is the data being released?
Microsoft has a continued interest in supporting a thriving OpenStreetMap ecosystem.

### Should we import the data into OpenStreetMap?
Maybe. Never overwrite the hard work of other contributors or blindly import data into OSM without first checking the local quality. While our metrics show that this data meets or exceeds the quality of hand-drawn building footprints, the data does vary in quality from place to place, between rural and urban, mountains and plains, and so on. Inspect quality locally and discuss an import plan with the community. Always follow the [OSM import community guidelines](https://wiki.openstreetmap.org/wiki/Import/Guidelines).

### Will the data be used or made available in larger OpenStreetMap ecosystem?
Yes. Currently Microsoft Open Buildings dataset is used in ml-enabler for task creation. You can try it out at [AI assisted Tasking Manager](https://tasks-assisted.hotosm.org/). Facebook has also integrated the dataset into experimental version of RapiD editor. Try out this experimental version here [RapiD](https://mapwith.ai/rapid-sotm2019).

### What is the creation process for this data?
The building extraction is done in two stages:
1.	Semantic Segmentation – Recognizing building pixels on the aerial image using DNNs
2.	Polygonization – Converting building pixel blobs into polygons

#### Stage1: Semantic Segmentation
![](/images/segmentation.jpg)

#### Stage 2: Polygonization
![](/images/polygonization.jpg)

### Evaluation set metrics
Australia evaluation set contains 6,785 buildings from several diverse and represenative regions.

Building match metrics on the evaluation set:

| Metric | Value |
| --- | :---: |
| Precision | 98.59% |
| Recall | 64.95% |

We track following metrics to measure the quality of matched buildings in the evaluation set:
1. Intersection over Union – This is a standard metric measuring the overlap quality against the labels
2. Shape distance – With this metric we measure the polygon outline similarity
3. Dominant angle rotation error – This measures the polygon rotation deviation

IoU is 0.79, Shape distance is 0.44, Average rotation error is 4.46 degrees

![](/images/bldgmetrics.JPG)

### False positive ratio in the corpus

We estimate 1% false postive ratio in 1000 randomly sampled buildings from the entire output corpus.

### Evaluation recall error space

| Error category | 35.05% Gap |
| --- | :---: |
| Very small buildings | 15.4% |
| Connected buildings | 14.0% |
| DNN | 2.8% |
| Various | 2.1% |
| Polygonization | 0.7% |

Small building example:  
![](/images/small_building_example.jpg)

Connected buildings example:  
![](/images/connected_buildings_example.JPG)

### What is the vintage of this data?
The vintage of the footprints depends on the vintage of the underlying imagery. Bing Imagery is a composite of multiple sources, therefore it is difficult to know the exact dates for individual pieces of data.

### How good is the data?
Our metrics show that in the vast majority of cases the quality is at least as good as data hand digitized buildings in OpenStreetMap. It is not perfect, particularly in dense urban areas but it provides good recall in rural areas. See below for metrics by area type:  
![](/images/polygonmetrics.JPG)

### What is the coordinate reference system?
EPSG: 4326

### Will there be more data coming for other geographies?
Maybe. This is a work in progress.

<br>

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.microsoft.com.

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Legal Notices

Microsoft, Windows, Microsoft Azure and/or other Microsoft products and services referenced in the documentation
may be either trademarks or registered trademarks of Microsoft in the United States and/or other countries.
The licenses for this project do not grant you rights to use any Microsoft names, logos, or trademarks.
Microsoft's general trademark guidelines can be found [here](http://go.microsoft.com/fwlink/?LinkID=254653).

Privacy information can be found [here](https://privacy.microsoft.com/en-us/)

Microsoft and any contributors reserve all others rights, whether under their respective copyrights, patents,
or trademarks, whether by implication, estoppel or otherwise.
