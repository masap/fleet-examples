SHELL=/bin/bash
KUBE_VERSION := 1.28.13

# 事前にインストールが必要
# https://github.com/yannh/kubeconform
.PHONY: lint-helm
lint-helm:
	helm -n spark-operator template spark-operator ./spark-op-1.1.27 -f ./values_spark-op-1.1.27.yaml | \
	kubeconform -verbose -kubernetes-version $(KUBE_VERSION) -output pretty \
	-summary -schema-location default \
	-schema-location 'https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/refs/heads/main/jsonnet/prometheus-operator/podmonitors-crd.json'

