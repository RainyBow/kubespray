FROM alpine:latest as files
RUN apk --no-cache add wget ca-certificates
WORKDIR /build
COPY build/kubespray-files/files_*.list /build/
RUN ARCH=$(uname -m | sed 's/x86_64/amd64/') \
    && cat files_${ARCH}.list > all_files.list 
RUN wget -nv -x -P /files -i all_files.list

FROM scratch
COPY --from=files /files /files
