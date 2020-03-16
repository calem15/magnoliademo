FROM openjdk:10-jdk
WORKDIR /
RUN wget -O magnolia-cms.zip "https://nexus.magnolia-cms.com/content/repositories/magnolia.public.releases//info/magnolia/bundle/magnolia-community-demo-bundle/6.1.4/magnolia-community-demo-bundle-6.1.4-tomcat-bundle.zip"
RUN unzip magnolia-cms.zip
RUN rm magnolia-cms.zip
COPY mysql-connector-java_8.0.19-1debian10_all.deb /
RUN apt install /mysql-connector-java_8.0.19-1debian10_all.deb
WORKDIR magnolia-6.1.4/apache-tomcat-9.0.10/bin/
RUN rm -f /magnolia-6.1.4/apache-tomcat-9.0.10/webapps/magnoliaAuthor/WEB-INF/lib/derby-10.14.2.0.jar
RUN rm -f /magnolia-6.1.4/apache-tomcat-9.0.10/webapps/magnoliaPublic/WEB-INF/lib/derby-10.14.2.0.jar
COPY mysql-connector-java-8.0.19.jar ../webapps/magnoliaAuthor/WEB-INF/lib/
COPY mysql-connector-java-8.0.19.jar ../webapps/magnoliaPublic/WEB-INF/lib/
ENTRYPOINT ["bash", "-c", "./magnolia_control.sh start --ignore-open-files-limit && tail -f ../logs/catalina.out"]
