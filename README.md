# Ola-Bike-Ride-Demand-Forecast

Problem Statement

Ola Bikes are suffering losses and losing out from their competition due to their inability to fulfill the ride requests of many users. To tackle this problem you are asked to predict demand for rides in a certain region and a given future time window. This would help them allocate drivers more intelligently to meet the ride requests from users.

Goal

You have to predict ride requests (demand forecast) for a particular latitude and longitude for a requested future time window/duration.

Data Description

Raw Data contains a number (unique for every user), ride request timestamp (IST time), pickup and drop location latitude, and longitude.

Data Fields

number: unique id for every user

ts: DateTime of booking ride (IST time)

pick_lat: ride request pickup latitude

pick_lng: ride request pickup longitude

drop_lat: ride request drop latitude

drop_lng: ride request drop longitude

Defining a Good Ride Request

1. Count only 1 ride request by a user, if there are multiple bookings from the same latitude and longitude within 30 min of the last booking time.
2. If there are ride requests within 5 mins of the last booking time consider only 1 ride request from a user (latitude and longitude may or may not be the same).
3. If the geodesic distance from pickup and drop point is less than 50 meters consider that ride request as a fraud ride request.
4. Consider all ride requests where pick up or drop location is outside India bounding box: ['6.2325274', '35.6745457', '68.1113787', '97.395561'] as system error.
5. Karnataka is our prime city where we have a lot of drivers and ride requests to fulfill. We would not love to serve rides that are outside Karnataka and have pickup and drop geodesic distance > 500kms.
   Karnataka bounding box: ['11.5945587', '18.4767308','74.0543908', '78.588083']
