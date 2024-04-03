
FROM openjdk:11 as base 
WORKDIR /app
COPY . .        # it means all files in this dir(first dot) are copied to (second dot) that is /app
RUN chmod +x gradlew
RUN ./gradlew build 

FROM tomcat:9
WORKDIR webapps
COPY --from=base /app/build/libs/sampleWeb-0.0.1-SNAPSHOT.war .     # to get detilas from above dockerfile, that are in chache, so we use  --from=stage(base  in our case ) , it is alias
  #/app/build/libs/  in  this that war file is stored
RUN rm -rf ROOT && mv sampleWeb-0.0.1-SNAPSHOT.war ROOT.war   #we remove default root folder and add our webapp to root folder
