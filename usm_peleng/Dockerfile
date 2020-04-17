FROM perl:5

COPY cpanfile /
RUN cpanm --installdeps .
RUN mkdir -p /app /var/log/userside/usm_peleng/logs/

WORKDIR /app
