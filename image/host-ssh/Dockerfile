#build from parent directory using docker build -t host-ssh -f host-ssh/Dockerfile .
FROM alpine:latest
ADD ./host-ssh/entrypoint.sh /
RUN chmod +x /entrypoint.sh && \
  apk add --no-cache openssh-client && \
  mkdir -p ~/.ssh && \
  echo -e "Host *\n\tStrictHostKeyChecking no\n\tForwardAgent yes\n\n" > ~/.ssh/config
ENTRYPOINT ["/entrypoint.sh"]