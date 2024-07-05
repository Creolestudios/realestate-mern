# realestate-mern

This project provides comprehensive information about homes for potential buyers. It offers details about the property, including location, price, amenities, and other relevant features to help users make informed decisions when purchasing a home.

## Features ##
- Property Details: Access detailed information about each property, including size, price, number of bedrooms and bathrooms, and year built.
- Location Insights: Get information about the neighborhood, nearby schools, public transportation, and local amenities.
- Image Gallery: View high-quality images of the property and its surroundings.

## Project setup ##

- Clone the repository to your local machine.

### Server Setup ###

- Install Node.js(version 18) and npm on your machine.
- Open the terminal and navigate to the server folder.
- Run the command "npm install" to install the required dependencies.
- Create a .env file in the server folder and add the following environment variables:

  CLIENT_URL = Your MongoDB connection string.
  JWT_SECRET_KEY = A secret key for generating JSON Web Tokens.
  PORT = Backend Port 

- Run the command "npm start" to start the server.

### Client Setup ###

- Open the terminal and navigate to the client folder.
- Run the command "npm install" to install the required dependencies.
- Run the command "npm start" to start the client application.

## Common API Request File ##
To simplify making HTTP requests to the backend, we have created a common API request file using Axios. This file sets up a base URL and includes credentials with every request.

` const apiRequest = axios.create({
  baseURL: "http://localhost:{BACKEND_PORT}/api",
  withCredentials: true,
}); `





