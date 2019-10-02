FROM mongo:3.4-xenial
RUN apt-get update
RUN apt-get install default-jdk -y
RUN groupadd tomcat
RUN useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat
RUN mkdir /opt/tomcat
ADD apache-tomcat-8.5.46 /opt/tomcat
RUN cd /opt/tomcat
RUN chgrp -R tomcat /opt/tomcat
RUN chmod -R g+r conf
RUN chmod g+x conf
RUN chown -R tomcat webapps/ work/ temp/ logs/
RUN update-java-alternatives -l
ADD tomcat.service /etc/systemd/system/tomcat.service
RUN systemctl daemon-reload
RUN systemctl start tomcat
RUN systemctl status tomcat
RUN systemctl enable tomcat