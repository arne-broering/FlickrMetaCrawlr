FlickrMetaCrawlr
================
The Flickr Crawler  is able to programmatically download metadata of Flickr photos and users. It relies on the open Flickr API  and fetches metadata of Flickr photographs for a specified set of tags.
The Flickr API restricts applications to access a maximum of 5,000 photos in a single API query execution, however, a certain tag combination may result in a much larger number of photos - e.g., searching for Times Square and New York results in around 15,000 geotagged photos. Therefore, we implement a mechanism that divide the initial query into sub-queries which result in less than 5,000 photos. We utilize a quadtree algorithm (Samet, 1984) for this purpose. The quadtree is applied to the geographic space and subdivides it recursively into four quadrants starting with the maximum extent (the bounding box of between 180°W, 90°S and 180°E, 90°N). A division into four quadrants is performed in case more than 5,000 photos are contained within a bounding box. Finally, for all defined quadrants (each containing less than 5,000 photos) separate API queries can be executed and the relevant metadata is downloaded.
