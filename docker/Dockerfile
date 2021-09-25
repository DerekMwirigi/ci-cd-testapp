FROM python:3.6

ENV EDITOR=vi \
    PYTHONUNBUFFERED=1 \
    DEBIAN_FRONTEND=noninteractive \
    TZ=Africa/Nairobi


RUN apt-get update \
    && apt-get install -yq --no-install-recommends \
    vim \
    cron \
    htop \
    less \
    binutils \
    libproj-dev \
    && rm -rf /var/lib/apt/lists/*

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get -yq autoremove

WORKDIR /code

ADD ../requirements.txt /code/
RUN pip install -r requirements.txt
ADD . /code/

RUN jupyter nbextension enable python-markdown/main
RUN jupyter nbextension enable hide_input_all/main
RUN jupyter nbextension enable toc2/main
RUN jupyter nbextension enable notify/notify
RUN jupyter nbextension enable printview/main
RUN jupyter nbextension enable tree-filter/index


EXPOSE 8001
