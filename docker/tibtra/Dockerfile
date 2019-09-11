FROM claudioranaldi/tibrv:8.4.5

MAINTAINER Mike Schippers <info@mikeschippers.com>
USER root

COPY TIB_TRA_linuxnozip  /tmp/install/

RUN ls -la /tmp/install &&  mkdir -p /tmp/install/tibtra &&  /tmp/install/TIB_TRA_linuxnozip -d /tmp/install/tibtra && \
	sed -i 's/<entry key="environmentName">.*<\/entry>/<entry key="environmentName">DockerEnvironment<\/entry>/g' /tmp/install/tibtra/TIBCOUniversalInstaller_TRA_*.silent && \
	sed -i 's/<entry key="configDirectoryRoot">.*<\/entry>/<entry key="configDirectoryRoot">\/opt\/tibco\/config<\/entry>/g' /tmp/install/tibtra/TIBCOUniversalInstaller_TRA_*.silent && \
	sed -i 's/<entry key="feature_Documentation_Designer">.*<\/entry>/<entry key="feature_Documentation_Designer">false<\/entry>/g' /tmp/install/tibtra/TIBCOUniversalInstaller_TRA_*.silent && \
	sed -i 's/<entry key="feature_Documentation_TRA">.*<\/entry>/<entry key="feature_Documentation_TRA">false<\/entry>/g' /tmp/install/tibtra/TIBCOUniversalInstaller_TRA_*.silent && \	
	/bin/bash /tmp/install/tibtra/TIBCOUniversalInstaller-lnx-*.bin -silent -is:javahome /usr/lib/jvm/java-7-openjdk-amd64/jre/ && \
	chmod u+s /opt/tibco/hawk/*/bin/tibhawkhma && \
	rm -rf /tmp/install/tibtra /tmp/install/TIB_TRA_linuxnozip