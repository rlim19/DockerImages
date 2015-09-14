FROM rlim19/workspace
FROM rlim19/circos:0.67
MAINTAINER <rlim.email@gmail.com>

RUN \
  apt-get update && apt-get install -y ncbi-blast+ && \
  easy_install ibidas && \
  easy_install fastcluster && \
  git clone https://github.com/thiesgehrmann/proteny.git 

# make the directory executable
RUN \
  find /root/proteny -type f -exec chmod 755 {} \;

# prefer bash instead of dash
RUN \
  sudo rm /bin/sh && \
  sudo ln -s /bin/bash /bin/sh 

# alias for proteny
RUN echo "alias proteny='/root/proteny/run_proteny.sh'" >> .bash_aliases 

# change circos path 
ENV circos_dir /root/circos-0.67-7/bin/circos  
RUN sed -i "s,CIRCOS=.*,CIRCOS=$circos_dir,g" /root/proteny/circos_run 
