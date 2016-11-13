
![](Icon-72@2x.png)
#Fit Spotting API 
http://www.fitspotting.com

# Fit Spotting API now requires a token. Please send an email to request your access token. 

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
    "HotelID": "105655",
    "Name": "The Fairmont Miramar Hotel & Bungalows",
    "Address1": "101 Wilshire Blvd",
    "City": "Santa Monica",
    "StateProvince": "CA",
    "PostalCode": "90401",
    "Country": "US",
    "Latitude": "34.01716",
    "Longitude": "-118.50075",
    "frontImage": "http://www.fitspotting.com/images/2004A96D-14D3-490B-9278-7B50A47A49B3.jpeg",
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
return all gym/fitness images associated with the hotel. Images are uploaded by users through the Fit Spotting iOS app.

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

#### getHotelsGPS
```
http://www.fitspotting.com/api/public/gethotels:lat:long
```
Returns top 50 hotels within 100 miles radius from the coordinates submitted. Results are sorted by distance where closest hotels show up first.

**Example Usage with Latitude = 33.979389 and Longitude = -106.575363**
```
http://www.fitspotting.com/api/public/gethotelsgps:33.979389:-106.575363

```
**returns**
```
 {
    "reviews": "0",
    "hotel_image": "http://media.expedia.com/hotels/8000000/7390000/7383300/7383205/7383205_17_b.jpg",
    "hotel_ID": "448957",
    "StarRating": "2.0",
    "hotel_name": "Rodeway Inn",
    "hotel_address": "807 Highway 85",
    "hotel_city": "Socorro",
    "hotel_state": "NM",
    "hotel_country": "US",
    "hotel_postal": "87801",
    "hotel_location": "Near Sedillo Park",
    "hotel_long": "-106.89218",
    "hotel_lat": "34.04813",
    "distance": "18.8"
  }
```
**JSON Fields**

| Field  | Description |
| ------------- | ------------- |
| Reviwes | Number of User Reviews |
| Hotel_Image | Primary Hotel Image |
| Hotel_ID  |  Unique Hotel ID  |
| StarRating | Hotel Star Rating as in a Five Start Hotel ..etc and not to be confused with user rating |
| Hotel_Name  | Hotel Name  |
| Hotel_Address | Hotel Address |
| Hote_City  | Hotel City  |
| Hotel_State | Hotel State if applicable |
| Hotel_Postal  | Hotel Zip Code  |
| Hotel_Country | Hotel Country based on 2 letter country code  |
| Hotel_Location | Description of a close major point of interest or attraction |
| Hotel_Long  | Goegraphical Coordinates - Longitude  |
| Hotel_Lat | Goegraphical Coordinates - Latitude  |
| Distance  | Distance from coordinates in miles  |

#### getHotelName
```
http://www.fitspotting.com/api/public/gethotelname:Hotel Name
```
Search hotels by name. Return up to 45 hotels using Text Search/Natural Language Mode with relevance score. 

**Example Usage**
```
http://www.fitspotting.com/api/public/gethotelname:beach view
http://www.fitspotting.com/api/public/gethotelname:disneyland   //spaces allowed
```
**returns**
```
{
    "HotelID": "115093",
    "Country": "US",
    "State": "CA",
    "Postal": "92802",
    "City": "Anaheim",
    "Address1": "1150 W Magic Way",
    "Name": "Disneyland Hotel - On Disneyland Resort Property",
    "starRating": "4.0",
    "Type": "Hotel",
    "Address": "1150 W Magic Way, Anaheim, CA, US",
    "Longitude": "-117.927180",
    "Latitude": "33.812680",
    "relevance": "13.05816650390625"
  }
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
| reviewsCnt  | Number of Review associated with the hotel  |
| StarRating | Hotel Star Rating as in a Five Start Hotel ..etc and not to be confused with user rating |
| Type | For this release, Type will always be "Hotel". Other types can be "Airport" or "City" to allow searches on|
| Relevance | Search Relevance Score highest showing first - using NATURAL LANGUAGE MODE |



