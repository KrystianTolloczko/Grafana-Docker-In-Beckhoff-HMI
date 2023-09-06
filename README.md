# Grafana Docker in Beckhoff HMI iFrame

for HTTP simply run:
`docker run -d -e "GF_PANELS_DISABLE_SANITIZE_HTML=true" -e "GF_SECURITY_ALLOW_EMBEDDING=true" -e "GF_AUTH_ANONYMOUS_ENABLED=true" -e "GF_AUTH_ANONYMOUS_ORG_NAME=Main Org." -e "GF_SERVER_SERVE_FROM_SUB_PATH=true" -e "GF_AUTH_JWT_AUTO_SIGN_UP=true" -p 3000:3000 --name=grafana --restart=always -v grafana_volume:/var/lib/grafana grafana/grafana-enterprise`

with HTTPS enabled will be:

`docker run -d -e "GF_PANELS_DISABLE_SANITIZE_HTML=true" -e "GF_SECURITY_ALLOW_EMBEDDING=true" -e "GF_AUTH_ANONYMOUS_ENABLED=true" -e "GF_AUTH_ANONYMOUS_ORG_NAME=Main Org." -e "GF_SERVER_SERVE_FROM_SUB_PATH=true" -e "GF_SERVER_HTTP_PORT=443" -e "GF_AUTH_JWT_AUTO_SIGN_UP=true" -e "GF_SERVER_PROTOCOL=https" -e "GF_SERVER_ENFORCE_DOMAIN=false" -e "GF_SERVER_CERT_FILE=/var/lib/grafana/ssl2/grafana.crt" -e "GF_SERVER_CERT_KEY=/var/lib/grafana/ssl2/grafana.key" -e "GF_SERVER_DOMAIN=(YOUR-DOMAIN)" -e "GF_SEVER_ROOT_URL=https://(YOUR-WEBSITE).tech:443" -p 443:443 --name=grafana --restart=always -v grafana_volume:/var/lib/grafana grafana/grafana-enterprise
`

NOTE: Change "Main Org." according to your organization.
