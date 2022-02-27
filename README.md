# Methods for Historical Map Extraction
--

## Introduction

There are many kinds of historical maps, fire insurance atlases and city atlases, thanks to their meticulously documented details and wide coverage, are valuable sources for research both at micro level and on a large scale. 

While many of these maps have been digitized and georeferenced by librarians and volunteers in recent years, most of them are not yet "machine-readable", which presents a "last-mile" problem to many interesting Historical GIS research. 

This repository is dedicated to the dicussion and curation of methods that turns digital map collection into "analysis-ready" data. 

-- 

## Sanborn Atlases


### Background

What is it for? The publisher? What do the publisher care about? Thus what features are captured in the maps? When & Where - spatial temporal coverage

### Target Features

#### Block Contour
#### Lot Line
#### Building Footprint

#### Street Name
#### Place Name
#### House Number
#### Building Details

### High-level Extraction Approach

Three types of information can help us discern and extract the rich data encoded in the maps: shape, color, and text. 

Shape includes the contours and border lines of the various elements. Contour detection and morphology operation can help us understand the basic layout of a map and put a hierarchical structure to the elements, which faciliates the better extraction in smaller parts of the map. Shapes can also be used to reconstruct spatial relationship between between buildings, lots, and other elements on the map, at a very local level.

Color includes the color of the map's background, foreground, shape border color. Color is used in image preprocessing, which is critical to the success and accuracy of morphology operation. Color also provide basis for image processing operations such as flood-fill, which is important in footprint extraction. In addition, color indicates land use or building material, which in itself is valuable data for research. 

Text includes the various text labels on the map. The content, location, and font style of the text all matters in map extraction process. The text content is clearly valuable data for research, especially when geocoded through its location on map. However, the location of text on a map image also help identify buildings and built structures. The font style of the text labels often convey important information about what types of content they have, be it street name or place name or land owner name. 

An automated and comprehensive map data extraction pipeline will most likely rely all three types of information on a map. And the pipeline will probably need to extract these three types of information in an iterative process i.e. the extraction of one type of information will learn from extracted data in another type, then feed into the extraction of new data in the other type.

Another benefit of working with urban data is the fact that cities are "evolving" cultural artifact that are resistant to drastic changes. We can bring modern day GIS data and data extracted for other years to guide and improve the extraction of historical maps. Thinking in a longitudinal way also help organize the evolving data and make the database more sustainable in the long term.

Coming back to the extraction of a specific map, the current high level approach is to identify the blocks contours first, then find the lot lines, and then extract footprints. In the parallel, harvest the text labels, and consolidate and attach them to the footprints once footprints data are ready. The techniques and types of information to achieve each steps are being experimented to find a best pipeline in terms of accuracy and efficiency.