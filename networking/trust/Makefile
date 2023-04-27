CHART_REPO    := https://charts.jetstack.io
CHART_NAME    := cert-manager-trust
CHART_VERSION := 0.3.0

NAMESPACE := cert-manager

# Maintain a local inflated version of the chart
# https://github.com/kubernetes-sigs/kustomize/blob/master/examples/chart.md#best-practice
# This is a kustomize best-practice, and makes static testing easier.
# It also is easier with ArgoCD
$(CHART_NAME).yaml: Makefile values-$(CHART_NAME).yaml
	helm template $(CHART_NAME) \
		-f values-$(CHART_NAME).yaml \
		-n $(NAMESPACE) \
		--release-name $(CHART_NAME) \
		--repo $(CHART_REPO) > $@
