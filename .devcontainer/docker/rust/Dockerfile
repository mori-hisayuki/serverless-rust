FROM rust:1.43.0

ARG USERNAME
ARG USER_UID
ARG USER_GID

ENV UID ${USER_UID}
ENV GID ${USER_GID}
ENV UNAME ${USERNAME}

RUN apt-get update \
    && apt-get -y install --no-install-recommends apt-utils dialog 2>&1 \
    && groupadd -g ${GID} ${UNAME} \
    && useradd -u ${UID} -g ${UNAME} -m ${UNAME} \
    && rustup update 2>&1 \
    && rustup component add rls rust-analysis rust-src rustfmt clippy 2>&1