FROM bitnami/node:12-prod

COPY build/expensify_integration-nginx/install_app.sh /install_app

RUN chmod +x /install_app && \
  apt-get update -y && \
  apt-get install build-essential git python2 -y && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/*

RUN /install_app expensify_integration https://github.com/Ion-Mobility-Infra/expensify_integration main

FROM urieltan/frappe:erpnext-nginx

COPY --from=0 /home/frappe/frappe-bench/sites/ /var/www/html/
COPY --from=0 /rsync /rsync
RUN echo -n "\nexpensify_integration" >> /var/www/html/apps.txt

VOLUME [ "/assets" ]

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["nginx", "-g", "daemon off;"]
