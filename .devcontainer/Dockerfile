FROM mcr.microsoft.com/vscode/devcontainers/base:ubuntu

# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends bubblewrap

USER root

# Install opam
RUN echo "/usr/local/bin" | sudo bash -c "sh <(curl -fsSL https://opam.ocaml.org/install.sh)"

# Initialize opam - we're disabling sandboxing as we're running inside of a container
RUN echo 5 | opam init --disable-sandboxing  
RUN opam switch create ocaml-5.2.1 5.2.1
RUN yes | opam install ocaml-lsp-server odoc ocamlformat utop

USER vscode
# TODO: Put the following into the vscode user profile.
# eval $(opam env)