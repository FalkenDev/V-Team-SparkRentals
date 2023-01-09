# SparkRentals Project
![Default branches](/v-teamAssets/sparkrentals.png "Default branches")
## Content
- [About](#about)
- [Download](#download)
- [Usage](#usage)
- [License and Tools](#license-and-Tools)
## About
This project is created by 4 students who attend Blekinge Institute of Technology in web programming. We were given the task of creating a system for a scooter company where we would, among other things, create a mobile-adapted web app for the customer, administrative web interface, a simulation program for the electric scooters, an intelligence program in the bicycle and a Rest API that distributes and retrieves information from the entire system and stores the information on a database.

**The Project is created by:**
- [Kasper Falk / FalkenDev](https://github.com/FalkenDev)
- [James Taylor](https://github.com/JamesTTTT)
- [Joel Persson](https://github.com/Jolpango)
- [Oscar Idberg](https://github.com/oscaridberg)

### Background
The company "Svenska Elsparkcyklar AB" needs a system that manages the rental of electric scooters in Swedish cities. The company operates in 3 different cities and plans to expand to more cities with the support of a new data system.

The data system comprises the following parts:

- Web-based solution for backend with connection to database to administer bicycles, charging stations, parking zones, permitted zones to cycle in, lending/returning, bicycle collection.
- REST API with the possibility to connect custom applications.
- Administrative web interface where you can see the status of bikes, stations and customers.
- Web interface to the customer so they can log in and view their account, lending history and payments.
- Mobile-adapted web app for the customer so they can see borrow/return the bike as well as see the status of the last trip and history of trips made.
- The intelligence in the bike, programs that control and monitor the bike (on, off, speed, limit speed, position, needs service/charging).

In addition, an option is included to simulate the entire system's operation in order to be able to test and verify the system's function.

## Repositories for this project
- [Mobile App](https://github.com/FalkenDev/SparkRentals-Mobile-App)
- [Admin Dashboard](https://github.com/FalkenDev/SparkRentals-Admin-Dashboard)
- [Webb Client](https://github.com/FalkenDev/SparkRentals-Webb-Client)
- [Scooter Simulator](https://github.com/FalkenDev/SparkRentals-Scooter-Simulator)
- [REST API](https://github.com/FalkenDev/SparkRentals-REST-API)
- [Data Generator](https://github.com/FalkenDev/SparkRentals-Data-Generator)

## Download
### Required environment variables
***.env:***

    #---------------------------------- General ----------------------------------
    # -> Configs
    API_TOKEN=["API TOKENS"]
    JWT_SECRET="JWT Sercret Code"
    # Database Location (MongoDB)
    DBURI="mongodb://mongodb_container:27017"

    #---------------------------------- Dummy Generator ----------------------------------
    # -> Configs
    CREATE_USER=100
    CREATE_PREPAID=100

    #---------------------------------- Scooter ----------------------------------
    # -> Configs
    GEOAPIFY_KEY="Geoapify API Key"
    NUMBER_OF_SCOOTERS=50
    UPDATE_FREQUENCY_MILLISECONDS=1000
    BATTERY_DEPLETION_RATE=0.0005
    SIMULATION_CITY=Karlskrona
    SIMULATION_ROUTE_PADDING=10

    #"DROP ZONE" of scooters
    #KARLSKRONA
    SIMULATION_MAX_LAT="56.166217"
    SIMULATION_MIN_LAT="56.158594"
    SIMULATION_MAX_LON="15.593868"
    SIMULATION_MIN_LON="15.583096"

    #SIMULATION
    SIMULATION_EMAIL="The Simulator Account Email"
    SIMULATION_PASSWORD="Password to the Simulator Account"

    #-------------- REST API URLS ------------------------------
    API_URL=http://URL:8393/v1

    #---------------------------------- REST API ----------------------------------
    # Localhost URL
    GOOGLE_CALLBACK_URL="http://"URL-TO-REST-API":8393/v1/auth/google/callback"
    GOOGLE_SUCCESS_URL="http://"URL-TO-WEBB-CLIENT":3000/login/google/success"
    GOOGLE_FAILURE_URL="http://"URL-TO-WEBB-CLIENT":3000/login/google/failure"

    # -> Configs
    REST_API_PORT=8393
    GOOGLE_CLIENT_ID="Google Client ID"
    GOOGLE_CLIENT_SECRET="Google Client Secret Code"
    COOKIE_KEY="Cookie Secret Code"
    CREATE_SINGLE_PREPAID=2
    API_CLUSTER=false

    #---------------------------------- REACT ----------------------------------
    #SparkRentals
    REACT_APP_API_URL="http://"URL-TO-REST-API":8393/v1"

    # -> Configs
    REACT_APP_REST_API_KEY="React Admin API KEY"
    REACT_APP_MAP_UPDATE_INTERVAL_BOOLEAN=1
    REACT_APP_MAP_UPDATE_INTERVAL=1000
    PORT=3000

    #---------------------------------- REACT NATIVE ----------------------------------
    API_KEY="Mobile API KEY"
    

### Run the whole system on Docker
- Fork / download the SparkRentals map

- Create .env file and insert the environment variables and change the inputs.

> docker compose up

## Usage
>**Mobile App**
To use the Mobile app you need to scan the qr code or enter the link in the mobile (Need to have the expo app). The link can be found in the terminal when running the mobile app.

>**Admin Dashboard**
To use the Admin Dashboard: http://localhost:3000 otherwise check the port in the docker compose file.

>**Scooter Simulator**
To use the Scooter Simulator you need to follow the steps at: [Scooter Simulator](https://github.com/FalkenDev/SparkRentals-Scooter-Simulator).

>**REST API**
To use the REST API: http://localhost:8393/v1/

>**Data Generator**
Auto loads when docker compose is running. Can be runned again follow the steps at: [Data Generator](https://github.com/FalkenDev/SparkRentals-Data-Generator).

>**Web Client**
To use the webb client: http://localhost:3000 otherwise check the port in the docker compose file.

## License and Tools
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white) ![NPM](https://img.shields.io/badge/NPM-%23000000.svg?style=for-the-badge&logo=npm&logoColor=white) ![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white) ![Expo](https://img.shields.io/badge/expo-1C1E24?style=for-the-badge&logo=expo&logoColor=#D04A37) ![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB) ![Figma](https://img.shields.io/badge/figma-%23F24E1E.svg?style=for-the-badge&logo=figma&logoColor=white) ![ESLint](https://img.shields.io/badge/ESLint-4B3263?style=for-the-badge&logo=eslint&logoColor=white) ![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white) ![Notion](https://img.shields.io/badge/Notion-%23000000.svg?style=for-the-badge&logo=notion&logoColor=white) ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white) ![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white) ![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white) ![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=for-the-badge&logo=mongodb&logoColor=white) ![Express.js](https://img.shields.io/badge/express.js-%23404d59.svg?style=for-the-badge&logo=express&logoColor=%2361DAFB) ![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E) ![TailwindCSS](https://img.shields.io/badge/tailwindcss-%2338B2AC.svg?style=for-the-badge&logo=tailwind-css&logoColor=white) ![React Native](https://img.shields.io/badge/react_native-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)

### Scrutinizer
**Mobile App**
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-Mobile-App/badges/quality-score.png?b=dev)](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-Mobile-App/?branch=dev) [![Build Status](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-Mobile-App/badges/build.png?b=dev)](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-Mobile-App/build-status/dev)

**Admin Dashboard**
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-Admin-Dashboard/badges/quality-score.png?b=dev)](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-Admin-Dashboard/?branch=dev) [![Build Status](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-Admin-Dashboard/badges/build.png?b=dev)](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-Admin-Dashboard/build-status/dev)

**Scooter Simulator**
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-Scooter-Simulator/badges/quality-score.png?b=dev)](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-Scooter-Simulator/?branch=dev) [![Build Status](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-Scooter-Simulator/badges/build.png?b=dev)](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-Scooter-Simulator/build-status/dev)

**REST API**
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-REST-API/badges/quality-score.png?b=dev)](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-REST-API/?branch=dev) [![Build Status](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-REST-API/badges/build.png?b=dev)](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-REST-API/build-status/dev)

**Web Client**
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-Webb-Client/badges/quality-score.png?b=dev)](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-Webb-Client/?branch=dev) [![Build Status](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-Webb-Client/badges/build.png?b=dev)](https://scrutinizer-ci.com/g/FalkenDev/SparkRentals-Webb-Client/build-status/dev)
