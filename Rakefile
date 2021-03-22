task :install do
  sh "sudo apt install libgdal-dev python3-gdal python3-rasterio"
  sh "CPLUS_INCLUDE_PATH=/usr/include/gdal C_INCLUDE_PATH=/usr/include/gdal pip install GDAL==2.2.4"
  sh "pip3 install rio-rgbify"
end

task :geotiff do
  sh "python3 ./fgddem.py -out_dir geotiff -replace_nodata_by_zero src/*.xml"
end

task :tiles do
  sh "gdalwarp geotiff/*.tif a.tif"
  sh "rio rgbify --min-z=15 --max-z=15 -b -10000 -i 0.1 -v a.tif tiles.mbtiles"
end

