<p align="center">
  <a href="https://github.com/growthspace-engineering/gce-cloudsql-proxy-action" target="blank"><img src="logo-white.svg" width="250" alt="Logo" />
  </a>
  <h2 align="center">
    @GrowthSpace/gce-cloudsql-proxy-action
  </h2>
</p>
<p align="center">
  Github action which will start a <a href="https://cloud.google.com/sql/docs/postgres/sql-proxy" target="_blank">Google Cloud SQL Proxy</a> as Docker container. 
</p>
<hr>

## Getting Started 

### Prerequisites

Set up the following resources manually in the Cloud Console 
or use a tool like [Terraform](https://www.terraform.io).

* Running Cloud SQL instance with a public IP address
* Create Service Account with Role `Cloud SQL Client` and export a new JSON key.


### Github Action Inputs

| Variable                         | Description                                                                 |
|----------------------------------|-----------------------------------------------------------------------------|
| `creds`                          | ***Required*** Service Account JSON Key (not base64 encoded)                |
| `instances`                       | ***Required*** Cloud SQL connection names. Expects a comma-separated list of CloudSQL instance names                                    |
| `port`                           | Expects a comma-separated list of ports corresponding to each CloudSQL instance. If not provided, it defaults to port 5432.                                                |
| `proxy_version`                  | Cloud SQL Proxy version, default 1.21.0                                     |


## Example Usage

```yaml
uses: growthspace-engineering/gce-cloudsql-proxy-action@v2.0.2
with:
  creds: ${{ secrets.GOOGLE_APPLICATION_CREDENTIALS }}
  instances: my-project:us-central1:instance-1,my-project:us-central1:instance-2
  ports: 5432,5433
```

