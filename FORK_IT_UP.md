1. **Github**
	1. Fork github repos:  [cloud-native-cicd-starter](https://github.com/krumIO/cloud-native-cicd-starter) & [baseline-vue-app](https://github.com/krumIO/baseline-vue-app)
	2. Create github PAT, fine-grained:  write access for `Contents` and `Webhooks`
2. **Docker**
	1. Bring your own docker registry (dockerhub for our purposes, can cover others at secret creation)
3. **Rancher**
	1. Create secrets on rancher in namespace argocd
		1. githube-machine-user
			1. username, email, token (PAT)
		2. docker-push-user
			1. registry secret
			2. copy this to namespace `development` as well (or create an image-pull-user)
	2. Add forked cloud-native-cicd-starter as a chart repo in Rancher
	3. Install apps & customize values
		1. argo-workflow-ci
			1. update docker registry values
			2. update repositories and github owner
			3. update sslip hostname address
		2. argocd-app-of-apps
			1. update gitops.repoUrl to fork
	4. Visit ArgoCD, see apps
	5. Visit Workflows, see resources
	6. Edit forked baseline-vue-app, monitor build
	7. Visit ArgoCD, see app redeployment on image update
