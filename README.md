# fluentd-on-kubernetes-elasticsearch-kibnan
Fluentd deployment on kubernetes and to elasticsearch and kibana
for eck mode, fluentd yaml file setting connection to elasticsearh with user login, should set like bleow:
      containers:
      - name: fluentd
        image: fluent/fluentd-kubernetes-daemonset:v1-debian-elasticsearch
        env:
          - name: K8S_NODE_NAME
            valueFrom:
              fieldRef:
                fieldPath: spec.nodeName
          - name:  FLUENT_ELASTICSEARCH_HOST
            value: "quickstart-es-default.default"
          - name:  FLUENT_ELASTICSEARCH_PORT
            value: "9200"
          - name: FLUENT_ELASTICSEARCH_SCHEME
            value: "https"
          - name: FLUENTD_SYSTEMD_CONF
            value: "disable"
          # Option to configure elasticsearch plugin with self signed certs
          # ================================================================
          - name: FLUENT_ELASTICSEARCH_SSL_VERIFY
            value: "false"
          # Option to configure elasticsearch plugin with tls
          # ================================================================
          #- name: FLUENT_ELASTICSEARCH_SSL_VERSION
          #  value: "TLSv1_2"
          # X-Pack Authentication
          # =====================
          - name: FLUENT_ELASTICSEARCH_USER
            value: "elastic"
          - name: FLUENT_ELASTICSEARCH_PASSWORD
            value: "3nfYck024hUfZVMl22W1g686"
