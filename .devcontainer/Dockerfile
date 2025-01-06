FROM mcr.microsoft.com/vscode/devcontainers/base:ubuntu

# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends bubblewrap

# Install opam
USER root
RUN echo "/usr/local/bin" | sudo bash -c "sh <(curl -fsSL https://opam.ocaml.org/install.sh)"

# Initialize opam - we're disabling sandboxing as we're running inside of a container
USER vscode
RUN echo 5 | opam init --disable-sandboxing  
RUN opam switch create ocaml-5.2.1 5.2.1
RUN opam install -y ocaml-lsp-server odoc ocamlformat utop

USER vscode
# TODO: Put the following into the vscode user profile, or just hardcore the output of `opam env`
# eval $(opam env)