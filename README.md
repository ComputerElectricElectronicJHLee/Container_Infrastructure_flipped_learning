# Container_Infrastructure_flipped_learning
CI/CD 관련 이론을 위한 공간입니다. (쿠버네티스, 도커, 젠킨스, 프로메테우스, 그라파나 등)

---
# 목차
- 1. 컨테이너 인프라 환경
- 2. 테스트 환경
- 3. 쿠버네티스
- 4. 도커
- 5. 젠킨스
- 6. 프로메테우스 및 그라파나
---
# 내용

※주로 참고 도서 : 컨테이너 인프라 환경 구축을 위한 쿠버네티스/도커

### 1. 컨테이너 인프라 환경

- 엔지니어가 개발 환경을 구축하면 사용자(개발자)는 그에 맞는 Tool을 모두 설치해야 했던 On-premises 환경은 이제 구 시대 환경

- 이미 구성된 환경을 사용자(개발자)가 필요에 따라 선택 및 조합하여 사용할 수 있는 IaaS 환경이 대두되고 있음

- 기존 계획 단계에서 설계 및 환경을 완전히 구비한 후 예정된 목표를 달성하는 폭포수 방법론

- 애자일(Agile) 방법론은 일정 주기를 정한 다음 해당 주기에 맞춰 요구 사항을 충족시키는 Proto 타입을 만들고 개선하여 최종 목표에 점진적으로 접근

- 이를 위해 인프라는 다음과 같이 변화하고 있음

  - 사용자(개발자)가 요구하는 인프라를 즉시 제공하는 기능 유지
  
  - 사용자(개발자)마다 독립적인 환경에서 개발해도 모두 동일한 결과를 도출 가능
  
  - 개발된 SW의 성능 보장 및 인프라 가용 리소스를 최대한 확보 가능

- 컨테이너는 하나의 운영 체제 커널에서 다른 프로세스에 영향을 받지 않고 독립적으로 실행되는 프로세스 상태

- 컨테이너는 가상화 상태에서 동작하는 프로세스보다 가볍고 빠르게 동작

#### <모놀리식 아키텍처와 마이크로 서비스 아키텍처>

<img src="https://user-images.githubusercontent.com/101415950/196708479-94084c8b-e211-41ac-9583-0c56c9c744fb.png" width="80%" height="80%">
(출처 : https://blog.lgcns.com/1278)

- 모놀리식 아키텍처
	
	- 하나의 큰 목적이 있는 서비스 또는 애플리케이션에 여러 기능이 통합된 구조
	
	- 하나의 결합된 코드로 구성되므로 초기 단계에서 설계하기 용이
	
	- 개발이 좀 더 단순하고 코드 관리가 간편
	
	- 운영하는 과정에서 수정이 많을 경우, 결합도가 높아 하나의 서비스 수정이 다른 서비스에 영향끼칠 수 있음

	- 소규모 프로젝트에 적합

- 마이크로 서비스 아키텍처

	- 개별 기능을 하는 작은 서비스를 각각 개발하여 연결하는 방식으로 각 서비스가 독립적으로 동작할 수 있음

	- 개발한 서비스 재활용 용이
	
	- 서비스 수정 시 다른 서비스에 영향을 끼칠 가능성이 적어 사용량 변환에 따라 특정 서비스 확장 가능

	- 사용자의 요구 사항에 따라 가용성을 즉각적으로 확보해야 하는 IaaS 환경에 적합

	- 모놀리식 아키텍처에 비해 복잡도가 높고 각 서비스가 서로 유기적으로 통신하는 구조이므로 네트워크를 통한 호출 횟수가 증가   
	  => 성능에 영향

	- 대규모 프로젝트에 적합

#### <컨테이너 인프라 환경 지원 도구>

- 컨테이너 인프라 환경은 컨테이너, 컨테이너 관리, 개발 환경 구성 및 배포 자동화, 모니터링으로 구성

- 도커

	- 컨테이너 환경에서 독립적으로 애플리케이션을 실행할 수 있도록 컨테이너를 만들고 관리하는 것을 지원

	- 운영체제 환경 관계없이 독립적인 환경에서 일관적인 결과 보장

- 쿠버네티스

	- 다수의 컨테이너 관리에 사용

	- 컨테이너 자동 배포, 배포된 컨테이너에 대한 동작 보증, 부하에 따른 동적 확장 등 기능 제공
	
	- 컨테이너 인프라에 필요한 기능을 통합하고 관리하는 솔루션

	- 컨테이너 인프라를 기반으로 다양한 서비스를 효율적으로 관리하는 환경 제공
	
	- 내외부와 유연하게 연결하는 역할

- 젠킨스

	- 빌드, 테스트, 패키지화, 배포 단계 모두 자동화하여 계발 단계를 표준화하는 CI/CD 제공
	
	- 개발된 코드의 빠른 적용과 효과적인 관리를 통해 개발 생산성을 높이는 데 초점이 맞춰져 있음

	- 단일 기능을 빠르게 개발해 적용해야 하는 환경에 적합(=컨테이너 인프라 환경)

- 프로메테우스 및 그라파나

	- 모니터링을 위한 도구

	- 프로메테우스는 상태 데이터를 수집

	- 그라파나는 프로메테우스로 수집한 데이터를 시각화

	- 컨테이너 인프라 환경에서 많은 종류의 소규모 기능이 각각 나누어 개발되기 때문에 중앙 모니터링이 필요

	- 프로메테우스 및 그라파나는 컨테이너로 패키징이 되어 동작하며 최소환의 자원으로 쿠버네티스 클러스터 상태를 시작적으로 표현

---
### 2. 테스트 환경 구성

- 코드형 인프라

	- 코드로 하드웨어를 설정 후 운영체제 설치 및 네트워크 구성하여 개발환경 구층

	- 코드로 인프라를 소프트웨어처럼 다룸

- 버추얼 박스

	- 가상화 소프트웨어

	- 다운로드 링크 : https://www.virtualbox.org/wiki/Download_Old_Builds_6_1 (6.1.12버전)

	- 모두 기본상태로 next 클릭 후 설치 완료

- 베이그런트

	- 프로비저닝(provisioning) 기능 수행
	
		- 사용자의 요구에 맞게 시스템 자원을 할당, 배치, 배포

		- 필요할 때 시스템을 사용할 수 있는 상태로 변경

	- 다운로드 링크 : https://www.vagrantup.com/downloads (2.2.9버전)

	- 모두 기본상태로 next 클릭 후 설치 완료

	- vagrant init : 프로비저닝을 위한 기초 파일 생성

	- vagrant up : Vagrantfile을 읽어 프로비저닝 진행
	
	- vagrant halt : 베이그런트에서 다루는 가상 머신 종료
	
	- vagrant destroy : 베이그런트에서 관리하는 가상 머신 삭제
	
	- vagrant ssh : 베이그런트에서 관리하는 가상 머신에 ssh로 접속

	- vagrant provision : 베이그런트에서 관리하는 가상 머신에 변경된 설정 적용

#### <Tool 정상 동작 확인>

- 먼저 프로비저닝을 위한 코드 작성 후 베이그런트에서 호출한 뒤 버추얼 박스에 운영 체제 설치

- 베이그런트 설치 디렉터리(c:\HashiCorp)에 프로비저닝을 위한 코드 작성 권장

1. 명령 프롬프트에서 베이그런트 설치 디렉터리로 이동 후 베이그런트 초기화(프로비저닝을 위한 기초 파일 생성)

```
cd c:\HashiCorp
vagrant init
```

2. 생성된 베이그런트 스크립트 파일(Vagrantfile)을 IDE 등을 통해 실행 후 config.vm.box = "base"라는 내용있는지 확인   
   => 가상머신의 이미지를 의미, 기본값으로 base가 지정, 이를 변경하여 가상머신 지정

3. 명령 프롬프트에서 vagrant up 실행하면 base이미지를 찾지 못하여 에러 발생

```
cd c:\HashiCorp
vagrant up
```

4. https://app.vagrantup.com/boxes/search 에 접속하여 sysnet4admin을 입력   
   (컨테이너 인프라 환경 구축을 위한 쿠버네티스/도커 저자의 파일)

5. sysnet4admin/CentOS-k8s를 확인 (https://app.vagrantup.com/sysnet4admin/boxes/CentOS-k8s)

6. Vagrantfile에서 config.vm.box = "base"를 config.vm.box = "sysnet4admin/CentOS-k8s"으로 변경 후 저장

```
config.vm.box = "sysnet4admin/CentOS-k8s"
```

7. 명령 프롬프트에서 vagrant up 실행하여 가상 머신 이미지 내려받는지 확인   
   (Vagrant was unable to mount VirtualBox shared folders 에러 무시, 게스트 에디션이 설치되지 않아 발생)
   
8. 버추얼 박스를 실행하여 가상 머신 제대로 생성되었는지 확인

```
cd c:\HashiCorp
vagrant ssh
[vagrant@k8s ~]$
```

9. CentOS의 실행 시간(uptime)과 운영 체제의 종류(cat/etc/redhat-release)를 확인

``
[vagrant@k8s ~]$ uptime
[vagrant@k8s ~]$ cat/etc/redhat-release
``

10. 설치 테스트 완료 후 가상 머신 삭제

``
[vagrant@k8s ~]$ exit
vagrant destroy -f
``

#### <베어그런트로 테스트 환경 구축>

Vagrantfile을 수정하여 원하는 구성이 자동으로 CentOS에 입력되도록 수행

1. Vagrantfile을 아래와 같이 수정

```
#do |이름|으로 시작한 작업은 end로 종료
#Providier는 베이그런트를 통해 제공되는 코드가 실제로 가상 머신으로 배포되게 하는 소프트웨어
#auto_correct:true는 포트가 중복되면 포트가 자동으로 변경

# -*- mode: ruby -*- #루비(ruby) 언어임을 인식하는 호환 코드
# vi: set ft=ruby : #ft는 파일 종류(file type)의 약자
Vagrant.configure("2") do |config| #"2"는 API 버전, do |config|는 베어크런드 설정의 시작
 config.vm.define "m-k8s" do |cfg| #가상머신을 "m-k8s"로 정의, do |cfg|를 추가해 원하는 설정으로 변경
 config.vm.box = "sysnet4admin/CentOS-k8s" #do |cfg|에서 적용한 내용을 받아 cfg.vm.box로 변경
  cfg.vm.provider "virtualbox" do |vb| #Provider를 버추얼박스로 정의, 버추얼 박스에 필요한 설정을 정의하기 위해 do |vb| 추가
   vb.name="m-k8s(github_SysNet4Admin)" #가상머신 이름
   vb.cpus=2 #CPU 수
   vb.memory=2048 #메모리 크기
   vb.customize ["modifyvm",:id, "--groups","/k8s-SM(github_SysNet4Admin)"] #소속된 그룹 명시
  end
  cfg.vm.host_name="m-k8s" #가상머신 자체 설정으로 호스트이름 설정
  cfg.vm.network "private_network",ip:"192.168.1.10" #호스트 전용 네트워크를 private_network로 설정, eth1 인터페이스를 Host-Only로 구성하고 IP 지정
  cfg.vm.network "forwarded_port", guest:22, host:60010, auto_correct:true, id:"ssh" #ssh통신은 호스트 60010번을 게스트 22번으로 전달되도록 구성
  cfg.vm.synced_folder "../data","/vagrant", disabled:true #호스트(PC)와 게스트(가상 머신) 사이에 디렉터리 동기화가 이루어지지 않게 disabled:true 설정
 end #들여쓰기 위치 정확하게
end
```

- ssh 서비스의 기본 포트 번호인 22번을 id: "ssh"로 설정하지 않으면 중복된 두개의 포트로 설정

- 자기 자신(127.0.0.1/localhost)의 2222번 포트로 오는 내용과 모든 IP(0.0.0.0)의 60010 포트에서 오는 내용을 게스트의 22번으로 포워딩

```
vagrant port
	22(guest) => 2222(host)
	22(guest) => 60010(host)

netstat -an | findstr 2222
netstat -an | findstr 60010
```

- 명시적으로 좋지 않고 설정의 낭비를 줄이기 위해 왠만하면 id: "ssh"를 사용하는 것이 나음

2. 코드 실행

- 명령 프롬프트에 vagrant up 명령 실행 후 새로운 호스트 전용 네트워크를 설정하는 메시지에서 모두 허용 처리

- vagrant ssh 명령 실행하여 가상 머신(CentOS) 접속

- CentOS에서 ip addr show eth1 명령을 입역하여 IP(192.168.1.10) 설정 확인

- exit를 이용하여 CentOS 종료

```
cd c:\HashiCorp
vagrant up
vagrant ssh
[vagrant@k8s ~]$ ip addr show eth1
[vagrant@k8s ~]$ exit
```

- 호스트 전용 네트워크가 정상적으로 동작하지 않는 경우

	- 버추얼박스에서 파일>호스트 네트워크 관리자 선택

	- 속성 클릭 후 DHCP 서버를 사용하지 않도록 체크를 해제, IPv4 주소에 198.168.1.1 입력


## 마크다운 언어 참조
https://gist.github.com/ihoneymon/652be052a0727ad59601
