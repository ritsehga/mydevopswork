FROM ibmcom/ace-mqclient
USER aceuser
COPY packages/*.bar /home/aceuser/bars
RUN ace_compile_bars.sh
