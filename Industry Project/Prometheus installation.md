# root@deco:~# cat /etc/prometheus/prometheus.yml

global:
  scrape_interval:     1s
  evaluation_interval: 1s
  external_labels:
    monitor: 'example'

rule_files:
   - alert_rules.yml

alerting:
  alertmanagers:
  - static_configs:
    - targets: ['alertmanager:9093']

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']

  - job_name: 'node'
    static_configs:
      - targets: ['192.168.123.212:9100']

# root@deco:~# cat /etc/prometheus/alert_rules.yml

groups:
  - name: instance_down
    rules:
      - alert: InstanceDown
        expr: up{job="node"} == 0
        for: 10s
        labels:
          severity: critical
        annotations:
          summary: "Instance {{ $labels.instance }} is down"
          description: "{{ $labels.instance }} of job {{ $labels.job }} has been down for more than 1 minutes."

# root@deco:~# cat /etc/alertmanager/alertmanager.yml

global:
  resolve_timeout: 5m

route:
  receiver: 'prom2teams-webhook'

receivers:
- name: 'prom2teams-webhook'
  webhook_configs:
  - url: 'http://192.168.123.211:8089/'
    send_resolved: true

templates:
- '/etc/alertmanager/*.tmpl'

# root@deco:~# cat /etc/alertmanager/server_offline.tmpl

templates:
- name: 'prom2teams-server-offline'
  text: |
    {
      "receiver": "{{ .Receiver }}",
      "status": "{{ .Status }}",
      "alerts": [
        {
          "status": "{{ .Status }}",
          "startsAt": "{{ .StartsAt }}",
          "endsAt": "{{ .EndsAt }}",
          "generatorURL": "{{ .GeneratorURL }}",
          "labels": {
            "alertname": "{{ .Labels.alertname }}",
            "instance": "{{ .Labels.instance }}",
            "job": "{{ .Labels.job }}",
            "severity": "{{ .Labels.severity }}"
          },
          "annotations": {
            "description": "{{ .Annotations.description }}",
            "summary": "{{ .Annotations.summary }}",
            "runbook_url": "{{ .Annotations.runbook_url }}"
          }
        }
      ],
      "externalURL": "{{ .ExternalURL }}",
      "version": "{{ .Version }}"
    }

# root@deco:~# cat /etc/prom2teams/config.toml

[route.default]
  receiver = "default"

[[route.route]]
  match = { severity = "critical" }
  templates = [ "markdown" ]

[[receiver]]
  name = "default"
  type = "teams"
  webhook_url = "https://decospan0.webhook.office.com/webhookb2/fa94e8ce-c01c-4fd1-9798-900a4412fea9@e64aa77f-1efc-40b8-982d-4e510e65203d/IncomingWebhook/b2cbd17ceb7f438abd31daf430266ea2/941e76a2-32e2"

# root@deco:~# cat docker-compose.yml

version: '3.9'

services:
  prometheus:
    image: prom/prometheus:latest
    container_name: prometheus
    volumes:
      - /etc/prometheus/prometheus.yml:/etc/prometheus/prometheus.yml
      - /etc/prometheus/alert_rules.yml:/etc/prometheus/alert_rules.yml
    ports:
      - "9090:9090"
    networks:
      - prom_network

  alertmanager:
    image: prom/alertmanager:latest
    container_name: alertmanager
    volumes:
      - /etc/alertmanager/alertmanager.yml:/etc/alertmanager/alertmanager.yml
    ports:
      - "9093:9093"
    networks:
      - prom_network

  prom2teams:
    image: idealista/prom2teams:latest
    container_name: prom2teams
    environment:
      - PROM2TEAMS_GROUP_ALERTS_BY=alertname
      - PROM2TEAMS_CONNECTOR=https://decospan0.webhook.office.com/webhookb2/fa94e8ce-c01c-4fd1-9798-900a4412fea9@e64aa77f-1efc-40b8-982d-4e510e65203d/IncomingWebhook/b2cbd17ceb7f438abd31daf430266ea2/941e76a2-32e2-4c52-b153-8d17c6f00f7e
    ports:
      - "8089:8089"
    networks:
      - prom_network

networks:
  prom_network:
    driver: bridge



