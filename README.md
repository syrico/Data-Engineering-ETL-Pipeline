# Data-Engineering-ETL-Pipeline (Beginner)
Making a simple pipeline Extract Transform and Load automated using Airflow

## Road Map

<p align="center">
  <img width="460" src="https://github.com/syrico/Data-Engineering-ETL-Pipeline/blob/main/ETL_project.png?raw=true" alt="Sublime's custom image"/>
</p>


* First we ingest database postgres with psycopg2
* We managed what the table or information that we need
* We get the data and transform to dataframe using Pandas
* Cleansing or fill the blank/null/outlier data
* Load to internal database or we can do visualization

## Milstone
* Connect Database postgresql windows 10 from WSL
* Display the 5 country/genre-film who the most rent(accumulate) and display every-day(choose one)
* *hint* Create data-bulk before this day and count based payement_id to get the amount of customer/country/genre-film

## Setup Database Postgre SQL
* Install PostgreSQL
  * Windows 10: Install downloader from `https://www.postgresql.org/download/`
  * Ubuntu : `sudo apt update`,`sudo apt install postgresql`
* Set passwd :
  * `sudo passwd postgres`
* Start psql service :
  * `sudo service postgresql start`
* We can use the DVDRental database from `https://www.postgresqltutorial.com/postgresql-sample-database/` and modify the payment_date with command :
`update payment set payment_date + interval '1 year'` to run real-time scheduling using airflow


## Setup connection port 5432 windows 10
* Setup firewall windows 
  * Go to Windows Defender Firewall with Advanced Security
  * Choose Inbound Rules
  * Tab action and 'New Rule'
  * Choose port, next
  * Choose TCP, specific local ports : 5432 (postgres port)
* Setup connection list who can connect to postgresql
  * Go to `C:\Program Files\PostgreSQL\13\data`
  * Edit pg_hba.conf became 
    '# IPv4 local connections:'
    host    all             all             0.0.0.0/0    	        scram-sha-256
  * Edit postgresql.conf became :
    listen_addresses = '*' (uncommend listen_addresses)
* Connect to Postgresql windows from WSL
  * `su postgres` 
    *type the password*
  * `psql -h 'ip address win10' -U postgres -d DVDRental -p 5432` 
    *type the password*

