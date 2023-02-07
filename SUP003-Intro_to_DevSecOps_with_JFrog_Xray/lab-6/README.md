# Lab6 - JFROG ADVANCED SECURITY
- Prerequisites
- Xray at CI/CD
- Xray Reports (vuln, compliance, SBOM)

## Prerequisites
- A SAAS Instance of JFrog Platform. This will be provided as part of your enrollment to the Training class.
- JFrog CLI is installed on your machine by running `jf -v`

<br/>

## JFrog Advanced Security

### Vulnerability Contextual Analysis
- One of the most common inputs we gathered from developers on SCA tools is that they generate far too many results, requiring them to fix many vulnerabilities that do not, in reality, impose any risks.
- We also learned that these results are being inefficiently or incorrectly prioritized because of lack of context.
- Traditional CVSS scoring methods create even more complications, as they don’t take into account specific configurations, security mechanisms and other attributes of the analyzed software.
-


### Exposures Scanning Categories

#### Secrets Category
- Commonly enough, keys and credentials are being kept in containers and other forms of artifacts. They can appear as tokens and key files, sometimes hardcoded in the binary (which is clearly a malpractice) and sometimes in configurations and other text files.
- `jf xr curl -XGET "/api/v1/secrets/results?repo=containers&path=ics/latest/manifest.json"`
    - `repo` will be name of the container repository where docker image resides
    - `path` will be the path of the `manifest.json`

#### Services Category
- Cutting edge security engines will scan the configuration and way of usage of services (such as Apache and Nginx) and will identify misuse or misconfigurations that expose the software product to attack.
- `jf xr curl -XGET "/api/v1/services/results?repo=containers&path=ics/latest/manifest.json"`
    - `repo` will be name of the container repository where docker image resides
    - `path` will be the path of the `manifest.json`

#### Applications Category
- Cutting edge security engines will scan the configuration and way of usage of common OSS libraries (such as Django and Flask) and will identify misuse or misconfigurations that expose the software product to attack.
- `jf xr curl -XGET "/api/v1/applications/results?repo=containers&path=ics/latest/manifest.json"`
    - `repo` will be name of the container repository where docker image resides
    - `path` will be the path of the `manifest.json`

#### IaC Category
