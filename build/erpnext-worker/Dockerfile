ARG GIT_BRANCH=v13.0.0-beta.11
ARG DOCKER_REGISTRY_PREFIX=frappe
FROM ${DOCKER_REGISTRY_PREFIX}/frappe-worker:${GIT_BRANCH}

ARG GIT_BRANCH
RUN install_app erpnext https://github.com/frappe/erpnext ${GIT_BRANCH}
RUN install_app expensify_integration https://github.com/Ion-Mobility-Infra/expensify_integration main
