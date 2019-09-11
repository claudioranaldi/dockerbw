FROM claudioranaldi/tibrv:8.4.5

MAINTAINER Mike Schippers <info@mikeschippers.com>

USER root

COPY TIB_TRA_*.zip /tmp/install/

ADD https://github.com/claudioranaldi/dockerbw/blob/master/docker/tibtra/TIB_TRA_linux.zip /tmp/install/

RUN mkdir -p /tmp/install/tibtra  && unzip /tmp/install/TIB_TRA_* -d /tmp/install/tibtra/ && \
	sed -i 's/<entry key="environmentName">.*<\/entry>/<entry key="environmentName">DockerEnvironment<\/entry>/g' /tmp/install/tibtra/TIBCOUniversalInstaller_TRA_*.silent && \
	sed -i 's/<entry key="configDirectoryRoot">.*<\/entry>/<entry key="configDirectoryRoot">\/opt\/tibco\/config<\/entry>/g' /tmp/install/tibtra/TIBCOUniversalInstaller_TRA_*.silent && \
	sed -i 's/<entry key="feature_Documentation_Designer">.*<\/entry>/<entry key="feature_Documentation_Designer">false<\/entry>/g' /tmp/install/tibtra/TIBCOUniversalInstaller_TRA_*.silent && \
	sed -i 's/<entry key="feature_Documentation_TRA">.*<\/entry>/<entry key="feature_Documentation_TRA">false<\/entry>/g' /tmp/install/tibtra/TIBCOUniversalInstaller_TRA_*.silent && \
	/bin/bash /tmp/install/tibtra/TIBCOUniversalInstaller-lnx-*.bin -silent -is:javahome /opt/jdk/jre/ && \
	chmod u+s /opt/tibco/hawk/*/bin/tibhawkhma && \
	rm -rf /tmp/install/tibtra /tmp/install/TIB_TRA_*