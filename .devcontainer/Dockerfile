ARG GOLANG_VERSION
FROM golang:${GOLANG_VERSION}

RUN apt-get update && \
    apt-get install git sudo -y && \
    apt-get clean
ENV GO111MODULE=on
ENV GOPATH=/go
RUN go install github.com/zeromicro/go-zero/tools/goctl@latest
RUN go install github.com/golang/protobuf/protoc-gen-go@v1.3.2

WORKDIR /tmp
COPY scripts/*.sh .
RUN chmod +x *.sh

ARG USER
RUN ./create-user.sh ${USER}
RUN chown ${USER}:sudo -R ${GOPATH}
RUN chown ${USER}:sudo .

ARG WORKSPACE
ARG PROFILE
RUN mv load-*.sh /home/${USER}/ && \
    usermod -aG sudo ${USER} && \
    echo "%sudo ALL=(ALL:ALL) ALL" | EDITOR="tee -a" visudo && \
    echo ". ~/load-env.sh ${WORKSPACE} ${PROFILE}" >> /home/${USER}/.bashrc && \
    echo ". ~/load-completions.sh" >> /home/${USER}/.bashrc

USER ${USER}
RUN ./install-bun.sh
