FROM rust:1.43.0

# arges
ARG USERNAME
ARG USER_UID
ARG USER_GID

# env
ENV UID ${USER_UID}
ENV GID ${USER_GID}
ENV UNAME ${USERNAME}

# useradd
RUN apt-get update \
    && apt-get -y install --no-install-recommends apt-utils dialog 2>&1 \
    && groupadd -g ${GID} ${UNAME} \
    && useradd -u ${UID} -g ${UNAME} -m ${UNAME}

USER ${USERNAME}
WORKDIR /home/vscode/develop

#rust setting
RUN rustup update 2>&1 \
    && rustup component add rls rust-analysis rust-src rustfmt clippy 2>&1

#nodenv setting
RUN git clone git://github.com/nodenv/nodenv.git ~/.nodenv \
    && git clone git://github.com/nodenv/node-build.git ~/.nodenv/plugins/node-build \
    && echo 'export PATH="$HOME/.nodenv/bin:$PATH"' >> ~/.bash_profile \
    && echo 'eval "$(nodenv init -)"' >> ~/.bash_profile \
    && echo 'source ~/.bash_profile' >> ~/.bashrc \
    && . ~/.bash_profile \
    && nodenv install 13.14.0 \
    && nodenv global 13.14.0 \
    && npm install

ENTRYPOINT ["tail", "-f", "/dev/null"]
