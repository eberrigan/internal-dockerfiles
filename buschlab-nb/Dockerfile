FROM talmo/tf-extras

LABEL maintainer="Elizabeth Berrigan <eberrigan@salk.edu>"

# Install R environment
ARG R_CONDA_ENV=r
COPY --chown=${NB_UID}:${NB_GID} environment_r.yml "/home/${NB_USER}/tmp/"
RUN cd "/home/${NB_USER}/tmp/" && \
    mamba env create -p "${CONDA_DIR}/envs/${R_CONDA_ENV}" -f environment_r.yml && \
    mamba clean --all -f -y

# Link R environment to jupyter
RUN "${CONDA_DIR}/envs/${R_CONDA_ENV}/bin/R" -e 'IRkernel::installspec()' && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"

# Install R packages
RUN "${CONDA_DIR}/envs/${R_CONDA_ENV}/bin/R" \
    -e "install.packages(c('Seurat', 'Monocle3', 'ggplot2', 'Signac', 'shiny', 'EdgeR', 'DESeq2'), repos='https://cloud.r-project.org')"
