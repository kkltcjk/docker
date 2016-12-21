FROM opnfv/yardstick:latest                                                                     
MAINTAINER Jack Chen <jack.chen.8@qq.com>
LABEL version="0.1" description="nginx"

RUN apt-get update && apt-get install -y \                                                      
git \
nginx \ 
uwsgi \                                                                                         
python-pip \
uwsgi uwsgi-plugin-python

RUN git clone https://github.com/kkltcjk/install /root/install                                  
RUN git clone https://github.com/kkltcjk/api4yardstick /home/kklt/kklt

WORKDIR /home/kklt/kklt
RUN python setup.py install

RUN cp /root/install/plugin/nginx/yardstick.conf /etc/nginx/conf.d/                             

RUN pip install flask celery flasgger
RUN pip install flask_restful
RUN pip install flask_restful_swagger

# RUN echo "daemon off;" >> /etc/nginx/nginx.conf
RUN uwsgi -i /home/kklt/kklt/api/yardstick.ini

# CMD ["nginx", "-g", "daemon off;"]
# CMD ["/bin/bash", "-c", "service nginx restart && uwsgi -i /home/kklt/kklt/api/yardstick.ini && /bin/bash"]
# CMD ["/usr/sbin/nginx"]
# CMD /usr/sbin/nginx;uwsgi -i /home/kklt/kklt/api/yardstick.ini

WORKDIR /home/kklt

EXPOSE 5000
