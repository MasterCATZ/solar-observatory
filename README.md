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
* http://localhost:3000  Username: `admin` Password: `foobar` import `solar-observatory/dashboard.json`



I have 3 arrays of panels, so I have some location labeling for these 3 arrays to measure AMPS of each string.
If you wish to label your panels
just replace the `serials` map in scrape.py and rebuild the container.

![dashboard](https://github.com/petercable/solar-observatory/blob/master/screenshot.png)
