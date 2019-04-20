# solar-observatory
Monitoring system for Enphase envoy-based photovoltaic systems

## Setup instructions

* install docker and docker-compose
* set ENVOY_HOST (ip address for your envoy) and ENVOY_PASS
(https://thecomputerperson.wordpress.com/2016/08/28/reverse-engineering-the-enphase-installer-toolkit/)

* in /solar-observatory/prometheus/prometheus.yml set the `targets` for the `node-exporter` job 
  (if you want to monitor your host machine as well)
  
* in /solar-observatory/grafana/config.monitoring set you password `GF_SECURITY_ADMIN_PASSWORD=foobar`
* `docker-compose build scraper`
* `chown -R 1000:1000 /solar-observatory`
* `docker-compose up -d`
* http://localhost:3000  Username: `admin` Password: `foobar` Import `/solar-observatory/dashboard.json`



I have 3 arrays of panels, so their are some location labeling for these arrays to help measure loads of each phase.
If you wish to label your panels,
Just replace the inverters `serials` map in scrape.py 
then rebuild the container. `docker-compose build scraper`, `docker-compose up -d`
(their is also an `ignorelist`  if you are unable to delete dead inverters from your envoy)

![dashboard](https://github.com/petercable/solar-observatory/blob/master/screenshot.png)
![dashboard](https://github.com/MasterCATZ/solar-observatory/blob/master/Screenshot%20from%202019-04-20%2015-14-27.png)
