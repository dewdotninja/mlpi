FROM --platform=linux/amd64 quay.io/jupyter/pytorch-notebook

USER root

RUN	pip install --upgrade pip && \
  	pip install scikit-learn  && \
        fix-permissions "/home/${NB_USER}"
