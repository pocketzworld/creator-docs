# **Overview**

## **Introduction**

This is the official documentation for the Highrise Web API. Our API offers a broad spectrum of access to data from the Highrise game, designed with developers and community members in mind. This data can be utilized for a range of applications, from creating community apps to game analytics, or even enhancing Highrise bot functionality.

## **Getting Started**

All API requests start with the base URL:

```
https://webapi.highrise.game/
```

This base URL should be the recipient of all your requests to our API.

## **Pagination**

The Highrise Web API employs cursor-based pagination using the `starts_after` and `ends_before` request parameters. Here’s how it works:

- **`starts_after`**: This is the ID of the item from which you want to start fetching data. The server will return entries that come after this ID. If this parameter is not provided, the server starts from the first entry.
- **`ends_before`**: This is the ID of the item before which you want to stop fetching data. The server will return entries that come before this ID.

To help illustrate, here is an example:

1. **Initial request:**
    
    Example: **`GET https://webapi.highrise.game/rooms?limit=50`**
    
    This fetches the first 50 rooms. The **`room_id`** of the last room in the response will be used as a cursor for the next request.
    
2. **Fetching subsequent pages:**
    
    Example: **`GET https://webapi.highrise.game/rooms?starts_after=641ca75c543d7461b472ef63&limit=50`**
    
    In this example, **`starts_after=641ca75c543d7461b472ef63`** uses the last **`room_id`** from the previous request to fetch the next 50 rooms.
    
3. **Fetching previous pages:**
    
    Example: **`GET https://webapi.highrise.game/rooms?ends_before=641ca75c543d7461b472ef63&limit=50`**
    
    Here, **`ends_before=641ca75c543d7461b472ef63`** uses the first **`room_id`** from the current page to fetch the previous 50 rooms.
    

## **API Resources**

Below is a list of the all API resources currently available through the Web API.

- [Users](https://create.highrise.game/learn/web-api/endpoints/invoke_get_user)
- [Rooms](https://create.highrise.game/learn/web-api/endpoints/invoke_get_room)
- [Posts](https://create.highrise.game/learn/web-api/endpoints/invoke_get_post)
- [Items](https://create.highrise.game/learn/web-api/endpoints/invoke_get_item)
- [Grabs](https://create.highrise.game/learn/web-api/endpoints/invoke_get_grab)

## **API Responses**

All responses are in JSON format. Here is an example response:

```json
{
    "user": {
        "user_id": "641ca75c543d7461b472ef62",
        "username": "DAnie842",
        "outfit": [...],
        "bio": "Hey!!!!",
        "joined_at": "2023-03-23T19:24:12.954000+00:00",
        "last_online_in":  "2023-06-28T17:26:10.254000+00:00",
        "num_followers": 2,
        "num_following": 2,
        "num_friends": 1,
        "active_room": null,
        "country_code": "302",
        "crew": null,
        "voice_enabled": true
    }
}
```

## **Rate Limiting**

We implement rate limiting to ensure fair usage of the API. If a rate limit is surpassed within a designated time period, the API will respond with a HTTP 429 Too Many Requests status code. This mechanism helps prevent potential abuse and maintain the overall stability and reliability of the API service for all our users.

## **Authentication**

As of now, the API does not mandate any authentication tokens or API keys. All accessible data is public. Please note that any data modification or updating is unsupported.

## **Feedback and Support**

If you encounter any issues or have questions, we invite you to join our community discord server. We greatly value your feedback and are committed to ongoing improvement and content additions based on your suggestions.