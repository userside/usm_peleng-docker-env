FROM perl:5

COPY cpanfile /
RUN cpanm --installdeps .
RUN mkdir -p /app /var/log/usm_peleng

WORKDIR /app
CMD [ "perl", "usm_peleng.pl" ]