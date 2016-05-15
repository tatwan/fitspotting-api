#Fit Spotting API
http://www.fitspotting.com

### Fit Spotting REST API for searching hotel gym ratings, reviews and user photos

Fit Spotting iOS app is a social media app that allows users to rate hotels based on their Fitness Centers and overall fitness offerings. This API is meant for users who would like to integrate Fit Spotting reviews with their website or app or just to explore the data.

The original hotel listing is based on **Expedia Inc.** data with over 120,000 hotel listings around the globe. Majority of images are curated to focus on Fitness Centers/Gyms. 

## How to use the API
#### getFitSpots
```
http://www.fitspotting.com/api/public/getfitspots:1
```
return all hotels with 1 or more user reviews. This returns:

```
{
    "HotelID": "105306",
    "Name": "Arizona Biltmore, A Waldorf Astoria Resort",
    "Address1": "2400 E Missouri Avenue",
    "City": "Phoenix",
    "StateProvince": "AZ",
    "PostalCode": "85016",
    "Country": "US",
    "Latitude": "33.52331",
    "Longitude": "-112.02456",
    "frontImage": "http://media.expedia.com/hotels/1000000/10000/9800/9796/9796_281_b.jpg",
    "reviewsCnt": "1"
  }
```
**Example Usage**
```
/getfitspots:1  //retrieves all hotels with 1 or more reviews 
/getfitspots:2  //retrieves all hotels with 2 or more reviews 
/getfitspots:0  //retrieves all hotels limited to 1000 only 
```
**JSON Fields**

| Field  | Description |
| ------------- | ------------- |
| HotelID  |  Unique Hotel ID  |
| Name  | Hotel Name  |
| Address1 | Hotel Address |
| City  | Hotel City  |
| StateProvince | Hotel State if applicable |
| PostalCode  | Hotel Zip Code  |
| Country | Hotel Country based on 2 letter country code  |
| Latitude  | Goegraphical Coordinates - Latitude  |
| Longitude | Goegraphical Coordinates - Longitude  |
| frontImage  | In URL format, this is the main image for the hotel  |
| reviewsCnt  | Number of Review associated with the hotel  |


#### getReviews
```
http://www.fitspotting.com/api/public/getreviews:HotelID
```
return all reviews for the particular hotel. 

**Example Usage**
```
http://www.fitspotting.com/api/public/getreviews:105687
```
**returns**
```
[
  {
    "HotelID": "105687",
    "Rating": "3",
    "Review_Text": "Pretty decent. Good for cardio, and some with some creativity you can do weight resistant training. They have Dumbbells, though limited. Good number of benches, I like that they have barbells with weights. Equipment for resistant training was good, not a full gym style, but covered all the basics. I would recommend and stay there next time I am at LAX area."
  }
]
```
**JSON Fields**

| Field  | Description |
| ------------- | ------------- |
| HotelID  |  Unique Hotel ID  |
| Rating  | Fit Spotting User Star-Rating (scale 1-5)  |
| Review_Text | Fit Spotting User Review |


#### getImages
```
http://www.fitspotting.com/api/public/getimages:HotelID
```
return all gym/fitness images associated with the hotel. 

**Example Usage**
```
http://www.fitspotting.com/api/public/getimages:112534
```
**returns**
```
[
  {
    "HotelID": "112534",
    "URL": "http://www.fitspotting.com/images/112534-1.jpg",
    "Caption": "",
    "verified": "1"
  }
]
```
**JSON Fields**

| Field  | Description |
| ------------- | ------------- |
| HotelID  |  Unique Hotel ID  |
| URL  | Fitness Center/Hotel Gym Image  |
| Caption | Image Caption as entered by the user |
| verified |  Fit Spotting Image Verification (1=True, 0=False)

#### getHotels
```
http://www.fitspotting.com/api/public/gethotels:City
```
return all hotels for the city selected. Note: The query uses a %LIKE% statement. 

**Example Usage**
```
http://www.fitspotting.com/api/public/gethotels:dubai
http://www.fitspotting.com/api/public/gethotels:los angeles   //spaces allowed
```
**returns**
```
[
  {
    "HotelID": "105304",
    "Name": "Hyatt Regency Century Plaza",
    "Address1": "2025 Avenue Of The Stars",
    "City": "Los Angeles",
    "StateProvince": "CA",
    "PostalCode": "90067",
    "Country": "US",
    "Latitude": "34.05819",
    "Longitude": "-118.41564",
    "frontImage": "http://media.expedia.com/hotels/1000000/20000/12700/12670/12670_136_b.jpg",
    "reviewsCnt": "0"
  }
]
```
**JSON Fields**

| Field  | Description |
| ------------- | ------------- |
| HotelID  |  Unique Hotel ID  |
| Name  | Hotel Name  |
| Address1 | Hotel Address |
| City  | Hotel City  |
| StateProvince | Hotel State if applicable |
| PostalCode  | Hotel Zip Code  |
| Country | Hotel Country based on 2 letter country code  |
| Latitude  | Goegraphical Coordinates - Latitude  |
| Longitude | Goegraphical Coordinates - Longitude  |
| frontImage  | In URL format, this is the main image for the hotel  |
| reviewsCnt  | Number of Review associated with the hotel  |

