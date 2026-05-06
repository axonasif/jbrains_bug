FROM mcr.microsoft.com/devcontainers/base:ubuntu

ENV DISPLAY=:0

RUN printf '%s\n' '#!/bin/bash' '$BROWSER "$1"' > /usr/bin/xdg-open \
    && chmod +x /usr/bin/xdg-open
