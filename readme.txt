-------------------------------------------------

			# TERRAFORM-WORK #

-------------------------------------------------

########################################################
### Terraform

https://www.terraform.io/
https://developer.hashicorp.com/terraform/docs

https://developer.hashicorp.com/terraform/docs/terraform-tools

https://github.com/shuaibiyy/awesome-terraform

########################################################
### Reference

-  Iac
https://www.redhat.com/ko/topics/automation/what-is-infrastructure-as-code-iac

- Terraform
https://j-dev.tistory.com/search/Terraform?page=1
https://velog.io/@borab/terraform-%EC%9D%B4%EB%9E%80
https://www.44bits.io/ko/keyword/terraform

- Terraform AWS
https://developer.hashicorp.com/terraform/tutorials/aws-get-started
https://terraform101.inflearn.devopsart.dev/cont/

- Terraform Azure 
https://developer.hashicorp.com/terraform/tutorials/azure-get-started
https://learn.microsoft.com/ko-kr/azure/developer/terraform/

- Terraform GCP 
https://developer.hashicorp.com/terraform/tutorials/gcp-get-started
https://cloud.google.com/docs/terraform/get-started-with-terraform

- Terraform Naver Cloud
https://docs.toast.com/ko/Compute/Instance/ko/terraform-guide/

- Terraform Etc
https://kim-dragon.tistory.com/249

########################################################
### Terraform Guide

# IaC(Infrastruction as Code)
코드를 이용해 인프라를 자동으로 구축, 관리, 프로비저닝하는 접근 방식
프로비저닝, 시스템 변경 및 구성에 대해 일관되게 반복되는 과정을 코드를 통해 자동화 하면 빠르게 변경/구성할 수 있으며, 
수동으로 구성 시 발생하는 누락 및 잘못 설정하는 등의 인적 실수를  방지 
인프라 구성을 코드로 처리하므로 애플리케이션 구성과의 경계가 좁아지면서 개발자와 운영자의 경계가 모호해진 요즘의 DevOps에서 많이 사용됨 

 # Iac 종류
- Provisioning Tool 
컴퓨터나 가상호스트를 사용해 라이브러리나 서비스등을 설치하는것을 의미 
ex) Terraform, Cloudformation

-SCM Tool
성능부터 H/W 속성과 라이프사이클 전반에  걸친  요구사항 설계 및 운영정보의 일관선을 유지하기 위한 시스템 프로세스 
ex) Chef Puppet Ansible

# Terraform
Terraform은 Hashicorp에서 오픈소스로 개발중인 클라우드 인프라스트럭처 자동화를 지향하는 코드로서의 인프라스트럭처Infrastructure as Code, IaC 도구
IaC는 코드로 인프라스트럭처를 관리한다는 개념으로 테라폼에서는 하시코프 설정 언어HCL, Hashicorp Configuration Language을 사용해 클라우드 리소스를 선언 아마존 웹 서비스Amazon Web Service가 자체적으로 만든 AWS CloudFormation의 경우 AWS만 지원하는 것과 달리 테라폼의 경우 Amazon Web Service, Google Cloud Platform, Microsoft Azure와 같은 주요 클라우드 서비스를 비롯한 다양한 클라우드 서비스들을 프로바이더 방식으로 제공
이를 통해 테라폼만으로 멀티 클라우드의 리소스들을 선언하고 코드로 관리하는 것도 가능

테라폼은 고Go 프로그래밍 언어로 개발 
테라폼 사용자는 HCL 언어로 클라우드 리소스를 정의하고 이 내용을 테라폼 CLI 애플리케이션(terraform)으로 자신의 클라우드 계정에 실제로 반영
API를 호출해 명령을 실행하는 절차적인 방법과 달리 HCL은 선언적으로 리소스를 정의하기 때문에 리소스를 정의하고 여러번 테라폼을 실행한다고 여러 개의 리소스가 만들어지지는 않음(멱등성) 테라폼을 사용하면 이 과정을 계획(plan)과 적용(apply) 단계로 나누어 진행 plan 서브 명령어를 사용하면 클라우드에 적용될 변화 사항을 보여주며 apply 서브 명령어는 이를 자신의 클라우드 계정에 실제로 적용


# 테라폼 기본 개념
* 프로비저닝
    어떤 프로세스나 서비스를 실행하기 위한 준비 단계
    프로바이더로는 aws, 구글 클라우드 플랫폼, 마이크로소프트 애저와 같은 범용 클라우드 서비스를 비롯해 깃허브, 
    데이터 도그와 같은 특정 기능을 제공하는 서비스, mysql, 도커와 같은 로컬 서비스를 지원

* Resource
    리소스란 특정 프로바이더가 제공해주는 조작 가능한 대상의 최소 단위

* Plan
    테라폼 프로젝트 디렉터리 아래의 모든 .tf 파일의 내용을 실제로 적용 가능한지 확인 하는 작업
    테라폼은 이를 terraform plan 명령어로 제공하며, 이를 명령어로 실행하면 어떤 리소스가 생성되고, 수정되고, 삭제될지 보여줌

* Apply
    테라폼 프로젝트 디렉터리 아래의 모든 .tf 파일의 내용대로 리소스를 생성, 수정, 삭제하는 일을 적용

