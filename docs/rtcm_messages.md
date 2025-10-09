Ntrip - Networked Transport of RTCM via Internet Protocol
Ntrip stands for an application-level protocol for streaming Global Navigation Satellite System (GNSS) data over the Internet.
It is a generic, stateless protocol based on the Hypertext Transfer Protocol HTTP/1.1. The HTTP objects are enhanced to GNSS data streams. Ntrip is an RTCM standard designed for disseminating differential correction data (e.g in the RTCM-104 format) or other kinds of GNSS streaming data to stationary or mobile users over the Internet, allowing simultaneous PC, Laptop, PDA, or receiver connections to a broadcasting host. It supports wireless Internet access through Mobile IP Networks like GSM, GPRS, EDGE, or UMTS.

Ntrip is implemented in three system software components: NtripClients, NtripServers and NtripCasters. The NtripCaster is the actual HTTP server program whereas NtripClient and NtripServer are acting as HTTP clients.

Ntrip is meant to be an open none-proprietary protocol. Major characteristics of Ntrip dissemination technique are:

Based on the popular HTTP streaming standard; comparatively easy to implement when having limited client and server platform resources available.
Application not limited to one particular plain or coded stream content; ability to distribute any kind of GNSS data.
Potential to support mass usage; disseminating hundreds of streams simultaneously for up to thousand users possible when applying modified Internet Radio broadcasting software.
Considering security needs; stream providers and users do not necessarily get into contact, streams often not blocked by firewalls or proxyservers protecting Local Area Networks.
Enables streaming over any mobile IP network because of using TCP/IP.

Motivation
Since 1993 the RINEX Format is the standard file format for long-time storage and dissemination of GNSS receiver data, targeted mainly for the estimation of station coordinates in post-processing mode. RINEX data can be downloaded at several global and regional data centers usually as "daily" files containing 24 hours of data.
With ongoing development and the desire for getting information immediately the demand for accessing GNSS data with very small delay (in real-time) grew. Monitoring and of course positioning are probably the main use cases where real-time data is indispensable.
In order to disseminate GNSS data in real-time a new format had to be developed. RTCM messages (see [RTCM Home Page](http://www.rtcm.org/)) are nowadays widely used for this purpose. In addition to a format a transport protocol had to be defined, the so-called Ntrip streaming protocol, developed at BKG together with TU Dortmund. Using this protocol the data user is able to communicate with the data provider. Georg Weber, the former scientific director in the Department of Geodesy at BKG and representing BKG as a member of the RTCM Services Special Committee (SC) 104 played a decisive role in the development and promotion of real-time GNSS and Ntrip.
An important reason why Ntrip has been widely accepted is that BKG provides software tools for both, the server and the client side. On the server side the BKG Ntrip Broadcaster was developed to stream GNSS data in real-time over the Internet. The BKG Ntrip Client (BNC), which is not only an Ntrip client, is the leading internationally accepted standard Ntrip client application. It's development started in 2005 mainly by Leos Mervart from TU Prague.


Documentation
The material provided here describes the Ntrip real-time GNSS data transport protocol definition and the description of an Ntrip Example Implementation. Note that the protocol definition made available here is not the official Ntrip documentation. The standards can be purchased at the RTCM shop.
The Ntrip working group of RTCM SC104 provides a practical guidance to developers of Ntrip client software. The document is distributed freely at the RTCM shop. New

Ntrip, Version 1.0
In September 2004 Ntrip Version 1.0 became an RTCM Recommended Standard, see Press Release. The Transport Protocol Definition Vers. 1.0, Status 2004-09-30 is available here.

Ntrip, Version 2.0
In June 2009 RTCM Special Committee 104 (SC104) has completed a Version 2.0 of its Ntrip standard, see Press Release. Major changes compared to Version 1.0 are:

Cleared and fixed design problems and HTTP protocol violations
Replaced non standard directives
Adds chunked transfer encoding
Improves header records
Provides for sourcetable filtering
Provides for Real Time Streaming Protocol (RTSP) communication
Note that Ntrip Version 2.0 is fully downward compatible with Ntrip Version 1.0.

Ntrip Broadcaster
Global Navigation Satellite System (GNSS) data can be broadcast in real-time over the Internet using the Ntrip dissemination technique. In this context, the purpose of so-called Ntrip Broadcasters is to split data streams coming in from GNSS Reference Stations (Sources) for many simultaneously listening Clients. Ntrip Broadcasters do not alter the data. The communication between Sources, a Broadcaster, and its Clients is done through HTTP. Ntrip supports the dissemination of any GNSS data stream (GPS, GLONASS, Galileo, EGNOS, WAAS etc.) that needs 0.2 to 10 Kbit/s transmission rate and carries e.g.

RTCM observations or broadcast ephemeris or orbit/clock corrections, DGPS, RTK
RTCA corrections, [EGNOS](http://www.egnos-pro.esa.int/) & [WAAS](https://www.faa.gov/about/office_org/headquarters_offices/ato/service_units/techops/navservices/gnss/waas/)
Raw receiver data, vendor formats
RINEX observations
[BINEX](https://binex.unavco.org/binex.html) observations
other GNSS data/formats
Ntrip Broadcasters are currently installed world-wide to disseminate GNSS data in real-time. Visit [www.rtcm-ntrip.org](http://www.rtcm-ntrip.org/home) for a list of known installations.



Ntrip References
The following links shall provide some background information on Ntrip usage and further Ntrip development. We try to keep the list up to date. Feel free to inform us about your Ntrip publication in case you would like to see it listed below.

Ntrip: Protocol, Video on YouTube,English
Ntrip: Client Excercise, Video on YouTube, English
Ntrip: Application and Benefit in Modern Surveying Systems, English
Nutzung der Internet-Radio-Technologie zur Übertragung von GNSS-Daten, German
Die Zukunft spricht Ntrip, German
El proyecto EUREF-IP: Resultados con GPRS, Spanish
Techniques GPS-RTK appliquées à la trajectographie, French
GNSS-Echtzeitorbitkontrolle auf Basis Internet-transferierter ..., German
D-GNSS Accuracy Test At Bucu EPN Station, English
Networked Transport of RTCM via Internet Protocol, English
Ntrip: PP-Presentation, IAG, Sapporo, Japan, 2003, English
Новый формат Ntrip передачи..., Russian
Test Results of an Internet RTK System Based on the Ntrip Protocol, English
Ntrip - Ein neues Konzept zur Übertragung von Korrekturdaten unter SAPOS, German
Benefits of Telecommunications Technology to GPS Users, English
GNSS/GPS infrastructure to support LBS Positioning Systems in Victoria, English
NTRIP Estudi i Aplicacions, Catalan
Interactive Map of EUREF-IP Real-Time GNSS Data Streams, English
Verbesserte GPS-Positionsschätzung mit IP-transportierten ..., German


Data and Products
Real-time observations, ephemeris and corrections can be received from following non-exhaustive list of Ntrip Broadcasters. Corrections are disseminated in the RTCM-State Space Representation (RTCM-SSR) format that has been adopted by the IGS and can be used for real-time PPP.

Ntrip Broadcasters dedicated to support IGS and EUREF
Broadcaster	Operator	Registration	Remarks
cddis.nasa.gov	Crustal Dynamics Data Information System (CDDIS), North America	CDDIS	IGS observations and products, world-wide
gnssdata-ch1.cosmic.ucar.edu	IGS Central Bureau / UCAR COSMIC, North America	IGSCB	IGS observations and products, world-wide
igs-ip.net	Federal Agency for Cartography and Geodesy (BKG, Europe)	BKG	IGS station observations, world-wide
products.igs-ip.net	Federal Agency for Cartography and Geodesy (BKG, Europe)	BKG	IGS products, world-wide
auscors.ga.gov.au	Geoscience Australia (GA)	auscors	IGS observations and products, world-wide
ntrip.gnsslab.cn	Wuhan (China)	Wuhan	IGS observations and products, world-wide
112.65.161.226:2101	Shanghai Astronomical Observatory (China)	SHAO	IGS observations and products, world-wide
www.euref-ip.net	Federal Agency for Cartography and Geodesy (BKG, Europe)	BKG	EPN observations and products, Europe
www.euref-ip.be	Royal Observatory of Belgium (ROB), Europe	ROB	EPN observations and products, Europe
euref-ip.asi.it	Agenzia Spaziale Italiana (ASI), Europe	ASI	EPN observations and products, Europe

Observations
For the very beginning real-time observations have been made available on IGS and EUREF broadcasters in form of legacy messages for GPS and GLONASS (1004, 1012). Nowadays they have been more and more replaced by the new RTCM3 Multi-Signal Message (MSM) format that was developed to handle all GNSS constellations, signals, and observation types.


Broadcast Ephemeris
Several Ntrip broadcasters disseminate streams carrying only broadcast ephemeris. They derive their stream contents independently from a globally distributed selection of mainly EUREF and IGS reference stations. Ephemeris message repetition rates vary between 1 and 5 seconds.

non-exhaustive list of broadcast ephemeris streams
Caster:Port	Mountpoint	GNSS	Provider	Sign up
products.igs-ip.net:2101	BCEP00BKG0	GPS+GLO+GAL+BDS+QZS	BKG	Registration
wox.geopp.de:2101	WW_EPH	GPS+GLO	Geo++	support(at)geopp.de
ntrip.gnssonline.eu	RTCM3EPH	GPS+GLO	Alberding GmbH	info(at)alberding.eu
Broadcast Ephemeris messages from globally distributed streams are also converted to RINEX Navigation files. These files are made available for download at https://igs.bkg.bund.de/root_ftp/NTRIP/BRDC/. Unlike daily concatenated files from reference stations, their 24h sliding window content is updated every 15 minutes.



Broadcast Orbit and Clock Corrections
Precise orbits and clocks can be derived from corrections to Broadcast Ephemeris. RTCM's State Space Representation (SSR) Working Group has developed appropriate v3 messages to disseminate such Broadcast Corrections in real-time. The following messages are defined:

Message	Contents
1057	GPS orbit corrections to Broadcast Ephemeris
1058	GPS clock corrections to Broadcast Ephemeris
1059	GPS code biases
1060	Combined orbit and clock corrections to GPS Broadcast Ephemeris
1061	GPS User Range Accuracy
1062	High-rate GPS clock corrections to Broadcast Ephemeris
1063	GLONASS orbit corrections to Broadcast Ephemeris
1064	GLONASS clock corrections to Broadcast Ephemeris
1065	GLONASS code biases
1066	Combined orbit and clock corrections to GLONASS Broadcast Ephemeris
1067	GLONASS User Range Accuracy
1068	High-rate GLONASS clock corrections to Broadcast Ephemeristd

Orbit corrections are provided in along-track, cross-track and radial components. These components are defined in the earth-centered, earth-fixed reference frame of the broadcast ephemeris. Clock corrections are not adjusted for the 2nd-order relativistic effect. After applying corrections, the satellite position and clock is referred to the 'ionospheric free' phase center of the antenna which is compatible with the broadcast orbit reference. The orbit and clock corrections do neither include local effects (like Ocean Loading or Solid Earth Tides) nor atmospheric effects (ionosphere and/or troposphere). There is currently no RTCM SSR message for ionospheric state parameters. The development of ionospheric messages will be the next step in the schedule of the RTCM State Space Representation Working Group.