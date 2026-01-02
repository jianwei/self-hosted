ARG BASE_IMAGE
FROM ${BASE_IMAGE}
USER 0
RUN set_proxy() { \
    local proxy_var=$1; \
    local proxy_type=$2; \
    local proxy_val=$(eval echo \$$proxy_var); \
    if [ -n "$proxy_val" ]; then \
        local proxy_url=$(echo "$proxy_val" | sed 's|127\.0\.0\.1|host.docker.internal|g'); \
        echo "Acquire::${proxy_type}::proxy \"$proxy_url\";" >> /etc/apt/apt.conf; \
    fi; \
}; \
set_proxy HTTP_PROXY http; \
set_proxy HTTPS_PROXY https; \
set_proxy http_proxy http; \
set_proxy https_proxy https; \
sed -i 's|http://deb.debian.org|http://mirrors.aliyun.com|g' /etc/apt/sources.list.d/debian.sources 2>/dev/null || \
sed -i 's|http://deb.debian.org|http://mirrors.aliyun.com|g' /etc/apt/sources.list 2>/dev/null || true; \
sed -i 's|http://security.debian.org|http://mirrors.aliyun.com/debian-security|g' /etc/apt/sources.list.d/debian.sources 2>/dev/null || \
sed -i 's|http://security.debian.org|http://mirrors.aliyun.com/debian-security|g' /etc/apt/sources.list 2>/dev/null || true; \
apt-get update && apt-get install -y --no-install-recommends cron && \
rm -r /var/lib/apt/lists/*
COPY entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
