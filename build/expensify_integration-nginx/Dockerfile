FROM bitnami/node:12-prod

COPY build/expensify_integration-nginx/install_app.sh /install_app

RUN /install_app expensify_integration https://github.com/Ion-Mobility-Infra/expensify_integration main

FROM frappe/erpnext-nginx:v13.0.0-beta.11

COPY --from=0 /home/frappe/frappe-bench/sites/ /var/www/html/
COPY --from=0 /rsync /rsync
RUN echo -n "\nexpensify_integration" >> /var/www/html/apps.txt

VOLUME [ "/assets" ]

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["nginx", "-g", "daemon off;"]
