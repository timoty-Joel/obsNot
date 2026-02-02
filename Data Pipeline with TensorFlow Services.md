## Data Pipeline using TensorFlow
- Data pipeline is a method in which raw data is ingested from various data sources, transformed and then ported to a data store. 
- Data pipeline works on the principle ETL that stands for Extract, Transform and Load. 
- In TensorFlow Data Services 
	Extracting doesn't mean we extract the data only from simple sources but also from large composed of multiple shards distributed dataset in cloud storage
	In transform, we do the extracting feature performing augmentation process on your data. 
	Load means that we load the transformed data into the appropriate device
- In nutshell, below is an illustration in using TensorFlow services in data pipeline ![[Bangkit Notes/DataPipeline/W1_1.PNG]] - `tfds.load()` means load a dataset from the tensorflow data storage. In this code, we also can customize what kind of split that we want
- - `dataset.shuffle()` in for shuffle our data based on buffer size
- - `dataset.batch()` in the code is for batch mapping our data based on batch_size we set
- We can see the list of dataset in TFDS using `tfds.list_builders()`
	![[Bangkit Notes/DataPipeline/W1_2.PNG]]
- We also can view the metadata for the dataset using DatasetInfo
	![[Bangkit Notes/DataPipeline/W1_3.PNG]]
	
	DatasetInfo contains several properties from Name to the citation of the dataset
	![[Bangkit Notes/DataPipeline/W1_4.PNG]]
	We can see in features in dataset that consists of image and labels.
- In using TFDS, we can use versioning on the dataset we use, so basically we just load another version of the dataset. ![[W1_5.PNG]]
	Major version: The data could be changed 
	Minor version: Signifies that there's no change in the existing data, but it does imply that some additional features have been added
	Patch version: If the patch version has increased, the serialization of disk may have changed
