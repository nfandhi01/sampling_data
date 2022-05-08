# sampling_data
#! /usr/bin/bash

#download file excel dan link dan masukkan ke folder data
wget -P ./data https://github.com/labusiam/dataset/raw/main/weather_data.xlsx

cd data

#convert fodder setiap sheet menjadi csv
in2csv weather_data.xlsx --sheet 'weather_2014' > weather_2014.csv
in2csv weather_data.xlsx --sheet 'weather_2015' > weather_2015.csv 

#gabung data eather 2014 dan 2015 dengan nama weather.csv
csvstack weather_2014.csv weather_2015.csv > weather.csv

#hapus file weather_data.xlsx
rm weather_data.xlsx

#sampling file weather.csv dengan rate 0.3
cat weather.csv | sample -r 0.3 > sample_weather.csv
