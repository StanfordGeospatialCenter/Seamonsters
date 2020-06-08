# Seamonsters
 Exploring making training datasets from iiif-served imagery infrastructure
 
 These are my notes on experimenting with iiif content for creating training datasets
 
 
## Initial Exploration

### Label.box  
Allows adding online  images through csv of endpoints, so first step is to produce a csv with iiif endpoints appropriate to the task (sizes, regions, etc...)


Notes:
iiif links were curated by DRMC, based upon features, different sheets for seamonsters, cartouches, etc...

I took the curated sets of iiif manifest from DRMC/Rumsey.com and prepped first by combining into a single table (creating classes in Labelbox means we can have labels made for different classes, simultaneously from one image).

Then, fetching default.jpg links, using OpenRefine:

1. Create column **iiif JSON** at index 5 by fetching URLs based on column **IIIF URL** using expression `grel:value`   
2. Create new column **default image URL** based on column **iiif JSON** by filling 125 rows with `grel:value.parseJson().sequences[0].canvases[0].images[0].resource["@id"]`  

Results:

* size of default.jpg isn't homogenous and depends on the resolution and physical size of original, so some links were too big to serve. 
* Jack suggests grabbing info.json from the manifest to see the available sizes and evaluate their utility.
* Some images, like the Urbano Monte, are so big they will need to be called as more than one image, perhaps in quarters, with some buffer size to account for features on tile edges. [Is this manual and iterative, or can we define some size parameters that work universally?]
* Most images imported without issue, using the default image. 



