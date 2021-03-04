# deviceMap
LibreNMS plugin to locate indoor devices

## data.json
The data.json file is an example of a structure for creating an indoor building. The data should be a collection of GeoJSON features (or an array of GeoJSON features). With the standard configuration, each feature must have a "level" property attribute, which can be an integer, a string, or an array of one (or both).

To viemore levels, you will need to specify level 0, level 1, etc ..

it is also possible to insert multiple data.json files and therefore multiple data structures in order to control multiple buildings.

```
{
"type": "FeatureCollection",
    "features": [
        {
            "properties": {   
		"tags": {
                    "buildingpart": "room",
                     ........
                },
                "relations": [
                    {
                        "role": "buildingpart",
            		        "rel": "....",
            	"reltags":{
              		"height": "4",
              		"level": "0",
              		"type": "level"
                        }
                    }
                ],
                "meta": {}
            },
            "geometry": {
                "type": "Polygon",
                "coordinates": .....
            }
        },
        etc...
    ]
}
```
## JOSM

To create the map use an editor such as JOSM. This will be used to create a data.json file with the structure of a building.

## Update

New updates and new features soon.. 🚀

Create by Vittorio Russo and supervisor Antonio della Selva (Università degli studi di Urbino Carlo Bo)
