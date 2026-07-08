# World Explorer: Cyber Map

World Explorer is an interactive cybersecurity map built with D3.js and vanilla JavaScript. The project allows users to explore cybersecurity information for countries through a visual world map.

The application combines geographic data, structured country profiles and external CVE data in a client side application with no backend or build step.


## Features

Users can click on a country, search by country name or select a random country. The map supports zooming and automatically focuses on countries selected through search or random selection.

Country profiles can include:

* National CERT or security agency
* Responsible disclosure information
* Known cybersecurity incidents
* Incident timelines with year, severity and source links
* Local information security companies
* Security recommendations
* Major technology vendors
* Live vendor related CVE counts
* References to external sources

## Data structure

The main dataset contains profiles for 195 countries and is stored in `data/countries-all.json`. Additional country information can be loaded from JSON files in the `packs` directory.

The application uses a custom deep merge function to combine data from multiple sources. Incident records are deduplicated using their year and title, while other arrays are merged without duplicate values.

Country names are also normalised through an alias mapping system. This handles differences between the GeoJSON dataset and the country database, such as mapping `Russian Federation` to `Russia`.

Users can also import additional JSON content packs directly through the interface. Imported data is merged into the current dataset in memory.

## Live CVE data

For countries with configured technology vendors, the application can retrieve live CVE counts from the NVD REST API.

If the NVD request fails, the application attempts to use the CIRCL CVE API as a fallback source.

CVE counts are based on vendor keyword searches and should therefore be understood as an overview rather than an exact measurement of vulnerabilities associated with a country.

## Technologies

* D3.js v7
* Vanilla JavaScript
* HTML and CSS
* GeoJSON
* NVD REST API
* CIRCL CVE API

## Run locally

The project loads local JSON files, so it needs to be served over HTTP.

```bash id="a7n2kp"
git clone https://github.com/Fjonaam/cyber-world-map.git
cd cyber-world-map
python3 -m http.server 8000
```

Then open:

```text id="w4p9mx"
http://localhost:8000
```

## Background

This project was developed during my bachelor's degree in Cyber Security at Høyskolen Kristiania. It started as a way to learn D3.js and interactive data visualisation, and developed into a larger project involving geographic data, cybersecurity datasets, API integration, data merging and normalisation.

## License

MIT
