# speedtest-tracker
This project runs the henrywhitaker3/speedtest-tracker container which runs a speedtest every hour and graphs the results. The back-end is written in Laravel and the front-end uses React. It uses Ookla's Speedtest cli to get the data and uses Chart.js to plot the results.

Docker Homepage: https://hub.docker.com/r/henrywhitaker3/speedtest-tracker 

Project Source: https://github.com/henrywhitaker3/Speedtest-Tracker

![image](https://user-images.githubusercontent.com/127797701/226963907-80ee2aae-f1d5-499b-9b84-ba0f6d8c8559.png)

## Setup:
- Edit your Cradlepoint router configuration and navigate to System > Containers > Projects and click Add.  
- Give your project a name ("Speedtest-Tracker") and click on the Compose tab.
- Paste the following docker-compose (YAML) into the compose tab of your project and click save.

```yaml
version: '2.4'
services:
  speedtest:
    image: henrywhitaker3/speedtest-tracker:dev-arm
    ports:
     - 8000:80
    volumes:
     - data:/config
    environment:
     - OOKLA_EULA_GDPR=true
    restart: unless-stopped
volumes:
  data:
    driver: local
```

## Usage:  
- Use NCM Remote Connect LAN Manager to create a profile for "Speedtest-Tracker" at 127.0.0.1 port 8000 protocol HTTP.
- Connect to the "Speedtest-Tracker" profile you created.


