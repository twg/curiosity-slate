# Mobile Endpoints

## Get Home Page

```shell
curl "http://api.twgapi.com/v1/home"
```
> The above command returns JSON structured like this:

```json
{
  "data": {
    "featured_video": {
      "id": 1234567,
      "title": "What are rocks?",
      "speaker_names": "Brian Gilham, John Grant",
      "duration": 1024,
      "progress": 404,
      "description": "A really in-depth look at what rocks are.",
      "rating": 4,
      "bookmarked": true,
      "video_url": "http://videoprovider.com/videos/10.mp4",
      "thumbnail_url_small": "http://videoprovider.com/videos/10/smallThumb.png",
      "thumbnail_url_large": "http://videoprovider.com/videos/10/largeThumb.png",
      "type": {
        "id": 1234567,
        "name": "Documentary",
        "icon_url": "http://api.twgapi.com/icons/documentary.png"
      },
      "topic": {
        "id": 1234567,
        "name": "science",
        "label": "Science"
      }
    },
    "sections": [
      {
        "id":1234567,
        "name": "Thought-provoking videos",
        "label": "Videos that make you think",
        "color":"#000000",
        "total_number_of_videos":10,
        "videos": [
          {
            "id": 1234567,
            "title": "What are rocks?",
            "speaker_names": "Brian Gilham, John Grant",
            "duration": 1024,
            "progress": 404,
            "description": "A really in-depth look at what rocks are.",
            "rating": 4,
            "bookmarked": true,
            "video_url": "http://videoprovider.com/videos/10.mp4",
            "thumbnail_url_small": "http://videoprovider.com/videos/10/smallThumb.png",
            "thumbnail_url_large": "http://videoprovider.com/videos/10/largeThumb.png",
            "type": {
              "id": 1234567,
              "name": "Documentary",
              "icon_url": "http://api.twgapi.com/icons/documentary.png"
            },
            "topic": {
              "id": 1234567,
              "name": "science",
              "label": "Science"
            }
          }
        ]
      }
    ]
  }
}
```

This endpoint retrieves all Home Page content.

### HTTP Request

`GET http://api.twgapi.com/v1/home`

### HTTP Parameters

None

### HTTP Response

Parameter | Description
--------- | -----------
sections | Array of sections.