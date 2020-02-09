# Insight
My project for [Insight Boston](https://www.insightdatascience.com/) Data Science 2020A. Predicts service interruptions of commuter rails using past alerts records from [MBTA](https://www.mbta.com/developers/v3-api/streaming), reliability & ridership metrics from
the [MBTA performance](https://mbta-massdot.opendata.arcgis.com/search?tags=mbta%2Ccommuter%20rail), and past climate records from [NOAA](https://www.noaa.gov/weather). All code associated with the [web app](https://stayontrack-1.herokuapp.com/) can be found at my [commuterrail](https://github.com/ritwikamukherjee/commuterrail) repository.

# Motivation
Most current apps alert commuters of the real-time arrival departure times of the trains. But commuter rail lines suffer several service interruptions en route that commuters cannot account for ahead of time. My app Stay on Track! informs commuters of interruptions for the trains running tomorrow. 
This would help commuters make informed decisions about their travel plans. 

# Organization
My scripts were run on [Google Colab](https://colab.research.google.com). They have been organized into a ipynb file that is attached in this repository.  

# Workflow
The code contains extraction, cleaning, and exploration of the data. Followed by modelling the data to predict hours of interruption using a tree-based learning algorithm.
For extracting the MBTA information, you would require an API key. The json file contained past alerts information of train id, route id, description of the problem, causes, valid to & from. Queries were made using the MBTA [documentaion](https://cdn.mbta.com/sites/default/files/developers/2018-10-30-mbta-realtime-performance-api-documentation-version-0-9-5-public.pdf). 
The data was acquired from multiple sources. The past alerts information included information from Nov 2017 to 2019. Only service alert types such as track changes, delays, repairs, and maintenance were selected from the data. This information was combined temporally with reliability and ridership metrics of the 12 commuter lines. The frequency of the movement of the train 
was added from the commuter rail lines [schedules](https://www.mbta.com/schedules/commuter-rail). Direction of the train was extrapolated from the train ID information in the API. Imbalances in the data was handled by binning in 2 hour intervals across the day to be able to predict interruptions in every 2 hrs. 

# Built With
- [Google Colab](https://colab.research.google.com)
- [Jupyter Notebook](https://jupyter.org)

Dependencies can be found in the environment.yml file, and this file can be used to create a conda environment with
```console
foo@bar:~$ conda env create -f environment.yml
```
