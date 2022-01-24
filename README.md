docker run -d --name infracloudio infracloudio/csvserver:latest
docker ps -a

# check for docker  log
docker logs -f <conID>
root@training-worker2:/home/beddalasomasekar# docker logs -f 94777b1bd6f5
      2022/01/24 09:37:09 error while reading the file "/csvserver/inputdata": open /csvserver/inputdata: no such file or directory

# from above error it says input file is missing create the input file and data to it from gencsv.sh script

# once /csvserver/inputdata is available with data.

docker run -d -v /home/beddalasomasekar/inputdata:/csvserver/inputdata --name test2 infracloudio/csvserver:latest

# to access via port(9393) and env varibale run using below command
docker run -d -v /home/beddalasomasekar/inputdata:/csvserver/inputdata -e CSVSERVER_BORDER=orange --publish 9300:9393 --name test3 infracloudio/csvserver:latest


