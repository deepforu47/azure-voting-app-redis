FROM jbossacr.azurecr.io/jboss-fuse-7-tech-preview/fuse-eap-openshift:v1
USER root
RUN echo "appuser:x:500:0:appuser User:/home/appuser:/sbin/nologin" >> /etc/passwd && \
                echo "appuser:x:500:appuser" >> /etc/group
USER appuser
EXPOSE 9990
RUN $JBOSS_HOME/bin/add-user.sh adminUser Strongadmin --silent
ENV PRESERVE_JAVA_OPTS=false
ENV JAVA_OPTS="-Xmx2048m -Xms2048m -XX:MaxMetaspaceSize=256m -Djava.net.preferIPv4Stack=true"
ENV JAVA_OPTS="$JAVA_OPTS -Djboss.modules.system.pkgs=$JBOSS_MODULES_SYSTEM_PKGS -Djava.awt.headless=true"
CMD ["/opt/eap/bin/standalone.sh", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]