ARG PIP_VERSION=22.1.2
ARG POETRY_VERSION=1.1.13

FROM python:3.10.5-slim-bullseye as builder
ARG PIP_VERSION
ARG POETRY_VERSION
WORKDIR /tmp
COPY pyproject.toml poetry.lock ./
RUN pip install --no-cache-dir --upgrade pip==${PIP_VERSION} \
    && pip install --no-cache-dir --disable-pip-version-check poetry==${POETRY_VERSION} \
    && poetry export --without-hashes -f requirements.txt -o requirements.txt


FROM python:3.10.5-slim-bullseye
ARG PIP_VERSION
ARG POETRY_VERSION
ENV USERNAME=python
WORKDIR /usr/src/app/
COPY --from=builder /tmp/requirements.txt ./

RUN apt-get update \
    # NOTE: uncomment below if you execute apt-get to install something
    && apt-get install --no-install-recommends -y \
    libssl1.1=1.1.1n-0+deb11u3 \
    openssl=1.1.1n-0+deb11u3 \
    # NOTE: https://packages.debian.org/search
    && pip install --no-cache-dir --upgrade pip==${PIP_VERSION} \
    && pip install --no-cache-dir -r requirements.txt \
    && rm -rf \
    /bin/mount \
    /bin/umount \
    /bin/su \
    /usr/bin/chage \
    /usr/bin/chfn \
    /usr/bin/chsh \ 
    /usr/bin/expiry \
    /usr/bin/gpasswd \
    /usr/bin/newgrp \
    /usr/bin/passwd \
    /usr/bin/wall \
    /sbin/unix_chkpwd \
    /var/lib/apt/lists/* \
    && useradd ${USERNAME}

USER ${USERNAME}:${USERNAME}
COPY . .
CMD [ "python", "python_stub/hello.py" ]