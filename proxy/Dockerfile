# https://registry.hub.docker.com/_/nginx/
FROM nginx:1.13.7

# 設定ファイルをコピー
COPY ./nginx.conf /etc/nginx/nginx.conf

# HTMLファイルをコピー
COPY ./index.html /usr/share/nginx/html/index.html
