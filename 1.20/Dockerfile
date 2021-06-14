FROM debian:latest AS build-env
RUN apt-get update 
RUN apt-get install -y curl git wget unzip libgconf-2-4 gdb libstdc++6 libglu1-mesa fonts-droid-fallback lib32stdc++6 python3 psmisc
RUN apt-get clean


WORKDIR /usr/local/flutter

ENV FLUTTER_VERSION="1.20.0"
ENV FLUTTER_HOME "/usr/local/flutter"
ENV PATH $PATH:$FLUTTER_HOME/bin


# Download and extract Flutter SDK
RUN mkdir -p $FLUTTER_HOME \
    && cd $FLUTTER_HOME \
    && curl --fail --remote-time --silent --location -O https://storage.googleapis.com/flutter_infra/releases/stable/linux/flutter_linux_${FLUTTER_VERSION}-stable.tar.xz \
    && tar xf flutter_linux_${FLUTTER_VERSION}-stable.tar.xz --strip-components=1 \
    && rm flutter_linux_${FLUTTER_VERSION}-stable.tar.xz

RUN flutter precache



# Run flutter doctor
RUN flutter doctor -v
