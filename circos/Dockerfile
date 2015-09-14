FROM rlim19/workspace
MAINTAINER rlim.emal@gmail.com

RUN ln -s /usr/bin/env /bin/env

RUN \ 
  apt-get update && \
  apt-get -y -q install build-essential libgd2-xpm-dev libgd-gd2-perl && \ 
  cpan Set::IntSpan module && \ 
  cpan Math::Bezier && \
  cpan SVG

RUN \
  wget http://circos.ca/distribution/circos-0.67-7.tgz && \
  tar xfz circos-0.67-7.tgz && \
  cd circos-0.67-7 && \ 
  cd bin && \
  for line in $(./list.modules); do cpan $line; done; 

RUN \
  echo 'PATH=$PATH:/root/circos-0.67-7/bin/;export PATH;' >> /root/.bashrc 

RUN \ 
  apt-get clean && \
  rm circos-0.67-7.tgz 

CMD ["bash"]
