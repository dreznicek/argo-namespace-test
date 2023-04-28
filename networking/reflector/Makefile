CHART_REPO    := https://emberstack.github.io/helm-charts
CHART_NAME    := reflector
CHART_VERSION := 7.0.151

NAMESPACE := kubeseal

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
