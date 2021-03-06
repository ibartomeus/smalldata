# BUGS:

# Important (in order of importance for me, more or less):
[] make ORCID not compulsory when uploading a contributor. Warn contributor not updated if some compulsory fields are missing.  
[] When downloading data, locationDescription are merged and description not displayed (e.g. download data from Bombus terrestris)  
[] When data is downloaded from simple search, it lists all contributors of the table per row (i.e. per observation). Each observation should have only it's contributors, as it happens in advanced search.  
[] Advanced search. Country and contributor Search not working properly.  
[] Something goes wrong with calculating means: https://traitbase.info/species?q=5b0414a32265c5000fab55cb Hofmann dataset has the only measurement of m_body_size (6 mm length), so SE cannot be calculated, and the mean should not be NA?  
[] Map as displayed in simple exploration: NZ is not shown  
[?] Metadata from advanced search not working as expected e.g. https://traitbase.info/metadata?key=species&value=Bombus%20terrestris 
from simple search it works: https://traitbase.info/metadata?speciesId=5b04145b2265c5000fab2abf  

# Enhancements  
[] Users to be able to modify their own pws (maybe via github connection)  
[] Add a measurement source field for Observation (2 factors: literature, own_measurement). So each variable will have m_, n_, se_ and scr_ (source)  
[] Add photo field to the traits table accepting an URL. This is in case you want to add a photo on how to measure the trait.  

# less important  
[] Import csv (web) only works for ~2000 lines. e.g. table species.  
[] Export as csv (web) do not work in e.g. table Schema.  
[] Search from /app / observations do not search in the species field, making it not very useful
[] Some datasets behave wierd and do not import. e.g. Kremen. (DO NOT WORRY FOR NOW, I'll do more tests)  

# Very Minor or enhancements
[] `UrlPhoto` In table species: this field can be depreciated.  
[] Typo: in https://traitbase.info/app#/import/specie The text should read "import Species", not "Specie" NOT IMPORTANT.  
[] in /app/dataset observations can be paginated (not important)  
[] Add option to deactivate ITIS automatic check. For > 200 species it fails as ITIS is problematic. So far I succeed always!  
[X] Not let ITIS guess? NOW Validate sp do warns you, How this works exactly? Pedro: Warning means it loads the species. Nacho: Check this.  
[] Return original and uploaded species always (when downloading or visualazing data. That way is easy to catch any ITIS misinterpretation)  
[] importDataset warns "'contributor_ORCID' is not recognized and it will be ignored." BUT IT WORKS WELL and imports ORCID correctly.  
[] When n_ and se_ are missing they should be interpreted as 1 and 0 respectivelly. Make this by default.  
[] Accept observations without m_? (think about it, as for some species we know latitude and longitude only, and this is already something)  
[] Check what does latitude when not numeric... I think it tries to guess it. Nacho need to check.  
[] Countries can be mapped in the future.  
[] How it work the search criteria in /app? If I type a country, it returns nothing. It looks like only certain fileds are searched.  

# Package
[X] make nacho contributor of the R package. - Done.  
[] Would be cool to have a Delete dataset (and its observations) function. THIS IS IMPORTANT. 

# Web
[] Move search box to upper bar.   
[] When Date search has day/month blank, it ignores year. Not important.  
[] Metadata can be downloaded along with data (maybe simply add a download button)  
[I] We say: "Use our API to connect directly with you preferred programming tool. See details on the API implementation here." Can we refer people to the API? which is the link? I found this: "API REST published over /api on port 5000. Swagger documentation for /api available on /api/documentation" Is this information enough?  
[X] How do I edit the webpage. Pedro: On git and then Pedro will deploy it.  
[X] Can users modify their pasword? Pedro: Not yet.  


# Solved
[X] importDataset is not importing observations with old dates. FIXED!  
[X] importDataset is not importing the contributors!  - YES, but only with ORCID.  
[X] validateDataset time out in Osorio Canadas or Bartomeus (large list of species) -> now, up to 200 checks (but see below). Works well so far.  
[X] long shifted to the left (e.g. Bombus terrestris) - checked against Google maps. All EU represented.  
[X] Removing datasets do not remove its observations.  

