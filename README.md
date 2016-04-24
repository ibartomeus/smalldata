# smalldata (ITD: individual trait database?)
*Package documenting the creation of a small data package, initially on bee traits*

This is a guide to create a package to host, manage and deliver small dynamic data to the world. Tinny datasets, often static, containing scientific data can be hosted in several places (e.g. dryad, figshare). Similarly, big projects generating big data have the power to create customized data portals (e.g. gbif). But there is a lot of medium sized data that its well curated, dynamic, but that usually lives in a local computer because is not technically easy and/or cheap to put in the public domain. This is an attempt to liberate such data in a programatic way and use it as a guide or template for others to do the same.

Why small data? Becasue I need a ligth protable and simple data structure: _csv_. This has several advantadges, but the drawback is that data can't be really large (e.g. no more than ~50 MB to work smoothly with git and R).

The example data will be about bee traits, but is designed so it can be easily extended to other organisms. Actually there is no comprensive database of bee traits, but information is scatered in diverse publications and private databases. However, most importantly none of this data to my knowledge capture the variability in traits, but only mean values for especies. 

There are 5 datasets for each group.

- Schema: This can be created for any group, and defines the traits and units that can be used. For now, there is only one schema, the one for bees (and maybe other pollintors). It's done in a way adding traits is easy and don't break the schema.
- Species taxonomy: This is autogenerated via `taxize` and should not be edited by hand.
- Specimen level data: Morpfological, ecological, life history or physiological data measured on individuals from which to calculate mean and variance (if desired). 
- Observations data: Some traits are inferred from observational data (e.g. flower specialization, range). 
- Species level datase: This contain mean values for especies (extracted from specimen and observations data) as well as its taxonomy. This file is autogenerated.

# Process

1) Where to host the data: git or dat

Initially I will build 'smalldata' using git and Github as the data server. The advantages is that is well stablished and tools are build around it to streamline the process in a cost effective way. The drawback is that is not ideal for tracking changes on data. dat would be a preferred option, but is in early development stage and principally lacks of an easy-to-use free server to host the project. However, migrating the datasets to dat is planned in a second stage of the project.

Raw data will be stored in /data folder in csv. Probably autogenerated data will be saved in .RData if this speed up the project loading.

2) Automate a local check on the data (e.g. using taxize)

I decide only fully identified species will be allowed. Internal checks should check for taxonomy, variable categories, units and ranges, and provide warnings. Internal chacks should be a function that can be called from the package.

3) Create a R package to interact with the data.
    - download raw data: load() and read.table shuld suffice
    - use predefined functions (e.g. process data) on the data and update processed data.
    - upload data. This can be done by automating the fork, add & pull request from a single function.
    - get the correct citation for the used data. (including how acknowledgments should look like)

4) Issues with speed. Partition large files & automate pre-processed data.

Ideas: Large files can be partitioned geographically and downloaded only if needed. 
Pre-procesed data (e.g. mean values) can be saved in Rdata file and updated monthly(?). An update function should be available.

5) Define the metadata 

Package EML will be used: https://github.com/ropensci/EML

6) Ensure long term permanent repository of the data in different realeases & Doi's. A data paper paper with all data contributors as co-authors may be a good idea.

7) Do a shinny app to visualize the data, specially data coverage (maps).

# what next?

If you want to be the curator of another taxon, contact me and we can develop the schema for e.g. aphids, birds, spiders, etc... and I belive the infrastructure should work the same.




