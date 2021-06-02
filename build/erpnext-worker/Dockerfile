ARG GIT_BRANCH=develop
ARG DOCKER_REGISTRY_PREFIX=frappe
FROM urieltan/frappe:frappe-worker

ARG GIT_BRANCH
RUN install_app erpnext https://github.com/Ion-Mobility-Infra/erpnext ${GIT_BRANCH}
