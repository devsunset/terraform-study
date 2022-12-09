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

- Terraform AWS
https://terraform101.inflearn.devopsart.dev/cont/

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
테라폼은 하시코프에서 Go 언어로 개발되고 있는 오픈소스 IaC(Infrastructure as Code) 도구
HCL(Hashcorp Configuration Language)을 사용해 클라우드 리소스를 선언하며 AWS, GCP, Azure와 같은 
주요 클라우드 서비스를 비롯한 다양한 클라우드 서비스들을 프로바이더 방식으로 제공

