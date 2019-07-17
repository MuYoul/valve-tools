# valve-tools

쿠버네티스 클러스터에 DevOps 도구 설치를 돕는 CUI 도구 입니다.
도구를 설치하기 위한 템플릿은 대부분 [stable helm chart](https://github.com/helm/charts/tree/master/stable)를 사용하지만 일부 차트는 incubator 또는 벤더 제공 helm chart를 사용합니다. 

해당 프로젝트는 [kops-cui](https://github.com/opsnow/kops-cui)의 도구 설치 구현을 분리해서 진행하는 프로젝트입니다. kops 기반 클러스터 외에 모든 쿠버네티스 클러스터에 범용적인 DevOps 툴체인 설치 도구로 사용하기 위해서 입니다.

* Support Cloud
  * AWS
* Support OS
  * MacOS
  * Linux (centos, ubuntu ...)


> <주의 사항><br/>툴은 valve 도구를 통해 만든 쿠버네티스 클러스터에 적합하게 설정되어 있습니다.

## Tools
다음과 같은 툴을 설치할 수 있습니다.
* DevOps Tools
  * jenkins
  * argocd
  * sonarqube
  * sonatype-nexus
  * chartmuseum
  * docker-registry
* Network Tools
  * external-dns
  * nginx-ingress
  * cert-manager
* Kubernetes Operation Tools
  * cluster-autoscaler
  * heapster
  * k8s-spot-termination-handler
  * kube-state-metrics
  * kubernetes-dashboard
  * metrics-server
* Security
  * aws-iam-authenticator
* Monitoring
  * prometheus
  * grafana
  * jaeger
  * datadog
  * newrelic-infrastructure
* Logging
  * fluentd-elasticsearch
* Storage
  * efs-provisioner
* Service Mesh
  * istio

## 사용 방법

### 실행
```bash
$ git clone https://github.com/opsnow-tools/valve-tools
$ ./helm.sh
```
### 도구 설치
TBD

### 도구 삭제
TBD

### 버전/설정 변경
각 도구를 설치하기 위한 helm chart의 입력 설정값은 chart/\<namespace>/\<chartname>.yaml 에 정의되어 있습니다. 

#### 템플릿 설정 변경
chart/\<namespace>/\<chartname>.yaml 파일의 상단에는 매니페스트를 생성하기 위한 몇 가지 조건을 설정할 수 있습니다. 여기에서 차트의 버전, 차트 레포지토리, 인스레스 생셩 여부, PVC 사용 여부 등을 명시할 수 있습니다.
```yaml
# chart-repo: stable/jenkins
# chart-version: 0.28.10
# chart-ingress: true
# chart-pvc: jenkins ReadWriteOnce 8Gi
```

### helm chart 설정 변경
chart/\<namespace>/\<chartname>.yaml 파일은 기본적인 애플리케이션의 속성을 포함하고 있습니다. 해당 값을 변경해서 애플리케이션의 기동 조건을 변경할 수 있습니다.