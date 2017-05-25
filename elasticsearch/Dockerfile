FROM elasticsearch

RUN sed -i -e 's/-Xms2g/-Xms512m/g' /etc/elasticsearch/jvm.options

EXPOSE 9200 9300

CMD ["elasticsearch"]


