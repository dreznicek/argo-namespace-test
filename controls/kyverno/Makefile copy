CHART_REPO    := https://kyverno.github.io/kyverno
CHART_NAME    := kyverno
CHART_VERSION := 2.6.2

NAMESPACE := kyverno

# Maintain a local inflated version of the chart
# https://github.com/kubernetes-sigs/kustomize/blob/master/examples/chart.md#best-practice
# This is a kustomize best-practice, and makes static testing easier.
# It also is easier with ArgoCD
$(CHART_NAME).yaml: Makefile values-$(CHART_NAME).yaml
	helm template $(CHART_NAME) \
		-f values-$(CHART_NAME).yaml \
		--version $(CHART_VERSION) \
		-n $(NAMESPACE) \
		--release-name $(CHART_NAME) \
		--repo $(CHART_REPO) > $@
