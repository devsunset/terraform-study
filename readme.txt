--------------------------------------------------------------------------------

			# TERRAFORM-WORK #

--------------------------------------------------------------------------------

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
https://hvho.github.io/2021-07-25/terraform-up-and-running-1

- Terraform
https://gurumee92.tistory.com/tag/%ED%85%8C%EB%9D%BC%ED%8F%BC
https://j-dev.tistory.com/search/Terraform?page=1
https://www.44bits.io/ko/keyword/terraform
https://www.44bits.io/ko/post/terraform_introduction_infrastrucute_as_code
https://j-dev.tistory.com/search/Terraform?page=1
https://velog.io/@borab/terraform-%EC%9D%B4%EB%9E%80
https://hvho.github.io/2021-08-29/terraform-up-and-running-2

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
	인프라 구성을 코드로 처리하므로 애플리케이션 구성과의 경계가 좁아지면서 개발자와 운영자의 경계가 모호해진 DevOps에서 많이 사용 

 * Iac 종류
	- 애드혹 스크립트 
	bash 스크립트 등을 서버에 직접 실행하는 방식

	- Provisioning Tool 
	컴퓨터나 가상호스트를 사용해 라이브러리나 서비스등을 설치하는것을 의미 
	ex) Terraform, Cloudformation

	- SCM Tool (구성 관리 도구)
	성능부터 H/W 속성과 라이프사이클 전반에  걸친  요구사항 설계 및 운영정보의 일관선을 유지하기 위한 시스템 프로세스 
	ex) Chef Puppet Ansible

	- 서버 템플릿 도구
	도커 등으로 서버 환경에 필요한 운영체제, 소프트웨어, 파일등을 모두 포함하고 있는 이미지(스냅숏)으로 관리하는 도구

	- 오케스트레이션 도구
	쿠버네티스 등으로 위 서버 템플릿 도구로 생성한 서버 스냅숏을 실제 인프라에 띄워 관리하는 도구

*  Iac 장점 
	- 자급식 배포
	자동 배포 파이프라인을 구성해 놓음으로써, 일부의 관리자 말고도 모든 개발자가 원할때 직접 배포 가능 

	- 속도와 안정성
	사람 대신 컴퓨터가 자동으로 배포하면 당연히 속도가 빨라지고 human error 가 발생할 소지가 적음 

	- 문서화
	소스파일 자체가 인프라에 대한 문서 역할

	- 버전관리
	인프라의 변경 내역을 git 과 같은 버전 관리 도구로 관리할 수 있음 

	- 유효성 검증
	인프라가 변경을 적용 전 정적 분석을 통해 오류를 미리 확인 가능 

	- 재사용성
	인프라 코드를 재사용 함으로써 비슷한 인프라에 대해서 재사용 가능 


# Terraform

	https://www.terraform.io/
	
	https://developer.hashicorp.com/terraform/docs

	Terraform은 Hashicorp에서 오픈소스로 개발중인 클라우드 인프라스트럭처 자동화를 지향하는 Infrastructure as Code, IaC 도구
	IaC는 코드로 인프라스트럭처를 관리한다는 개념으로 테라폼에서는 하시코프 설정 언어HCL, Hashicorp Configuration Language을
	사용해 클라우드 리소스를 선언 아마존 웹 서비스Amazon Web Service가 자체적으로 만든 AWS CloudFormation의 경우 
	AWS만 지원하는	것과 달리 테라폼의 경우 Amazon Web Service, Google Cloud Platform, Microsoft Azure와 같은 주요 
	클라우드 서비스를 비롯한 	다양한 클라우드 서비스들을 프로바이더 방식으로 제공
	이를 통해 테라폼만으로 멀티 클라우드의 리소스들을 선언하고 코드로 관리하는 것도 가능

	테라폼은 고Go 프로그래밍 언어로 개발 
	테라폼 사용자는 HCL 언어로 클라우드 리소스를 정의하고 이 내용을 테라폼 CLI 애플리케이션(terraform)으로 자신의 
	클라우드 계정에 실제로 반영
	API를 호출해 명령을 실행하는 절차적인 방법과 달리 HCL은 선언적으로 리소스를 정의하기 때문에 리소스를 정의하고 
	여러번 테라폼을 실행한다고 여러 개의 리소스가 만들어지지는 않음(멱등성) 테라폼을 사용하면 이 과정을 
	계획(plan)과 적용(apply) 단계로 나누어 진행 plan 서브 명령어를 사용하면 클라우드에 적용될 변화 사항을 보여주며 apply 
	서브 명령어는 이를 자신의 클라우드 계정에 실제로 적용


# Terraform 설치
	https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli	


# 테라폼 기본 개념
	* 프로비저닝
	    어떤 프로세스나 서비스를 실행하기 위한 준비 단계
	    프로바이더로는 aws, 구글 클라우드 플랫폼, 마이크로소프트 애저와 같은 범용 클라우드 서비스를 비롯해 깃허브, 
	    데이터 도그와 같은 특정 기능을 제공하는 서비스, mysql, 도커와 같은 로컬 서비스를 지원

	* Provider
	    Terraform 은 AWS, GCP, AZURE 등 여러 클라우드 인프라 환경을 지원하는데, 이렇게 클라우드 인프라 공급자 들이 Provider 

	* Resource
	    리소스란 특정 프로바이더가 제공해주는 조작 가능한 대상의 최소 단위
	    예를 들어 EC2 instance, LB( Load Balencer ), DNS( Domain Name Server ), RDS 등의 각 요소들

	* Plan
	    테라폼 프로젝트 디렉터리 아래의 모든 .tf 파일의 내용을 실제로 적용 가능한지 확인 하는 작업
	    테라폼은 이를 terraform plan 명령어로 제공하며, 이를 명령어로 실행하면 어떤 리소스가 생성되고, 수정되고, 삭제될지 보여줌

	* Apply
	    테라폼 프로젝트 디렉터리 아래의 모든 .tf 파일의 내용대로 리소스를 생성, 수정, 삭제하는 일을 적용

	* HCL
	    HCL ( Hashicorp Configuration Languate ) 는 Terraform 을 만든 제작사인 hashicorp 에서 만든 Terraform 전용 DSL
	    ( Domain Specific Language ) Terraform 의 설정 파일들은 HCL 로 기술되며, .tf 의 파일 확장자를 가짐 


# Terraform command
	 ⚡ root@localhost  ~  terraform -help
	Usage: terraform [global options] <subcommand> [args]

	The available commands for execution are listed below.
	The primary workflow commands are given first, followed by
	less common or more advanced commands.

	Main commands:
	  init          Prepare your working directory for other commands
	  validate      Check whether the configuration is valid
	  plan          Show changes required by the current configuration
	  apply         Create or update infrastructure
	  destroy       Destroy previously-created infrastructure

	All other commands:
	  console       Try Terraform expressions at an interactive command prompt
	  fmt           Reformat your configuration in the standard style
	  force-unlock  Release a stuck lock on the current workspace
	  get           Install or upgrade remote Terraform modules
	  graph         Generate a Graphviz graph of the steps in an operation
	  import        Associate existing infrastructure with a Terraform resource
	  login         Obtain and save credentials for a remote host
	  logout        Remove locally-stored credentials for a remote host
	  output        Show output values from your root module
	  providers     Show the providers required for this configuration
	  refresh       Update the state to match remote systems
	  show          Show the current state or a saved plan
	  state         Advanced state management
	  taint         Mark a resource instance as not fully functional
	  test          Experimental support for module integration testing
	  untaint       Remove the 'tainted' state from a resource instance
	  version       Show the current Terraform version
	  workspace     Workspace management

	Global options (use these before the subcommand, if any):
	  -chdir=DIR    Switch to a different working directory before executing the
	                given subcommand.
	  -help         Show this help output, or the help for a specified subcommand.
	  -version      An alias for the "version" subcommand.


# Terraform LifeCycle
	Terraform 으로 인프라를 프로비저닝 하는 일련의 작업은  계획(Plan)-적용(Apply)-삭제(Destroy) 의 과정

	------------------

	* 계획(Plan)
	테라폼을 통해 인프라 작업을 하면, 직접 콘솔을 통해 인프라를 변경시키는 것에 비해서 코드를 실제 환경하기 적용하기 전에 
	“검증” 단계를 거칠 수 있는 장점  콘솔로 작업하면 인프라가 바로 변경되지만, 코드로 작업하면 해당 코드를 환경에 적용하기 전 
	static validation 할 수 있음
	해당 단계를 테라폼은 계획 단계라고 하며, 해당 단계는 현재 적용되어 있는 리소스들의 상태와 코드를 적용 시켰을 때 변경될 
	리소스의 상태의 차이를 보여줌 	코드를 실제 환경에 적용하기 전, 코드의 변경점이 내가 의도한 변경사항이 맞는지 확인해 보는
	단계이고, 해당 명령어는 실제 환경에 영향을 주지 않기 때문에 내가 정확히 원하는 결과를 얻을 때 까지 반복해서 확인 가능 

	* 적용(Apply)
	코드의 변경 사항을 실제 환경에 적용시키는 단계
	적용이 성공한다면 변경 ( 추가 / 변경 / 삭제 ) 된 리소스의 정보가 출력되고, 만약 실패한다면 실패한 이유 출력 
	적용 명령은 멱등성(idempotent) 을 가지기 때문에 여러번 적용하여도 작성한 코드와 동일한 상태를 보장
	리소스 여러개를 생성하다 중간에 실패했을 경우에도 코드를 고쳐 다시 적용하면 이전에 만들어졋던 리소스는 알아서 처리

	* 삭제(Destory)
	모든 인프라를 삭제하는 명령어

	------------------

	* terraform import 
	운영중인 리소스를 참조해서 code화 시킬 수 있음 
	terraform(0.12.16)에서는 import 명령어를 사용하기 전에 빈 tf 파일이 존재해야 함 

	terraform import aws_instance.<resource name> <instance ID>

	import가 되었다면 .tfstate 파일이 업데이트 됨 (실행 폴더에 .tfstate 파일이 미존재시 새로 생성)
	import는 사용에 매우 유의

	테라폼은 apply시에 .tf 파일에는 없고 .tfstate 에만 있는 인프라 정보를 삭제
	만약 운영환경에서 모든 ec2를 import한 후  .tf파일을 생성하지 않은채  apply 할 경우 모든 운영환경이 destroy 됨 

	* terraform graph
	하나의 리소스에서 다른 리소스로 참조를 추가하면 내재된 종속성이 작성
	테라폼은 이러한 종속성 구문을 분석하여 그래프를 작성하고 이를 사용하여 리소스를 생성하는 순서를 자동으로 결정
	결과값으로는 DOT라는 언어로 되어 있으며, 그래프비즈 혹은 그래프비즈온라인(https://dreampuf.github.io/GraphvizOnline/) 
	같은 앱을 사용하면 그래프 이미지로 확인 가능 

	------------------

# Terraform work process
	0. provider 정보 생성 - AWS 계정, API 키 설정
	1. *.tf 작성 - HCL 언어로 필요한 리소스 선언(*.tf 생성)
	2. terraform init - 선언된 리소스들이 생성 가능한지 계획 확인
	3. terraform validate - 유효성 검사 
	4. terraform plan - 선언된 리소스들이 생성 가능한지 계획 확인
	5. terraform appply - 선언된 리소스들을 적용r
	6. terraform destory - 선언된 리소스 한번에 제거


# Terraform 변수 선언 예시 
	* 입력 변수 
	variable "NAME" {
		description = "<description>"
		default = <default>
		type = <type>
	}
	- description(Option) : 변수를 설명하는 변수
	- default(Option) : 변수에 값을 전달하는 여러가지 방법이 있는데 -var(명령줄), -var-file(파일), 
	‘TF_VAR_<variable_name>’(환경변수)를 통해 값을 전달
	만약 값이 전달되지 않으면 기본값을 할당 기본값이 없는 경우 테라폼은 사용자에게 변수에 대한 정보를 물음 
	- type(Option) : 변수의 유형을 지정
	string, number, bool, list, map, set, object, tuple등의 유형이 있음
	유형을 지정하지 않으면 any로 간주

	- ex) 변수에 값 전달 예시
		#명령줄
		$ terraform plan -var "server_port=8080"

		#환경변수
		$ export TF_VAR_server_port=8080
		$ terraform plan

	* 출력 변수 
	output "NAME" {
		value = "<value>"
		description = <description>
		senstive = <senstive>
	}

	- value : 출력하려는 값
	- description(Option) : 출력 변수를 설명하는 변수
	- senstive(Option) : 변수 출력 실행이 끝날때 기록하지 않도록 하려면 senstive를 true로 설정해야함 
	 출력 변수에 개인정보 등 민감한 데이터가 있을 시 유용

# Terraform 상태 / Backend
	해당 파일에는 테라폼을 실행 시 매핑되는 리소스들의 상태값을 가지고 있음 
	기본적으로 /terraform/test 폴더에서 테라폼을 실행하면 JSON 형태의 /terraform/testterraform.tfstate 파일을 생성
	상태파일은 프라이빗이며 직접 편집하거나 수정해서는 안됨 
	파일 상태를 조작해야 하는 경우 terraform import, terraform state 명령을 통해 조작


    테라폼을 사용하여 인프라를 업데이트하려면 각 팀원이 동일한 테라폼 상태 파일에 엑세스해야 하므로, 
    상태 파일을 공유 위치에 저장해야 합니다.
    두 팀원이 동시에 테라폼을 실행하는 경우 여러 테라폼 프로세스가 상태 파일을 동시에 업데이트하여 충돌을 일으킬 수 있습니다. 
    이러한 상태가 되면 데이터가 손실되거나 상태 파일이 손상될 수 있습니다.
    인프라를 변경할 때는 다른 환경을 격리하는 것이 가장 좋습니다. 예를 들어 테스트 환경을 변경할 경우 실수로 
    운영 환경이 중단되는 경우가 없는지 확인해야 합니다.


    * 상태 파일 공유
	테라폼의 상태 파일을 깃과 같은 형상관리 시스템에 공유하는 것은 다음과 같은 이유 때문에 부적절
	1. 변경 사항을 실행하고 나서 푸시하는 것을 누락 할 수 있음 
	2. 여러 명의 팀 구성원이 동시에 하나의 상태 파일에 apply 명령을 실행하지 못하게 하는 잠금 기능을 제공하지 않음
	3. 테라폼의 상태 파일은 모든 데이터를 평문으로 저장하기에 보안적으로 적절하지 않음

	위의 문제와 같은 상황을 해결하기 위해서는 테라폼에 내장된 원격 백엔드 기능을 사용하여 클라우드 스토리지에 저장하는 것이 좋음
	1. 원격 백엔드 구성 시 테라폼은 plan이나 apply 명령을 실행할 때마다 해당 백엔드에서 상태 파일을 자동으로 로드 
	apply 명령을 실행한 후에는 상태 파일을 백엔드에 자동 저장
	2. apply 명령을 실행 시 자동으로 잠금을 활성화 -lock-timeout=<TIME>을 사용하면 apply 명령을 실행할 때 잠금이
	 해제되기까지 테라폼이 얼마 동안 대기하도록 할지 설정
	3. 데이터를 보내거나 상태 파일을 저장할 때 암호화하는 기능을 지원


	테라폼 백엔드에는 몇 가지 단점 존재

	1. 2단계로 백엔드를 구성
	- 백엔드 구성 시
	    테라폼 코드를 작성하여 S3 버킷 및 다이나모DB 테이블을 생성하고 해당 코드를 로컬 백엔드와 함께 배포
	    테라폼 코드로 돌아가서 원격 백엔드 구성을 추가 새로 생성된 S3 버킷과 다이나모 DB 테이블을 사용하고,
	    init 명령을 실행하여 로컬 상태를 S3에 복사

	- 백엔드 삭제 시
	    백엔드 구성을 제거한 다음 init 명령을 실행하여 테라폼 상태를 로컬 디스크에 다시 복사
	    destroy 명령을 실행하여 S3 버킷 및 다이나모DB 테이블을 삭제


	2. 테라폼의 백엔드 블록에서는 변수나 참조를 사용할 수 없음 
	해당 단점의 유일한 해결책은 init 명령어 실행 시 -backend-config 옵션을 통해 변수를 전달하는 것 

 
	GCP 스토리지 백엔드 참조
	https://www.terraform.io/language/settings/backends/gcs

	AWS S3 백엔드 참조
	https://www.terraform.io/language/settings/backends/s3

	백엔드 구성 참조
	https://www.terraform.io/language/settings/backends/configuration


	* 상태 파일 격리
	하나의 환경에서 문제가 발생하더라도 다른 환경에 영향을 주지 않도록 상태 파일을 격리

	1.작업 공간을 통한 격리
	테라폼은 별도의 이름을 가진 여러 개의 작업 공간에 저장할 수 있음 
	테라폼은 default라는 기본 작업 공간에서 시작하며 작업 공간을 지정하지 않으면 기본 작업 공간을 사용


	# 테라폼 워크 스페이스를 생성합니다.
	$ terraform workspace new example1

	# 현재 사용중인 워크스페이스를 보여줍니다.
	$ terraform workspace show

	# 생성된 워크스페이스 목록을 보여줍니다.
	$ terraform workspace list

	# 워크스페이스를 전환할 수 있습니다.
	$ terraform workspace select <workspace name>

	워크스페이스 생성 후 적용 시 S3에는 ‘evn:’ 라는 폴더가 생성 되고, 각 워크스페이스 마다 각자의 상태 파일을 따로 보유 
	GCP에서는 백엔드에 지정한 경로에 워크스페이스 명.tfstate 파일이 생성

	위의 워크스페이스에는 몇 가지 단점이 있음 
	모든 작업 공간의 상태 파일이 동일한 스토리지에 저장
	terraform workspace 명령어를 실행하지 않으면 워크스페이스에 대한 정보를 알기가 어려움
	어떠한 워크스페이스에서 작업하는지 잊어버릴 수가 있어 실수를 할 수가 있음 

    2. 파일 레이아웃을 이용한 격리
	환경을 완전히 격리하려면  각 테라폼 구성 파일을 분리된 폴더에 위치 
	예를 들어 스테이징 환경의 대한 모든 구성은 stage 폴더에, 프로덕션 환경의 모든 구성은 prod 폴더에 위치 
    서로 다른 권한을 사용하여 다른 백엔드를 구성 예를 들어 각 환경은 각각 분리된 S3 버킷을 백엔드로 사용
	각 환경별 VPC, 서비스, 데이터 베이스 같은 각 구성 요소를 별도의 테라폼 폴더 혹은 별도의 상태 파일에서 사용하는 것을 권장 

	위와 같은 구성은 면에서 단점
	실수로 인한 인프라를 망가뜨리진 않겠지만 한 번의 명령으로 전체 인프라를 만들수 없음 
	위와 같은 구성에서는 각 구성 요소 각각에 apply 명령을 실행해야 함
	테라그런트를 사용하는 경우 apply-all 명령을 사용하여 이 프로세스를 자동화 할 수는 있음 
	다른 폴더에 있는 리소스를 직접 액세스 할 수 없어 리소스 종속성을 사용할 수 없음 


# Example

* AWS example.tf
---------------------------------------------------------------------------
provider "aws" {
  region     = "ap-northeast-2"
  access_key = "your_access_key"
  secret_key = "your_secret_key"
}

resource "aws_security_group" "node" {
  name          = "allow_node_js_and_ssh"
  description   = "Allow SSH and nodejs port from all"
  ingress {
    cidr_blocks = ["0.0.0.0/0"]
    protocol    = "tcp"
    from_port   = 22
    to_port     = 22
  }
  ingress {
    cidr_blocks = ["0.0.0.0/0"]
    protocol    = "tcp"
    from_port   = 3000
    to_port     = 3000
  }
}

data "aws_security_group" "default" {
  name = "default"
}

resource "aws_instance" "example" {
    ami             = "ami-0e17ad9abf7e5c818"
    instance_type   = "t2.micro"
    key_name        = "example"

    vpc_security_group_ids = [
      aws_security_group.node.id,
      data.aws_security_group.default.id
    ]

    provisioner "remote-exec" {
      connection {
        user        = "ec2-user"
        private_key = file("your/pem/key")
        host        = aws_instance.example.public_ip
      }

      inline = [
        "sudo amazon-linux-extras install epel -y",
        "sudo yum install --enablerepo=epel -y nodejs",
        "sudo wget https://your.helloworld.js.link -O /home/ec2-user/helloworld.js",
        "sudo wget https://your.helloworld.service.link -O /etc/systemd/system/helloworld.service",
        "sudo systemctl enable helloworld",
        "sudo systemctl start helloworld",
      ]
  }
}

* GCP example.tf  (Web server)
---------------------------------------------------------------------------
provider "google" {
  credentials = file("key.json")
  project = "terraform-348208"
  region = "asia-northeast3"
}

resource "google_compute_instance" "example" {
  name = "webserver"
  machine_type = "f1-micro"
  zone = "asia-northeast3-a"

  boot_disk {
    initialize_params {
      image = "gcr.io/google-containers/busybox"
    }
  }

  network_interface {
    network = "default"
    access_config {}
  }

  tags = ["web"]

  metadata_startup_script = <<-EOF
              #!/bin/bash
              echo "Hello, World" > index.html
              nohup busybox httpd -f -p 8080 &
              EOF
}

resource "google_compute_firewall" "default" {
  name    = "webserver-firewall"
  network = "default"

  allow {
    protocol = "tcp"
    ports    = ["8080"]
  }

  source_tags = ["web"]
  target_tags = ["web"]
}	

* AWS example.tf  (Web server)
---------------------------------------------------------------------------
provider "aws" {
  region = "us-east-2"
}

resource "aws_instance" "example" {
  ami                    = "ami-xxxxxxxxxxx"
  instance_type          = "t2.micro"
  vpc_security_group_ids = [aws_security_group.instance.id]

  user_data = <<-EOF
              #!/bin/bash
              echo "Hello, World" > index.html
              nohup busybox httpd -f -p 8080 &
              EOF

  tags = {
    Name = "terraform-example"
  }
}

resource "aws_security_group" "instance" {

  name = var.security_group_name

  ingress {
    from_port   = 8080
    to_port     = 8080
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
}

variable "security_group_name" {
  description = "The name of the security group"
  type        = string
  default     = "terraform-example-instance"
}

output "public_ip" {
  value       = aws_instance.example.public_ip
  description = "The public IP of the Instance"
}


* AWS example.tf  (변수 선언 예시)
---------------------------------------------------------------------------
variable "number_example" {
  description = "An example of a number variable in Terraform"
  type        = number
  default     = 42
}

variable "list_example" {
  description = "An example of a list in Terraform"
  type        = list
  default     = ["a", "b", "c"]
}

variable "list_numeric_example" {
  description = "An example of a numeric list in Terraform"
  type        = list(number)
  default     = [1, 2, 3]
}

variable "map_example" {
  description = "An example of a map in Terraform"
  type        = map(string)

  default = {
    key1 = "value1"
    key2 = "value2"
    key3 = "value3"
  }
}

variable "object_example" {
  description = "An example of a structural type in Terraform"
  type        = object({
    name    = string
    age     = number
    tags    = list(string)
    enabled = bool
  })

  default = {
    name    = "value1"
    age     = 42
    tags    = ["a", "b", "c"]
    enabled = true
  }
}


* GCP example.tf  (스토리지 생성 리소스)
---------------------------------------------------------------------------
provider "google" {
  credentials = file("key2.json")
  project = "terraform-348208"
  region = "asia-northeast3"
}

resource "random_id" "instance_id" {
  byte_length = 8
}

resource "google_storage_bucket" "terraform_state" {

  # 버킷 이름
  name = "terraform-up-and-running-state-${random_id.instance_id.hex}"

  # 버킷을 삭제할 때 해당 버킷에 포함된 모든 객체를 삭제합니다.
  force_destroy = true

  location = "ASIA"

  storage_class = "Standard"

  # 실수로 S3 버킷을 삭제하는 것을 방지합니다.(생명주기 설정)
  lifecycle {
    prevent_destroy = true
  }

  # 코드 이력을 관리하기 위해 상태 파일의 버전 관리를 활성화합니다.
  versioning {
    enabled = false
  }

  // GCP는 스토리지 디폴트가 암호화

}

terraform {
  backend "gcs" {
    bucket = "terraform-up-and-running-state-0d9027ef04cb8b9b"
    credentials = "key2.json"
  }
}

* AWS example.tf  (S3 생성 리소스)
---------------------------------------------------------------------------
provider "aws" {
  region = "us-east-2"
}

resource "aws_s3_bucket" "terraform_state" {

  bucket = var.bucket_name

  // This is only here so we can destroy the bucket as part of automated tests. You should not copy this for production
  // usage
  force_destroy = true

  # 상태 파일의 이력관리를 위해
  # 버전관리 기능을 활성화 합니다.
  versioning {
    enabled = true
  }

  # Enable server-side encryption by default
  server_side_encryption_configuration {
    rule {
      apply_server_side_encryption_by_default {
        sse_algorithm = "AES256"
      }
    }
  }
}

resource "aws_dynamodb_table" "terraform_locks" {
  name         = var.table_name
  billing_mode = "PAY_PER_REQUEST"
  hash_key     = "LockID"

  attribute {
    name = "LockID"
    type = "S"
  }
}