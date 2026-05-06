FROM mcr.microsoft.com/devcontainers/base:ubuntu

ENV DISPLAY=:0

RUN printf '%s\n' '#!/bin/bash' '$BROWSER "$1"' > /usr/bin/xdg-open \
    && chmod +x /usr/bin/xdg-open

# The Copilot agent's isBrowserAvailable() check fails if SSH_CONNECTION
# or SSH_CLIENT are set. These are injected by sshd for every session.
# BASH_ENV is sourced by bash before executing -c commands, which is how
# the JetBrains backend gets launched (via sshdwrapper.sh → bash -c).
RUN printf '%s\n' 'unset SSH_CONNECTION SSH_CLIENT SSH_TTY' \
    > /etc/profile.d/unset-ssh-vars.sh
ENV BASH_ENV=/etc/profile.d/unset-ssh-vars.sh
