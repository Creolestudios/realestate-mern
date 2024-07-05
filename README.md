# realestate-mern

This project provides comprehensive information about homes for potential buyers. It offers details about the property, including location, price, amenities, and other relevant features to help users make informed decisions when purchasing a home.

## Features

- Property Details: Access detailed information about each property, including size, price, number of bedrooms and bathrooms, and year built.
- Location Insights: Get information about the neighborhood, nearby schools, public transportation, and local amenities.
- Image Gallery: View high-quality images of the property and its surroundings.

## Project setup

- Clone the repository to your local machine.

### Server Setup

- Install Node.js(version 18) and npm on your machine.
- Open the terminal and navigate to the server folder.
- Run the command "npm install" to install the required dependencies.
- Create a .env file in the server folder and add the following environment variables:

  CLIENT_URL = Your MongoDB connection string.
  JWT_SECRET_KEY = A secret key for generating JSON Web Tokens.
  PORT = Backend Port

- Run the command "npm start" to start the server.

### Client Setup

- Open the terminal and navigate to the client folder.
- Run the command "npm install" to install the required dependencies.
- Run the command "npm start" to start the client application.

## Common API Request File

To simplify making HTTP requests to the backend, we have created a common API request file using Axios. This file sets up a base URL and includes credentials with every request.

```

const apiRequest = axios.create({
  baseURL: "http://localhost:{BACKEND_PORT}/api",
  withCredentials: true,
});

```

## User Verification

We have created this middleware in which Token came from cookie through request, for that we need to provide withCredentials true in axios request. This middleware will check if the user is authenticated or not.

```
  const token = req.cookies.token;
  if (!token) return res.status(401).json({ message: "Not Authenticated!" });

  jwt.verify(token, process.env.JWT_SECRET_KEY, async (err, payload) => {
    if (err) return res.status(403).json({ message: "Token is not Valid!" });
    req.userId = payload.id;

    next();
  });
```

## Displaying a Map with Property Pins

To visualize the locations of properties, you can use a MapContainer component from React-Leaflet. This example shows how to center the map based on the properties' coordinates and display pins for each property.

```
 <MapContainer
            center={
                items.length === 1
                    ? [items[0].latitude, items[0].longitude]
                    : [52.4797, -1.90269] // Default center if no items or multiple items
            }
            zoom={7}
            scrollWheelZoom={false}
            className="map"
        >
            <TileLayer
                attribution='&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
                url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
            />
            {items.map((item) => (
                <Pin item={item} key={item.id} />
            ))}
        </MapContainer>
```
