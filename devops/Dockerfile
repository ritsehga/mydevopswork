FROM registry.ixpress.icicibank.com:5000/ace-mqclient
USER aceuser
COPY packages /home/aceuser/bars
RUN ace_compile_bars.sh
