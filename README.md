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

- vagrant init으로 생성 후 바로 vagrant up 실행하면 Vagrantfile이 config.vm.box = "base"로 설정되어 있어 base이미지를 찾지 못하여 에러 발생

- config.vm.box = "base"를 config.vm.box = "sysnet4admin/CentOS-k8s"으로 변경 후 저장하여 이미지 설정 필요

#### <베어그런트로 테스트 환경 구축>

Vagrantfile을 수정하여 원하는 구성이 자동으로 CentOS에 입력되도록 수행

[Vagrantfile 예시 코드]
```
#do |이름|으로 시작한 작업은 end로 종료
#Providier는 베이그런트를 통해 제공되는 코드가 실제로 가상 머신으로 배포되게 하는 소프트웨어
#auto_correct:true는 포트가 중복되면 포트가 자동으로 변경

# -*- mode: ruby -*-				 	#루비(ruby) 언어임을 인식하는 호환 코드
# vi: set ft=ruby :				 	#ft는 파일 종류(file type)의 약자

Vagrant.configure("2") do |config|		 	#"2"는 API 버전, do |config|는 베이그런드 설정의 시작
  N = 3 # max number of worker nodes			#쿠버네티스에서 작업을 수행할 worker node 수 설정(args: N을 통해 넘길 수 있음)
  Ver = '1.18.4' # Kubernetes Version to install	#쿠버네키스 버전을 변수로 설정

  #=============#
  # Master Node #
  #=============#

    config.vm.define "m-k8s" do |cfg|			#가상머신을 "m-k8s"로 정의, do |cfg|를 추가해 원하는 설정으로 변경
      cfg.vm.box = "sysnet4admin/CentOS-k8s"		#do |cfg|에서 적용한 내용을 받아 cfg.vm.box로 변경
      cfg.vm.provider "virtualbox" do |vb|		#Provider를 버추얼박스로 정의, 버추얼 박스에 필요한 설정을 정의하기 위해 do |vb| 추가
        vb.name = "m-k8s(github_SysNet4Admin)"		#가상머신 이름
        vb.cpus = 2					#CPU 수
        vb.memory = 3072				#메모리 크기
        vb.customize ["modifyvm", :id, "--groups", "/k8s-SgMST-1.13.1(github_SysNet4Admin)"]	#소속된 그룹 명시
      end						#들여쓰기 위치 정확하게
      cfg.vm.host_name = "m-k8s"			#가상머신 자체 설정으로 호스트이름 설정
      cfg.vm.network "private_network", ip: "192.168.1.10"	#호스트 전용 네트워크를 private_network로 설정, eth1 인터페이스를 Host-Only로 구성하고 IP 지정
      cfg.vm.network "forwarded_port", guest: 22, host: 60010, auto_correct: true, id: "ssh"	#ssh통신은 호스트 60010번을 게스트 22번으로 전달되도록 구성
      cfg.vm.synced_folder "../data", "/vagrant", disabled: true	#호스트(PC)와 게스트(가상 머신) 사이에 디렉터리 동기화가 이루어지지 않게 disabled:true 설정
      cfg.vm.provision "shell", path: "config.sh", args: N	#vm.provision "shell" 구문으로 경로에 있는 파일("config.sh")을 게스트(CentOS) 내부에서 호출하여 실행
      cfg.vm.provision "shell", path: "install_pkg.sh", args: [ Ver, "Main" ]	#변수 Ver, 문자 "Main"을 install_pkg.sh로 넘김
      cfg.vm.provision "shell", path: "master_node.sh"	#쿠버네티스 Master Node를 위한 "master_node.sh" 코드 추가
    end

  #==============#
  # Worker Nodes #
  #==============#

  (1..N).each do |i|					#1에서 3까지 반복하는 반복문으로 (1..N).each로 이루어짐
    config.vm.define "w#{i}-k8s" do |cfg|		#해당 값은 |i|를 통해 #{i}로 치환하여 사용
      cfg.vm.box = "sysnet4admin/CentOS-k8s"
      cfg.vm.provider "virtualbox" do |vb|
        vb.name = "w#{i}-k8s(github_SysNet4Admin)"
        vb.cpus = 1
        vb.memory = 2560
        vb.customize ["modifyvm", :id, "--groups", "/k8s-SgMST-1.13.1(github_SysNet4Admin)"]
      end
      cfg.vm.host_name = "w#{i}-k8s"
      cfg.vm.network "private_network", ip: "192.168.1.10#{i}"
      cfg.vm.network "forwarded_port", guest: 22, host: "6010#{i}", auto_correct: true, id: "ssh"
      cfg.vm.synced_folder "../data", "/vagrant", disabled: true
      cfg.vm.provision "shell", path: "config.sh", args: N
      cfg.vm.provision "shell", path: "install_pkg.sh", args: Ver
      cfg.vm.provision "shell", path: "work_nodes.sh"	#쿠버네티스 Worker Node를 위한 "work_node.sh" 코드 추가
    end
  end
end
```

[config.sh 예시 코드]
```
#!/usr/bin/env bash

# vim configuration 
echo 'alias vi=vim' >> /etc/profile			#vi를 호출하면 vim을 호출(코드에  하이라이트를 넣어 코드를 쉽게 구분하기 위함)

# swapoff -a to disable swapping
swapoff -a						#스왑되지 않도록 설정(쿠버네티스 설치 요구 조건을 충족하기 위해)
# sed to comment the swap partition in /etc/fstab
sed -i.bak -r 's/(.+ swap .+)/#\1/' /etc/fstab		#시스템이 다시 시작되더라도 스왑되지 않도록 설정

# kubernetes repo
gg_pkg="packages.cloud.google.com/yum/doc" # Due to shorten addr for key #리포지터리를 설정하기 위한 경로를 변수로 처리(간략화)
cat <<EOF > /etc/yum.repos.d/kubernetes.repo 		#쿠버네티스를 내려받을 리포티터리 설정 시작
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=0
repo_gpgcheck=0
gpgkey=https://${gg_pkg}/yum-key.gpg https://${gg_pkg}/rpm-package-key.gpg
EOF							#쿠버네티스를 내려받을 리포티터리 설정 끝

# Set SELinux in permissive mode (effectively disabling it)
setenforce 0						#selinux가 제한적으로 사용되지 않도록 permissive 모드로 변경
sed -i 's/^SELINUX=enforcing$/SELINUX=permissive/' /etc/selinux/config

# RHEL/CentOS 7 have reported traffic issues being routed incorrectly due to iptables bypassed
cat <<EOF >  /etc/sysctl.d/k8s.conf			#브리지 네트워크를 통과하는 IPv4와 IPv6의 패킷을 iptables가 관리하게 설정
net.bridge.bridge-nf-call-ip6tables = 1			#Pod(쿠버네티스에서 실행되는 객체의 최소 단위)의 통신을 iptables로 제어
net.bridge.bridge-nf-call-iptables = 1			#필요에 따라 IPVS 같은 방식으로 구성
EOF
modprobe br_netfilter					#br_netfilter 커널 모듈을 사용하여 브리지로 네트워크를 구성
							#IP 마스커레이드를 사용하여 내부 네트워크랑 외부 네트워크를 분리
							#IP 마스커레이드는 커널에서 제공하는 NAT 기능을 의미
							#br_netfilter 적용함으로써 iptables이 활성화

# local small dns & vagrant cannot parse and delivery shell code.
echo "192.168.1.10 m-k8s" >> /etc/hosts			#쿠버네티스 안에서 노드 간 통신을 이름으로 할 수 있게 하기 위한 구문
for (( i=1; i<=$1; i++  )); do echo "192.168.1.10$i w$i-k8s" >> /etc/hosts; done	#각 노드의 호스트 이름과 IP를 /etc/hosts에 설정
							#이때 Worker Node는 넘겨받은 N변수에 맞게 동적으로 생성됨
# config DNS  
cat <<EOF > /etc/resolv.conf				#외부와 통신할 수 있는 DNS 서버 지정
nameserver 1.1.1.1 #cloudflare DNS
nameserver 8.8.8.8 #Google DNS
EOF
```

[install_pkg.sh 예시 코드]

```
#!/usr/bin/env bash

# install packages 
yum install epel-release -y
yum install vim-enhanced -y
yum install git -y					#깃허브에서 코드를 내려받을 수 있게 Git을 설치

# install docker 
yum install docker -y && systemctl enable --now docker	#쿠버네티스를 관리하는 컨테이너를 설치하기 위해 도커를 설치하고 구동

# install kubernetes cluster 
yum install kubectl-$1 kubelet-$1 kubeadm-$1 -y		#넘겨받은 버전의 kubectl, kubelet, kubeadm 설치
systemctl enable --now kubelet				#kubelet 시작

# git clone _Book_k8sInfra.git 
if [ $2 = 'Main' ]; then				#전체 실행 코드를 Master Node에만 내려받도록 설정($2는 두번 째로 넘겨받은 값)
  git clone https://github.com/sysnet4admin/_Book_k8sInfra.git	#Git에서 코드를 내려받음
  mv /home/vagrant/_Book_k8sInfra $HOME			#내려받은 코드를 홈디렉터리(/root)로 옮김
  find $HOME/_Book_k8sInfra/ -regex ".*\.\(sh\)" -exec chmod 700 {} \;	#배시 스크립트(.sh)를 find로 찾아 바로 실행가능한 상태가 되도록 chmod 700 설정
fi
```

[master_node.sh 예시 코드]
```
#!/usr/bin/env bash

# init kubernetes 					#kubeadm을 통해 쿠버네티스 worker node를 받아들일 준비를 함
kubeadm init --token 123456.1234567890123456 --token-ttl 0 \	#토큰을 123456.1234567890123456로 지정하고 유지되는 시간(time to live)을 0으로 설정(기본 값인 24시간 후에 토큰이 계속 유지)
--pod-network-cidr=172.16.0.0/16 --apiserver-advertise-address=192.168.1.10	#Worker Node가 정해진 토큰에 들어오게 함
							#쿠버네티스가 자동으로 컨테이너에 부여하는 네트워크를 172.16.0.0/16(176.16.0.1 ~ 172.16.255.254)으로 제공
							#Worker Node에 접속하는 API 서버의 IP를 192.168.1.10으로 지정(Worker Node들이 자동으로 API 서버에 연결)
# config for master node only 
mkdir -p $HOME/.kube					#Master Node에서 현재 사용자가 쿠버네티스를 정상적으로 구동할 수 있게 하는 구문
cp -i /etc/kubernetes/admin.conf $HOME/.kube/config	#설정 파일을 루트의 홈디렉터리(/root)에 복사
chown $(id -u):$(id -g) $HOME/.kube/config		#쿠버네티스를 이용할 사용자에게 권한 부여

# config for kubernetes's network 
kubectl apply -f \					#CNI(컨테이너 네트워크 인터페이스)인 Calico의 설정을 적용해 쿠버네티스의 네트워크를 구성
https://raw.githubusercontent.com/sysnet4admin/IaC/master/manifests/172.16_net_calico.yaml
```

[work_nodes.sh 예시 코드]
```
#kubeadm을 이용하여 Master Node에 접속
#접속 시 연결에 필요한 토큰은 기존 Master Node에서 생성한 123456.1234567890123456 사용
#간단히 구성하기 위해 --discovery-token-unsafe-skip-ca-verification으로 인증 무시
#API 서버 주소인 192.168.1.10으로 기본 포트 번호인 6443 포트에 접속하도록 설정

#!/usr/bin/env bash

# config for work_nodes only 
kubeadm join --token 123456.1234567890123456 \
             --discovery-token-unsafe-skip-ca-verification 192.168.1.10:6443
```

#### <id: "ssh"로 설정하는 이유>

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

#### <호스트 전용 네트워크가 정상적으로 동작하지 않는 경우>

- 최대 절전 모드나 여러 차례 가상 머신을 다시 시작하는 경우에 호스트 전용 네트워크가 정상적으로 동작하지 않을 수 있음

- 버추얼박스에서 파일>호스트 네트워크 관리자 선택

- 속성 클릭 후 DHCP 서버를 사용하지 않도록 체크를 해제, IPv4 주소에 198.168.1.1 입력

#### <vi(visual editor)와 Vim(visual editor improved)>

- vi는 유닉스 환경에서 사용되는 텍스트 편집기(editor)

- vi와 Vim의 가장 큰 차이점은 Vim은 화살표로 커서가 이동하지만, vi는 H, J, K, L로 커서를 이동

#### <PuTTY와 SuperPuTTY>

- 명령 프롬프트(Command Prompt, cmd.exe)로 가상 머신에 접근할 수 있지만 가상머신마다 각각 명령어를 통해 접근해야 하므로 불편함

- PuTTY는 터미널 접속 프로그램으로 가볍고 다양한 플러그인을 통해 여러 대의 가상 머신에 접근할 수 있음

- 접속 정보를 저장하고 바로 불러와 실행할 수 있는 기능

- 한 번에 한 대씩만 접근 가능

- https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html 링크의 Alternative binary files 항목에서 다운로드

- SuperPuTTY는 한 번에 여러 대의 가상 머신에 접근하여 분할된 창을 통해 관리

- https://github.com/jimradford/superputty/releases 에서 다운로드

- SuperPuTTY 사용 시 putty.exe 위치를 지정하여 사용

#### <127.0.0.1로 접속하는 이유>

- 192.168.1.0/24 영역대로 가상 머신의 IP를 설정하는 경우

- 현업에서는 데이터 통신과 관리 네트워크를 분리해 사용하는 데 이와 비슷하게 관리 네트워크를 분리

- 192.168.1.0/24에서 문제가 발생해도 접속하는 데 문제가 없음

- 각 가상 머신은 베이그런트에서 NAT로 사용하는 eth0에 고유 포트 포워딩 규칙이 적용 ("forwarded_port", guest: 22, host: 60010)

---
### 3. 쿠버네티스

#### <컨테이너 인프라 환경>

<img src="https://user-images.githubusercontent.com/101415950/197549006-3059f673-f0a2-40b0-8f5b-2f48abeda60f.png" width="80%" height="80%">

- 리눅스 운영 체제의 커널 하나에서 여러 개의 컨테이너가 격리된 상태로 실행되는 인프라 환경

- 컨테이너는 하나 이상의 목적을 위해 독립적으로 작동하는 프로세스

- 개인 환경에서는 1명의 관리자(사용자)가 다양한 응용프로그램을 사용하므로 각각의 프로그램을 컨테이너로 구현할 필요 없음

- 기업 환경에서는 다수의 관리자가 수천 대의 서버를 함께 관리하므로 일관성 유지를 위해 컨테이너 필요

- 여러 사람이 조작하여 설정의 일관성이 떨어진 눈송이 서버를 방지하는 효과

- 가상화 환경에서 각각의 가상 머신이 모두 독립적인 운영체제 커널을 가지고 있어야 하므로 자원을 더 소모하고 성능이 떨어짐

- 컨테이너 인프라 환경은 커널 하나에 컨테이너 여러 개가 격리된 형태로 실행되므로 자원을 효율적으로 사용하고   
  수행해야 하는 단계도 적어 속도 빠름

<img src="https://user-images.githubusercontent.com/101415950/197551826-c1ad029c-920d-4d69-bc39-79f307d38411.png" width="80%" height="80%">
(출처 : https://www.alibabacloud.com/ko/knowledge/difference-between-container-and-virtual-machine)

#### <쿠버네티스(k8s) 정의>

- 쿠버네티스는 컨테이너 오케스트레이션(Orchestration)을 위한 솔루션

- 오케스트레이션은 복잡한 단계를 관리하고 요소들의 유기적인 관계를 미리 정의하여 손쉽게 사용하도록 서비스를 제공하는 것

- 즉 다수의 컨테이너를 유기적으로 연결, 실행, 종료 그리고 상태 추적 및 보존 등 컨테이너를 안정적으로 사용할 수 있게 만들어주는 솔루션

- 이와 비슷한 솔루션은 도커 스웜(소규모 환경에 유용), 메소스(분산 관리 시스템과 연동 필요), 노매드(Consul, Vault 연동)가 있음

#### <쿠버네티스(k8s) 구성 방법>

- 관리형 쿠버네티스
	
	- Public Cloud 업체에서 제공
	
	- EKS(Amazon Elastic Kubernetes Service), AKS(Azure Kubernetes Service), GKE(Google Kubernetes Engine)이 속함
	
	- 구성이 이미 다 갖춰져 있고 Master Node를 클라우드 업체에서 관리

- 설치형 쿠버네티스

	- Suse의 Rancher, RedHat의 Openshift와 같은 플랫폼에서 제공
	
	- 유료

- 구성형 쿠버네티스

	- 사용하는 시스템에 쿠버네티스 클러스터를 자동으로 구성해주는 솔루션
	
	- Kubeadm, kops(kubernetes Operations), KRIB(Kubernetes Rebar Integrated Bootstrap), kubespray가 있음
	
	- Kubeadm은 사용자가 변경하기 수월하고 온프레미스(On-premises)와 클라우드 모두 지원

	- kubespray는 실제 업무 환경에서도 매우 편리하게 쿠버네티스 클러스터를 자동으로 배포할 수 있는 도구

#### <쿠버네티스(k8s) 구성 요소>

- kubectl, kubelet, API 서버, 캘리코, etcd, 컨트롤러 매니저, 스케줄러, kube-proxy, 컨테이너 런타임, 파드 등

- 쿠버네티스 구성 요소는 동시에 여러 개가 존재하는 경우 Hash 코드를 삽입하여 중복된 이름 회피(예시 : calico-node-bf486의 bf486)

- 구성 요소의 이름을 직접 정할 수 있음

- 구성 요소에 문제 발견 시 다시 생성되는 특성을 가지는 파드로 이루어져 있어서 자동으로 이름을 지정하는 것이 관리 수월

- 아래 예시에서 coredns-5644d7b6d9-b4dz9의 5644d7b6d9은 레플리카셋(ReplicaSet)을 무작위 문자열로 변형하여 추가한 것

```
# --all-namespaces는 default(기본 namespaces) 외 모든 것을 표시
# kubectl get pods는 파드를 수집하여 출력

[root@m-k8s ~]#  kubectl get pods --all-namespaces
NAMESPACE     NAME                                       READY   STATUS    RESTARTS   AGE
kube-system   calico-kube-controllers-6bbf58546b-pmk78   1/1     Running   0          36m
kube-system   calico-node-bf486                          1/1     Running   0          31m
kube-system   calico-node-j9plc                          1/1     Running   0          22m
kube-system   calico-node-mnkgd                          1/1     Running   0          27m
kube-system   calico-node-xwxtc                          1/1     Running   0          36m
kube-system   coredns-5644d7b6d9-b4dz9                   1/1     Running   0          36m
kube-system   coredns-5644d7b6d9-jmsxh                   1/1     Running   0          36m
kube-system   etcd-m-k8s                                 1/1     Running   0          35m
kube-system   kube-apiserver-m-k8s                       1/1     Running   0          35m
kube-system   kube-controller-manager-m-k8s              1/1     Running   0          35m
kube-system   kube-proxy-5ltsx                           1/1     Running   0          22m
kube-system   kube-proxy-fzvsx                           1/1     Running   0          36m
kube-system   kube-proxy-gfsc8                           1/1     Running   0          31m
kube-system   kube-proxy-v8lxz                           1/1     Running   0          27m
kube-system   kube-scheduler-m-k8s                       1/1     Running   0          35m 
```

#### <쿠버네티스(k8s) 구성 요소간 통신 : 관리자나 개발자가 파드를 배포할 때>

- 관리자 or 개발자가 파드 배포 명령을 수행했을 때 실행되는 순서는 하기 그림과 같음

- 0 ~ 7번 : 기본 설정으로 배포된 쿠버네티스에서 이루어지는 통신 단계를 구분

- 10번대 : 선택적으로 배포하는 것들로 순서와 상관이 없음

<img src="https://user-images.githubusercontent.com/101415950/197653986-0e0c9c1f-f55d-4071-b344-d753e54be574.png" width="80%" height="80%">

- 0 : kubectl

	- 쿠버네티스 클러스터에 명령을 내리는 역할
	
	- 바로 실행되는 명령 형태인 binary로 배포되므로 Master Node에 있을 필요 없음
	  (kubectl이 어디에 있더라도 API 서버의 접속 정보만 있으면 어느 곳에서든 쿠버네티스 클러스터에 명령 가능)
	
	- 통상적으로 API 서버와 주로 통신하므로 API 서버가 위치한 Master Node에 구성할 수 있음

	- Worker Node에서 kubectl를 실행하기 위해 마스터 노드의 scp 명령으로 쿠버네티스 클러스터의 정보를 Worker Node로 받아와야 함
	  (쿠버네티스 클러스터의 정보를 kubectl이 알게 하기 위해)

- 1 : API 서버

	- 쿠버네티스 클러스터의 중심 역할을 하는 통로
	
	- 상태 값을 저장하는 etcd 등 여러 요소들이 API 서버를 중심으로 두고 통신
	
	- 회사에서 모든 직원과 상황을 관리하고 목표를 설정하는 관리자 역할

- 2 : etcd

	- etc 디렉터리(리눅스의 구성 정보를 가지고 있는 디렉터리)와 distributed(퍼트리다)의 합성어

	- 구성 요소들의 상태 값이 모두 저장되는 장소(etcd 외 다른 구성 요소는 상태 값을 관리하지 않음)
	
	- 회사의 관리자가 모든 보고 내용을 기록하는 노트
	
	- etcd의 정보만 백업되어있으면 긴급한 장애 상황에서도 쿠버네티스 클러스터 복구 가능
	
	- 분산 저장이 가능한 key-value 저장소이므로 복제하여 여러 곳에 저장해 두면 하나의 etcd에 장애가 발생해도 시스템 가용성 확보 가능

	- 멀티 마스터 노드 형태

- 3 : Controller Manager

	- 쿠버네티스 클러스터의 Object 상태 관리
	
	- Worker Node에서 통신 불량인 경우 상태 체크 및 복구는 Controller Manager에 속한 Node Controller에서 이루어짐

	- ReplicaSet Controller는 ReplicaSet에 요청받은 파드 갯수대로 파드 생성

	- EndPoint Controller는 서비스와 파드를 연결하는 역할

	-  Controller Manager에 소속된 다양한 상태 값을 관리하는 주체들이 각자의 역할 수행

- 4 : Scheduler

	- Node의 상태, 자원, 레이블, 요구 조건 등 고려하여 파드를 어떤 Worker Node에 생성할지 결정하고 할당하는 역할

	- 파드를 조건에 맞는 Worker Node에 지정하고, 파드가 Worker Node에 할당된 일정을 관리하는 역할

- 5 : kubelet

	- 파드의 구성 내용(PodSpec)을 받아 컨테이너 런타임으로 전달

	- 파드 내 컨테니어들이 정상적으로 동작하는지 모니터링

	- 파드의 생성과 상태 관리 및 복구 등 담당

	- kubelet에 문제 발생 시 파드가 정상적으로 관리되지 않음

- 6 : 컨테이너 런타임(CRI, Container Runtime Interface)

	- 파드를 이루는 컨테이너의 실행을 담당

	- 파드 내 다양한 종류의 컨테이너가 문제 없이 동작하게 하는 표준 인터페이스

- 7 : 파드(Pod)

	- 한 개 이상의 컨테이너로 단일 목적의 일을 수행하는 쿠버네티스 애플리케이션의 최소 단위

	- 웹 서버 역할을 할 수 있고 로그나 데이터를 분석하는 역할도 할 수 있음

	- 파드는 가상 머신과 달리 언제라도 죽을 수 있는 존재로 가정하고 설계되었기 때문에 여러 대안으로 디자인됨

	[컨테이너와 파드의 관계]   
	<img src="https://user-images.githubusercontent.com/101415950/197660830-bb278a36-0e2e-41dd-8f80-cb7cb04b1915.png" width="30%" height="30%">

- 11 : 네트워크 플러그인

	- 쿠버네티스 클러스터의 통신을 위해 구성해야 하는 요소

	- 일반적으로 CNI로 구성

	- CNI는 클라우드 네이티브 컴퓨팅 재단의 프로젝트로 컨테이너의 네트워크 안정성과 확장성을 보장하기 위해 개발

	- CNI에 사용할 네트워크 플로그인을 선택 시 구성 방식과 지원하는 기능, 성능이 각기 다르므로 사용 목적에 맞게 선택

	- CNI는 캘리코(Calico), 플래널(Flannel), 실리움(Cilium), 큐브 라우터(Kube-router), 로마나(Romana), 위브넷(WeaveNet), Canal이 있음

	- 캘리코(Calico)는 L3로 컨테이너 네트워크를 구성 / 플래널(Flannel)은 L2로 컨테이너 네트워크를 구성

	- 네트워크 프로토콜인 BGP와 VXLAN의 지원, ACL(Access Control List) 지원, 보안 기능 제공 등을 살펴보고 
	  필요한 조건을 가지고 있는 네트워크 플러그인을 선택할 수 있어서 설계 유연성이 높음

- 12 : CoreDNS

	- 클라우드 네이티브 컴퓨팅 재단에서 보증하는 프로젝트

	- 빠르고 유연한 DNS 서버

	- 쿠버네티스 클러스터에서 도메인 이름을 이용하여 통신하는 데 사용

	- 실무에서 쿠버네티스 클러스터를 구성하여 사용할 때, IP보다 DNS Name을 편리하게 관리해 주는 CoreDNS를 사용하는 것이 일반적임

#### <쿠버네티스(k8s) 구성 요소간 통신 : 사용자가 배포된 파드에 접속할 때>

- 1 : kube-proxy

	- 쿠버네티스 클러스터는 파드가 위치한 노드에 kube-proxy를 통해 파드가 통신할 수 있는 네트워크 설정
	
	- 실제 통신은 br_netfilter와 iptables로 관리   
	  (config.sh 파일에서 br_netfilter 커널 모듈을 적재하고 iptables를 거쳐 통신)

- 2 : 파드(Pod)

	- 이미 배포된 파드에 접속하고 필요한 내용을 전달받음

	- 대부분 사용자는 파드가 어떤 Worker Node에 위치하는지 신경쓰지 않아도 됨

#### <쿠버네티스(k8s) 구성 요소간 통신 : 파드 생명주기>

- 쿠버네티스의 가장 큰 장점은 쿠버네티스 구성 요소마다 하는 일이 명확하게 구분됨 => 마이크로서비스 아키텍처(MSA)와 연관

- 각자의 역할을 충실하게 수행하면 클러스터 시스템이 안정적으로 운영됨

- 역할이 나누어져 있어 문제 발생 시 어느 부분에서 문제가 발생했는지 디버깅하기 수월함

<img src="https://user-images.githubusercontent.com/101415950/197666301-6be225cc-8d55-46d8-801e-29d05d6206e2.png" width="80%" height="80%">


1. kubectl을 통해 API 서버에 파드 생성을 요청

2. API 서버에 전달된 내용이 있으면 API 서버는 etcd에 전달된 내용을 모두 기록하여 클러스터 상태 값을 최신으로 유지   
   => 각 요소가 상태를 업데이트할 때마다 모두 API 서버를 통해 etcd에 기록

3. API 서버에 파드 생성이 요청된 것을 Controller Manager가 인식하면 Controller Manager는 파드를 생성 후 API 서버에 전달   
   (아직 어떤 Worker Node에 파드를 적용할 지는 결정되지 않은 상태로 파드만 생성)

4. API 서버에 파드가 생성되었다는 정보를 Scheduler가 인식   
   Scheduler는 생성된 파드를 어떤 Worker Node에 적용할지 조건을 고려하여 결정 후 해당 Worker Node에 파드를 띄우도록 요청

5. API 서버에 전달된 정보대로 지정한 Worker Node에 파드가 속해 있는지 Scheduler가 kubelet으로 확인

6. kubelet에서 컨테이너 런타임으로 파드 생성을 요청

7. 파드 생성

8. 파드는 사용 가능한 상태가 됨

#### <쿠버네티스(k8s) 상태유지 방법>

- 쿠버네티스는 작업을 순서대로 진행하는 Workflow 구조가 아닌 선언적인(declarative) 시스템 구조를 가짐

- 각 요소가 추구하는 상태(desired status)를 선언하면 현재 상태(current status)와 비교 점검 후 추구하는 상태에 맞출려고 하는 구조

- 추구하는 상태를 API 서버에 선언하면 다른 요소들이 API 서버에서 확인하여 현재 상태와 비교하고 그에 맞게 상태를 변경

- API는 현재 상태 값을 가지고 있고 이것을 보존하므로 etcd가 필요, API서버와 etcd는 거의 한몸처럼 동작하도록 설계

- Work Node는 Workflow 구조에 따라 설계됨   
	
	- 쿠버네티스가 kubelet과 컨테이너 런타임을 통해 파드를 생성하고 제거 구조이므로 선언적인 방식으로 구조화 하기에 어렵기 때문
 	
	- 명령이 절차적으로 전달되는 방식이 시스템 성능을 높이는 데 효율적이기 때문
 
 - Master Node는 이미 생성된 파드들을 유기적으로 연결하므로 쿠버네티스 클러스터를 안정적으로 유지하기 위해 선언적인 시스템이 편리

<img src="https://user-images.githubusercontent.com/101415950/197680984-d017ee86-a748-4b9d-8371-579dc703b7b1.png" width="80%" height="80%">


#### <파드 생성 방법>

- 쿠버네티스를 사용한다는 것 = 사용자에게 효과적으로 파드를 제공한다는 뜻

- kubectl run 파드이름 : 파드생성

- kubectl create deployment 파드이름 : 파드생성(파드이름을 제외한 나머지 부분 해시코드로 무작위 생성)

- kubectl get pod : 파드 확인 (kubectl get pods -o wide : 파드에 대한 더 많은 정보 확인)

- curl ip주소 : ip주소의 웹 페이지 정보를 받아오는지 확인

```
[root@m-k8s ~]# kubectl run nginx-pod --image=nginx		#--image=(생성할 이미지 이름 or 이미지 경로)
pod/nginx-pod created						
[root@m-k8s ~]# kubectl create deployment dpy-nginx --image=nginx
deployment.apps/dpy-nginx created
```

- run으로 파드 생성 시 단일 파드 1개만 생성 (초코파이 1개)

- create deployment로 파드 생성 시 Deployment라는 관리 그룹 내 파드 생성 (초코파이 박스 내 초코파이 1개)

```
[root@m-k8s ~]# kubectl get pods
NAME                         READY   STATUS    RESTARTS   AGE
dpy-nginx-7cd4d79cc9-xmv28  1/1     Running   0          50s
nginx-pod                    1/1     Running   0          87s 
```

<img src="https://user-images.githubusercontent.com/101415950/197715292-485c95d7-c8d6-4eef-89cd-d00318723b7a.png" width="40%" height="40%">

#### <오브젝트>

- 쿠버네티스를 사용하는 관점에서 파드(Pod)와 Deployment는 Spec과 상태 등의 값을 가지고 있음

- 오브젝트는 Spec과 상태 등 값을 갖는 파드(Pod)와 Deployment를 개별 속성을 포함해 부르는 단위

- 기본 오브젝트

	- 파드(Pod)
	
		- 쿠버네티스에서 실행되는 최소 단위(웹 서비스를 구동하는 데 필요한 최소 단위)
		
		- 독립적인 공간과 사용 가능한 IP를 가지고 있음
		
		- 하나의 파드는 1개 이상의 컨테이너를 갖고 있으므로 여러 기능을 묶어 하나의 목적으로 사용 가능
		
		- 범용으로 사용할 시 대부분 1개의 파드에 1개의 컨테이너를 적용

	- 네임스페이스(Namespace)
		
		- 쿠버네티스 클러스터에서 사용되는 리소스들을 구분해 관리하는 그룹

		- ex) default : 특별히 지정하지 않으면 기본으로 할당됨
		
		- ex) kube-system : 쿠버네티스 시스템에 사용됨
		
		- ex) metallb-system : 온프레미스에서 쿠버네티스 사용 시 외부에서 클러스터 내부로 접속하게 도와주는 컨테이너들이 속함

	- 볼륨(Volume)
		
		- 파드가 생성될 때 파드에서 사용할 수 있는 디렉터리 제공

		- 파드는 영속되는 개념이 아니고 제공되는 디렉터리를 임시로 사용
	
		- 파드가 사라지더라도 저장과 보존이 가능한 디렉터리를 볼륨(Volume)을 통해 생성 및 사용 가능
	
	- 서비스(Service)

		- 파드는 클러스터 내 유동적이므로 접속 정보가 고정적이지 않음

		- 파드 접속을 안정적으로 유지하도록 서비스를 통해 내/외부로 연결

		- 서비스는 파드가 생성될 때 부여되는 새로운 IP를 기존에 제공하던 기능과 연결해줌

		- 서비스는 쿠버네티스 외부에서 내부로 접속 시 내부 구조, 파드의 생존 여부를 신경쓰지 않아도 이를 논리적으로 연결하는 것
		
		- 기존 인프라에서 로드밸런서, 게이트웨이와 비슷한 역할

	<img src="https://user-images.githubusercontent.com/101415950/197724789-20739f8c-d7fd-4e6d-afa1-b76e2012d164.png" width="80%" height="80%">

#### <디플로이먼트(Deployment)>

- 기본 오브젝트만으로 쿠버네티스 사용 가능, 그러나 한계가 있어 이를 극복하기 위해 기능을 조합하고 추가한 것이 Deployment

- Deployment 이외에 데몬셋(DaemonSet), 컨피그맵(ConfigMap), 레플리카셋(ReplicaSet), PV(PersistentVolume), PVC(PersistentVolumeClaim),    
  스테이트풀셋(StatefulSet) 등이 있으며 목적에 맞는 오브젝트들을 추가하여 사용

- Deployment는 파드를 기반하며 ReplicaSet 오브젝트를 합친 형태

- 아래 그림은 Deployment 오브젝트 계층 구조를 나타냄

<img src="https://user-images.githubusercontent.com/101415950/197727218-4d9c3a04-5fd0-481f-b6f2-e15abfb22876.png" width="40%" height="40%">

- API 서버와 Controller Manager는 파드를 생성되는 것을 감시할 뿐만 아니라 Deployment와 같이 ReplicaSet을 포함하는 오브젝트 생성 감시

- 아래 그림은 API 서버와 Controller Manager의 통신을 나타냄

<img src="https://user-images.githubusercontent.com/101415950/197727795-eac86dd4-56e6-4e7d-860e-53175d77545d.png" width="40%" height="40%">


#### <NGINX 이미지>

- 컨테이너로 도커를 사용하므로 도커의 기본 저장소인 도커 허브에서 이미지를 가지고 옴 (https://hub.docker.com/_/nginx)

- 클라우드 서비스를 이용하고 있으면 기본 저장소 외 클라우드 서비스 업체에서 제공하는 저장소를 사용

- ex) 구글의 GCR(Google Container Registry), 아마존의 ECR(Elastic Container Registry), 마이크로소프트의 ACR(Azure Container Registry)

#### <ReplicaSet으로 파드 수 관리>

- 다수의 파드를 하나씩 생성한다면 비효율적이므로 쿠버네티스에서는 다수의 파드를 만드는 ReplicaSet 오브젝트를 제공

- 파드 3개 생성하겠다고 ReplicaSet에 선언하면 Controller Manager와 Scheduler가 Worker Node에 파드 3개를 만들도록 선언 

- ReplicaSet은 파드 수를 보장하는 기능만 제공

- 그러므로 Rolling 업데이트 기능 등이 추가된 Deployment를 사용하여 파드 수를 관리하기를 권장

- 아래 그림은 ReplicaSet으로 파드 수를 관리하는 과정(총 3개의 파드 상태로 변경됨)
<img src="https://user-images.githubusercontent.com/101415950/197747014-7e3c2f22-e486-4200-bca6-eedf34577057.png" width="60%" height="60%">

[ReplicaSet : 파드로 생성된 nginx-pod]
```
[root@m-k8s ~]# kubectl scale pod nginx-pod --replicas=3
Error from server (NotFound): the server could not find the requested resource
```

- kubectl scale pod 파드명 --replicas=갯수 : 파드의 수를 작성한 갯수로 변경하는 명령어

- Deployment 오브젝트에 속하지 않아 파드 수를 관리하지 못하므로 리소스를 확인할 수 없다는 에러 발생

[ReplicaSet : Deployment로 생성된 dpy-nginx]
```
[root@m-k8s ~]# kubectl scale deployment dpy-nginx --replicas=3
deployment.apps/dpy-nginx scaled
[root@m-k8s ~]# kubectl get pods -o wide 
NAME                         READY   STATUS    …   AGE     IP              NODE   …
dpy-nginx-7cd4d79cc9-td8nk   1/1     Running   …   39s     172.16.132.3    w3-k8s …
dpy-nginx-7cd4d79cc9-xdbvx   1/1     Running   …   39s     172.16.103.134  w2-k8s …
dpy-nginx-7cd4d79cc9-xmv28   1/1     Running   …   7m47s   172.16.221.129  w1-k8s …
nginx-pod                    1/1     Running   …   8m24s   172.16.103.132  w2-k8s …
```

- Deployment를 사용하여 파드 수를 관리하여 올바르게 실행됨

- kubectl get pods, kubectl get pod 단수 복수 표현 둘다 동일하게 적용됨

#### <Spec 지정하여 오브젝트 생성>

- create 명령어는 replicas 옵션 사용불가, scale은 이미 만들어진 Deployment에만 사용 가능하므로 한번에 여러 개의 파드를 만들 수 없음

- 한번에 여러 개의 파드를 만들기 위해 오브젝트 스펙(object spec) 파일을 작성 필요

- object spec은 보통 YAML 문법으로 작성   
  (최근 상용 및 오픈 소스 기술들은 Spec과 상태값을 주로 YAML로 작성, YAML은 데이터의 내용을 쉽게 파악할 수 있는 표준)

- kubectl api-versions : 사용 가능한 API 버전을 확인하는 명령어

[Object Spec 파일 예시 : Deployment, echo-hname.yaml]

```
apiVersion: apps/v1 			# API 버전
kind: Deployment			# 오브젝트 종류
metadata:
  name: echo-hname
  labels:
    app: nginx
spec:
  replicas: 3 				# 몇 개의 파드를 생성할지 결정
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: echo-hname
        image: sysnet4admin/echo-hname 	# 사용되는 이미지
```

[Object Spec 파일 예시 : Pod, echo-hname.yaml]

```
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
spec:
  containers:
  - name: container-name
    image: nginx
```

[Object Spec 파일 구조 (좌측 : Deployment, 우측 : Pod)]

<img src="https://user-images.githubusercontent.com/101415950/197912694-76c6d10f-4579-40dc-a206-9ac07e8e3c36.png" width="100%" height="100%">

- 쿠버네티스는 API 버전마다 포함되는 Object(Kind)와 요구사항이 다르므로 기존 파일을 수정하면서 정리하는 방식이 효율적임

```
#replicas의 값을 3에서 6으로 변경할 때 사용하는 명령어 : sed(streamlined editor)

sed -i 's/replicas: 3/replicas: 6/' ~/_Book_k8sInfra/ch3/3.2.4/echo-hname.yaml

# -i는 --in-place의 약어로 변경된 내용을 현재 파일에 바로 적용
# s/는 주어진 패턴을 원하는 패턴으로 변경
```


#### <apply로 오브젝트 생성 및 관리>

- Deployment를 생성하고 sed를 사용하여 replicas 변경 후 다시 생성했을 때 아래와 같은 오류 발생

```
[root@m-k8s ~]# kubectl create -f ~/_Book_k8sInfra/ch3/3.2.4/echo-hname.yaml
Error from server (AlreadyExists): error when creating "echo-hname.yaml": deployments.apps "echo-hname" already exists
```

- 배포된 Object의 Spec을 변경하고 싶을 때 지우고 다시 생성하는 방법말고 다른 방법은 apply를 이용하는 방법

- run은 단일 파드만 생성 가능하고 create deployment는 파일의 변경사항을 바로 적용할 수 없기 때문에 apply 명령어 사용

```
[root@m-k8s ~]# kubectl apply -f ~/_Book_k8sInfra/ch3/3.2.4/echo-hname.yaml
Warning: kubectl apply should be used on resource created by either kubectl create --save-config or kubectl apply
deployment.apps/echo-hname configured

# 처음부터 apply로 생성된 것이 아니라서 경고 표시 => 동작에 문제는 없지만 일관성에서 문제 발생 농후함
# 변경사항이 발생할 가능성이 있는 경우 처음부터 apply로 생성
```

[Run / Create / Apply 비교]

![image](https://user-images.githubusercontent.com/101415950/197914675-ae84e421-ed4d-45a4-8bd3-77a3dc277fec.png)

### <파드의 컨테이너 자동 복구 방법>

- 쿠버네티스는 거의 모든 부분이 자동 복구되도록 설계, 이 자동 복구 기술을 Self-Healing이라고 명명함

- 제대로 동작하지 않는 컨테이너를 다시 시작하거나 교체하여 파드가 정상적으로 동작되도록 함

```
[root@m-k8s ~]# kubectl exec -it nginx-pod -- /bin/bash
root@nginx-pod:/#

# exec : 실행
# i옵선 : stdin(standard input, 표준 입력)
# t옵션 : tty (teletypewriter, 명령줄 인터페이스)
# it : 표준 입력을 명령줄 인터페이스로 작성
# --는 exec에 대한 인자 값을 나누고 싶을 때 사용(즉 명령어 구분할 때 사용)
# 즉 nginx-pod 파드에 /bin/bash를 실행하여 nginx-pod 컨테이너에서 bash셸 접속

#---------------------------------------------------------------------------------------------------------------------------
[root@m-k8s ~]# kubectl exec -it nginx-pod -- ls -l /run
total 4
drwxrwxrwt. 2 root root  6 Aug  3 07:00 lock
-rw-r--r--. 1 root root  2 Aug 12 02:06 nginx.pid
drwxr-xr-x. 4 root root 39 Aug 12 02:06 secrets

# ls 요소: 파드에서 요소의 내용을 확인(예제의 /run 내용 확인)
# -l(long listing format) : 권한 확인(예제의 /run 권한 확인)

#---------------------------------------------------------------------------------------------------------------------------
root@nginx-pod:/# cat /run/nginx.pid
1

#배시 셸 접속 후 PID(Process ID, 프로세스 식별자)를 확인하면 언제나 1인걸 확인 가능

#---------------------------------------------------------------------------------------------------------------------------
[root@m-k8s ~]# i=1; while true; do sleep 1; echo $((i++)) `curl --silent 172.16.103.132 | grep title` ; done

# nginx-pod의 IP (172.16.103.132)에서 실행되는 웹 페이지를 1초마다 한 번씩 요청하는 스크립트를 실행하는 명령어
# curl에서 요청한 값만 받도록 --silent 옵션 추가
# 이 명령어로 nginx 상태 체크 가능(자동으로 복구되는 여부 등)

#---------------------------------------------------------------------------------------------------------------------------
root@nginx-pod:/# kill 1
root@nginx-pod:/# command terminated with exit code 137

# kill : PID 1번 종료 (bash 셸)
```

### <파드의 동작 보증 기능>

- 쿠버네티스는 파즈 자체에 문제가 발생 시 파드를 자동 복구하여 파드가 항상 동작하도록 보장하는 기능 보유

```
#파드 확인
[root@m-k8s ~]# kubectl get pods
NAME                         READY   STATUS    RESTARTS   AGE
echo-hname-5d754d565-7bzfs   1/1     Running   0          9m44s
echo-hname-5d754d565-8759n   1/1     Running   0          6m21s
echo-hname-5d754d565-dbt29   1/1     Running   0          6m21s
echo-hname-5d754d565-g7tl5   1/1     Running   0          9m44s
echo-hname-5d754d565-jl2c6   1/1     Running   0          6m21s
echo-hname-5d754d565-lksqr   1/1     Running   0          9m44s 
nginx-pod                    1/1     Running   0          26m 

#단일 파드 삭제
[root@m-k8s ~]# kubectl delete pods nginx-pod
pod "nginx-pod" deleted

#Deployment에 속한 파드 삭제
[root@m-k8s ~]# kubectl delete pods echo-hname-5d754d565-7bzfs
pod "echo-hname-5d754d565-7bzfs" deleted

#삭제 확인
[root@m-k8s ~]# kubectl get pods
NAME                         READY   STATUS    RESTARTS   AGE
echo-hname-5d754d565-8759n   1/1     Running   0          7m35s
echo-hname-5d754d565-9zcnn   1/1     Running   0          38s
echo-hname-5d754d565-dbt29   1/1     Running   0          7m35s
echo-hname-5d754d565-g7tl5   1/1     Running   0          10m
echo-hname-5d754d565-jl2c6   1/1     Running   0          7m35s
echo-hname-5d754d565-lksqr   1/1     Running   0          10m

# echo-hname-5d754d565-7bzfs 파드가 삭제되고 echo-hname-5d754d565-9zcnn 파드가 새로 생성됨
```

- 단일 파드는 Deployment에 속한 파드가 아니며 어떤 Controller도 이 파드를 관리하지 않으므로 바로 삭제 가능

![image](https://user-images.githubusercontent.com/101415950/197918961-a43a2a88-1033-45a2-bcef-e993c10d793c.png)

- Deployment에 속한 파드는 이전에 replicas에서 n개로 선언하여 파드의 수를 항상 확인하며 부족하면 새로운 파드를 생성

- 즉 Deployment로 생성하는 것이 파드의 동작을 보장하기 위한 조건!

![image](https://user-images.githubusercontent.com/101415950/197919004-3ec45c34-a8b0-4cf6-865e-75999497f328.png)

```
# Deployment에 속한 파드는 상위 Deployment를 삭제해야 삭제됨

[root@m-k8s ~]# kubectl delete deployment echo-hname
deployment.apps "echo-hname" deleted
```

### <Node 자원 보호>

- Node는 쿠버네티스 Scheduler에서 파드를 할당받고 처리하는 역할

- 몇 차례 문제가 생긴 Node에 파드를 할당하면 문제가 생길 수 있지만 사용해야 하면 영향도 적은 파드를 할당하여 일정기간 모니터링 필요

- 쿠버네티스에서 모든 Node에 균등하게 파드를 할당하고자 할때 문제가 생길 가능성이 있는 노드를 구별하기 위해 cordon 기능 사용

```
# apply를 통해 파드 생성후 scale을 통해 파드 수 변경(늘리기)

[root@m-k8s ~]# kubectl apply -f ~/_Book_k8sInfra/ch3/3.2.8/echo-hname.yaml
deployment.apps/echo-hname created
[root@m-k8s ~]# kubectl scale deployment echo-hname --replicas=9
deployment.apps/echo-hname scaled

# 각 노드로 공평하게 배분되었는지 확인 => NODE열 참조(공평하게 분배됨)
# -o=custom-columns : 사용자가 임의로 구성할 수 있는 열을 의미

[root@m-k8s ~]# kubectl get pods \
-o=custom-columns=NAME:.metadata.name,IP:.status.podIP,STATUS:.status.phase,NODE:.spec.nodeName
NAME                         IP               STATUS    NODE
echo-hname-5d754d565-69wgw   172.16.103.139   Running   w2-k8s
echo-hname-5d754d565-9t9s8   172.16.221.134   Running   w1-k8s
echo-hname-5d754d565-jdzrt   172.16.132.6     Running   w3-k8s
echo-hname-5d754d565-khrrr   172.16.132.8     Running   w3-k8s
echo-hname-5d754d565-qlk6f   172.16.103.138   Running   w2-k8s
echo-hname-5d754d565-qzs9v   172.16.221.136   Running   w1-k8s
echo-hname-5d754d565-qzvkv   172.16.103.137   Running   w2-k8s
echo-hname-5d754d565-rd9cf   172.16.221.135   Running   w1-k8s
echo-hname-5d754d565-sz5nm   172.16.132.7     Running   w3-k8s

# scale을 통해 파드 수 변경(줄이기) 후 각 노드로 공평하게 배분되었는지 확인 => NODE열 참조(공평하게 분배됨)

[root@m-k8s ~]# kubectl scale deployment echo-hname --replicas=3
deployment.apps/echo-hname scaled
[root@m-k8s ~]# kubectl get pods \
-o=custom-columns=NAME:.metadata.name,IP:.status.podIP,STATUS:.status.phase,NODE:.spec.nodeName
NAME                         IP               STATUS    NODE
echo-hname-5d754d565-9t9s8   172.16.221.134   Running   w1-k8s
echo-hname-5d754d565-jdzrt   172.16.132.6     Running   w3-k8s
echo-hname-5d754d565-qzvkv   172.16.103.137   Running   w2-k8s

# w3-k8s 노드에 cordon 명령을 실행(해제는 uncordoned)

[root@m-k8s ~]# kubectl cordon w3-k8s
node/w3-k8s cordoned

# cordon 명령 적용 확인
# cordon 명령 시 스케줄되지 않는 상태(SchedulingDisabled)로 표시

[root@m-k8s ~]# kubectl get nodes
NAME     STATUS                     ROLES    AGE    VERSION
m-k8s    Ready                      master   131m   v1.18.4
w1-k8s   Ready                      <none>   127m   v1.18.4
w2-k8s   Ready                      <none>   122m   v1.18.4
w3-k8s   Ready,SchedulingDisabled  <none>   117m   v1.18.4 

#scale을 통해 파드 수 변경(늘리기)

[root@m-k8s ~]# kubectl scale deployment echo-hname --replicas=9
deployment.apps/echo-hname scaled

# cordon 명령 적용한 부분을 제외하고 적용됨

[root@m-k8s ~]# kubectl get pods \
-o=custom-columns=NAME:.metadata.name,IP:.status.podIP,STATUS:.status.phase,NODE:.spec.nodeName
NAME                         IP               STATUS    NODE
echo-hname-5d754d565-9t9s8   172.16.221.134   Running   w1-k8s
echo-hname-5d754d565-cg5w6   172.16.103.140   Running   w2-k8s
echo-hname-5d754d565-f947n   172.16.221.137   Running   w1-k8s
echo-hname-5d754d565-fr5v6   172.16.103.141   Running   w2-k8s
echo-hname-5d754d565-jdzrt   172.16.132.6     Running   w3-k8s
echo-hname-5d754d565-mb9z5   172.16.103.142   Running   w2-k8s
echo-hname-5d754d565-mcm97   172.16.221.138   Running   w1-k8s
echo-hname-5d754d565-qzvkv   172.16.103.137   Running   w2-k8s
echo-hname-5d754d565-zdp4d   172.16.221.139   Running   w1-k8s
```
![image](https://user-images.githubusercontent.com/101415950/197936708-2d420a91-3b93-4adc-9d40-5bdc5542fccf.png)

[배포된 파드의 세부 값 확인하기]

```
# 배포된 파드 선택 후 -o yaml 옵션으로 배포된 파드의 내용을 pod.yaml에 저장
# vi(vim이 alias돼 있음)로 pod.yaml의 내용 확인

[root@m-k8s ~]# kubectl get pod echo-hname-5d754d565-69wgw -o yaml > pod.yaml
[root@m-k8s ~]# vi pod.yaml
```

- 좌측은 줄번호, 오른쪽은 pods.yaml에서 확인할 수 있는 값으로 확인됨

![image](https://user-images.githubusercontent.com/101415950/197932524-e3ce73d7-4503-4e6c-9794-cc16f568b052.png)

### <노드 유지보수>

- 정기 또는 비정기적인 유지보수를 위해 Node를 Off 해야되는 상황이 있음 => drain 기능 사용

- drain은 지정한 Node의 파드를 전부 다른 곳으로 이동시켜 해당 노드를 유지보수할 수 있게 하는 기능

```
# kubectl drain을 통해 유지보수할 Node를 파드가 없는 상태로 만듬
# 해당 Node의 daemonset을 지울 수 없어서 명령을 수행할 수 없다고 함(daemonset은 각 Node에 1개만 존재하는 파드이므로 drain으로 삭제 불가능)
# 즉 drain은 실제로 파드를 옮기는 것이 아닌 해당 Node에서 파드 삭제 후 다른 곳에 다시 생성

[root@m-k8s ~]# kubectl drain w3-k8s
node/w3-k8s cordoned
error: unable to drain node "w3-k8s", aborting command...

There are pending nodes to be drained:
w3-k8s
error: cannot delete DaemonSet-managed Pods (use --ignore-daemonsets to ignore): kube-system/calico-node-j9plc, kube-system/kube-proxy-5ltsx

# ignore-daemonsets 옵션을 추가 => daemonset을 무시하고 진행

[root@m-k8s ~]# kubectl drain w3-k8s --ignore-daemonsets
node/w3-k8s already cordoned
WARNING: ignoring DaemonSet-managed Pods: kube-system/calico-node-j9plc, kube-system/kube-proxy-5ltsx
evicting pod " echo-hname-5d754d565-jdzrt"
pod/ echo-hname-5d754d565-jdzrt
node/w3-k8s evicted

# 해당 Node에 파드가 없는지 확인 
# 옮긴 Node에 파드가 새로 생성되어 파드 이름과 IP가 부여된 것도 확인

[root@m-k8s ~]# kubectl get pods \
-o=custom-columns=NAME:.metadata.name,IP:.status.podIP,STATUS:.status.phase,NODE:.spec.nodeName
NAME                          IP              STATUS   NODE
echo-hname-5d754d565-9t9s8    172.16.221.134  Running  w1-k8s
echo-hname-5d754d565-67gbr   172.16.221.140 Running  w1-k8s
echo-hname-5d754d565-qzvkv    172.16.103.137  Running  w2-k8s

# 해당 Node의 상태는 cordon을 실행했을 때처럼 SchedulingDisabled 상태

[root@m-k8s ~]# kubectl get nodes
NAME   STATUS                     ROLES   AGE    VERSION
m-k8s  Ready                      master  145m   v1.18.4
w1-k8s Ready                      <none>  140m   v1.18.4
w2-k8s Ready                      <none>  136m   v1.18.4
w3-k8s Ready,SchedulingDisabled  <none>  131m   v1.18.4

# 유지보수가 끝났다고 가정하고 uncordon 명령 실행
[root@m-k8s ~]# kubectl uncordon w3-k8s
node/w3-k8s uncordoned
```

### <파드 업데이트 및 복구>

- 컨테이너에 새로운 기능 추가, 버그가 있어 업데이트가 필요한 상황 및 업데이트 도중 문제로 기존 버전으로 복구가 필요한 상황 등 있음

- 버전을 정하는 image: nginx:1.15.12에서 설치할 컨테이너 버전을 지정하고, 설치한 후에 단계별로 버전을 업데이트 시행

<b>1. 업데이트</b>

[rollout-nginx.yaml]
```
01apiVersion: apps/v1
kind: Deployment
metadata:
  name: rollout-nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.15.12
```

[Console]

```
# 컨테이너 버전 업테이트를 테스트하기 위한 파드 배포
# --recode : 배포된 정보의 히스토리 기록

[root@m-k8s ~]# kubectl apply -f ~/_Book_k8sInfra/ch3/3.2.10/rollout-nginx.yaml --record
deployment.apps/rollout-nginx created

# rollout history : record 옵션으로 기록된 히스토리 확인

[root@m-k8s ~]# kubectl rollout history deployment rollout-nginx
deployment.apps/rollout-nginx
REVISION  CHANGE-CAUSE
1         kubectl apply --filename=/root/_Book_k8sInfra/ch3/3.2.10/rollout-nginx.yaml --record=true

# 배포된 파드의 정보 확인(파드 이름과 IP를 위주로 보기)

[root@m-k8s ~]# kubectl get pods \
-o=custom-columns=NAME:.metadata.name,IP:.status.podIP,STATUS:.status.phase,NODE:.spec.nodeName
NAME                             IP               STATUS    NODE
rollout-nginx-5b7c85b5c9-g8x8x   172.16.103.143   Running   w2-k8s
rollout-nginx-5b7c85b5c9-xl5db   172.16.221.141   Running   w1-k8s
rollout-nginx-5b7c85b5c9-zwpgk   172.16.132.9     Running   w3-k8s 

# curl -I(헤더 정보만 보여주는 옵션) : 컨테이너 버전 확인

[root@m-k8s ~]# curl -I --silent 172.16.103.143 | grep Server 
Server: nginx/1.15.12

# set image 명령으로 컨테이너 버전을 1.16.0으로 업데이트
# --recode로 히스토리 기록

[root@m-k8s ~]# kubectl set image deployment rollout-nginx nginx=nginx:1.16.0 --record
deployment.apps/rollout-nginx image updated

#업데이트한 후에 파드의 상태를 확인(파드 이름과 IP를 위주로 보기)

[root@m-k8s ~]# kubectl get pods \
-o=custom-columns=NAME:.metadata.name,IP:.status.podIP,STATUS:.status.phase,NODE:.spec.nodeName
NAME                             IP               STATUS    NODE
rollout-nginx-7598b44f45-cp9kk   172.16.132.10    Running   w3-k8s
rollout-nginx-7598b44f45-nscgk   172.16.103.144   Running   w2-k8s
rollout-nginx-7598b44f45-w6swb   172.16.221.142   Running   w1-k8s
```

- 파드들의 이름과 IP가 변경됨

- 파드는 언제든지 지우고 다시 생성할 수 있음

- 파드가 속한 컨테이너를 업데이트 하는 가장 쉬운 방법은 파드를 관리하는 replicas의 수를 줄이고 늘려 파드를 새로 생성하는 것

- 시스템 영향을 최소화하기 위해 replicas에 속한 파드를 하나씩 순차적으로 지우고 생성

- 파드 수가 많으면 하나씩이 아니라 다수의 파드가 업데이트 됨(업데이트 기본값 : 전체의 1/4개, 최솟값 : 1개)

<img src="https://user-images.githubusercontent.com/101415950/197939848-8d8b0502-b9a6-4ce8-bd12-0e3a7a72d9ad.png" width="80%" height="80%">

<b>2. 업데이트 실패 시 복구</b>

```
# set image 명령으로 컨테이너 버전을 의도(1.17.2)와 다르게 1.17.23으로 입력

[root@m-k8s ~]# kubectl set image deployment rollout-nginx nginx=nginx:1.17.23 --record
deployment.apps/rollout-nginx image updated

# 파드가 삭제되지 않고 pending(대기 중) 상태에서 넘어가지 않음

[root@m-k8s ~]# kubectl get pods \
-o=custom-columns=NAME:.metadata.name,IP:.status.podIP,STATUS:.status.phase,NODE:.spec.nodeName
NAME                             IP               STATUS    NODE
rollout-nginx-7598b44f45-cp9kk   172.16.132.10    Running   w3-k8s
rollout-nginx-7598b44f45-nscgk   172.16.103.144   Running   w2-k8s
rollout-nginx-7598b44f45-w6swb   172.16.221.142   Running   w1-k8s
rollout-nginx-7759875c65-wghcd   172.16.103.149   Pending  w2-k8s

# rollout status로 문제 확인
# 새로운 replicas는 생성했으나 Deployment 배포 단계에서 더 이상 진행되지 않은 것을 확인
# 여러 차례 Deployment 생성 시도 후 실패했다는 에러메시지 확인

[root@m-k8s ~]# kubectl rollout status deployment rollout-nginx
Waiting for deployment "rollout-nginx" rollout to finish: 1 out of 3 new replicas have been updated...
error: deployment "rollout-nginx" exceeded its progress deadline

# describe 명령으로 쿠버네티스 상태 자세히 살펴보기
# replicas가 새로 생성되는 과정에서 멈춤
# 1.17.23 버전의 nginx 컨테이너가 없기 때문

[root@m-k8s ~]# kubectl describe deployment rollout-nginx
Name:                   rollout-nginx
[중략]
OldReplicaSets:  rollout-nginx-7598b44f45 (3/3 replicas created)
NewReplicaSet:   rollout-nginx-7759875c65 (1/1 replicas created) 
[생략]

# rollout history로 revision 확인 후 rollout undo으로 명령 실행을 취소하여 버전 되돌림

[root@m-k8s ~]# kubectl rollout history deployment rollout-nginx
deployment.apps/rollout-nginx
REVISION  CHANGE-CAUSE
1         kubectl apply --filename=~/_Book_k8sInfra/ch3/3.2.10/rollout-nginx.yaml --record=true
2         kubectl set image deployment rollout-nginx nginx=nginx:1.16.0 --record=true
3         kubectl set image deployment rollout-nginx nginx=nginx:1.17.23 

[root@m-k8s ~]# kubectl rollout undo deployment rollout-nginx
deployment.apps/rollout-nginx rolled back

# rollout history로 확인 결과 revision 4가 추가되고 revision 2가 삭제됨
# revision 2로 되돌렸기 때문에 revision 2는 삭제되고 가장 최근 상태는 revision 4가 됨

[root@m-k8s ~]# kubectl rollout history deployment rollout-nginx
deployment.apps/rollout-nginx
REVISION  CHANGE-CAUSE
1         kubectl apply --filename=/root/_Book_k8sInfra/ch3/3.2.10/rollout-nginx.yaml --record=true
3         kubectl set image deployment rollout-nginx nginx=nginx:1.17.23 --record=true
4         kubectl set image deployment rollout-nginx nginx=nginx:1.16.0 --record=true 
```

![image](https://user-images.githubusercontent.com/101415950/197941594-06abb904-445f-454b-ba76-ccb9682f7fd9.png)

### <특정 시점으로 파드 복구>

- --to-revision 옵션을 통해 바로 전 상태가 아닌 특정 시점으로 복구

```
### revision 1로 돌아가기

[root@m-k8s ~]# kubectl rollout undo deployment rollout-nginx --to-revision=1
deployment.apps/rollout-nginx rolled back

### curl -I로 nginx 컨테이너의 버전 확인

[root@m-k8s ~]# curl -I --silent 172.16.103.150 | grep Server
Server: nginx/1.15.12
```

---
### 4. 도커(Docker)

- 쿠버네티스는 컨테이너를 오케스트레이션하는 Tool

- 파드는 오케스트레이션하는 기본 단위

- 파드는 컨테이너로 이루어짐

- 도커는 컨테이너를 만들고 관리하는 Tool

- 최근에는 도커를 몰라도 여러 공급사에서 만든 컨테이너 이미지로 쿠버네티스에 컨테이너 인프라 서비스를 만들 수 있음

- 그러나 상황에 따라서 직접 만든 소스 코드를 빌드하여 컨테이너로 만들어서 사용해야 하는 일이 있음

- 또한, 트러블 슈팅을 위해 컨테이너에 대한 지식이 요구됨 (CI & CD, 모니터링은 컨테이너로 관리)

- 그러므로 컨테이너와 이를 다루는 도커를 공부할 필요성이 있음

<br></br>
### <파드, 컨테이너, 도커, 쿠버네티스 관계>

- 파드들은 워커 노드라는 노드 단위로 관리

- 워커 노드와 마스터 노드가 모여 쿠버네티스 클러스터가 됨

- 파드는 1개 이상의 컨테이너로 이루어짐

- 파드는 쿠버네티스로부터 IP를 받아 컨테이너가 외부로 통신할 수 있는 경로 제공

- 파드는 컨테이너들이 정상적으로 동작하는지 확인하고 네트워크나 저장 공간을 서로 공유하게 함

- 파드가 이러한 환경을 조성하므로 컨테이너들이 마치 하나의 호스트에 존재하는 것처럼 동작   
  => 즉 파드는 컨테이너를 관리, 쿠버네티스 워커노드는 파드를 관리, 쿠버네티스 마스터는 워커노드를 관리

- 쿠버네티스 마스터 역시 파드(컨테이너)로 이루어짐

<img src="https://user-images.githubusercontent.com/101415950/199029127-9190910e-ae66-46c2-a0aa-7a536aaedd78.png" width="80%" height="80%">
(출처 : https://m.blog.naver.com/megaboy1129/222071383753)

- 이 구조에서 가장 기본인 컨테이너는 하나의 운영 체제 안에서 커널을 공유하며 개별적인 실행단위를 제공하는 격리된 공간

- 개별적인 실행 환경은 CPU, 네트워크, 메모리와 같은 시스템 자원을 독자적으로 사용하도록 할당된 환경

- 개별적인 실행 환경에서 실행되는 프로세스를 구분하는 ID도 컨테이너 안에 격리되어 관리

- 그러므로 각 컨테이너 내부에서 실행되는 애플리케이션은 <b>독립적</b>으로 동작

- 도커를 사용하면 사용자가 따로 신경쓰지 않아도 컨테이너를 생성할 때 개별적인 실행 환경을 분리하고 자원을 할당

<br></br>
### <다양한 컨테이너 관리 도구>

- 컨테이너디(Containerd)

	- 컨테이너 런타임 부분을 분리하여 만든 오픈 소스 컨테이너 관리 도구

	- 쿠버네티스와의 통신에 필요한 CRI(컨테이너 런타임 인터페이스) 규격에 맞춰 구현한 플러그인 사용하여 쿠버네티스와 통합

	- 다른 시스템과 통합해 컨테이너를 관리하는 기능을 제공하므로 컨테이너 관리 도구를 직접 개발하려는 개발자에게 적합

- 크라이오(CRI-I)

	- 범용적인 컨테이너 관리 도구인 도커와 컨테이너디와 달리 쿠버네티스와 통합하는 것이 주목적

	- 다른 도구에 비해 가볍고 단순하며 CRI 규격을 자체적으로 구현하고 있어 별도의 구성요소나 플러그인 없이 쿠버네티스와 통합

	- 현재 관리와 구성에 관한 자료는 도커보다 부족

- 카타 컨테이너(Kata Container)

	- 기존 컨테이너 방식과 달리 컨테이너마다 독립적인 커널을 제공

	- 개별 컨테이너를 위한 가벼운 가상 머신을 생성하고 그 위에서 컨테이너가 동작

	- 그러므로 모든 컨테이너는 독립적인 커널을 사용하므로 다른 컨테이너의 영향을 받지 않음

	- 기술적으로 기본 컨테이너 방식과 가상화 방식의 중간 영역

	- 가상 머신을 통해 컨테이너를 격리하므로 기술적으로는 보안에 좀 더 강함

	- 필요한 CPU나 메모리의 크기가 기존 컨테이너 방식보다 큼

- 도커(Docker)

	- 컨테이너 관리 기능 외에도 컨테이너를 실행하는 데 필요한 이미지를 만들거나 공유하는 등의 다양한 기능 제공

	- 도커는 CLI(Command Line Interface)와 명령을 받아들이는 도커 데몬으로 구성

	- 컨테이너를 제어하기 위해 별도의 컨테이너디를 포함

	- 도커와 쿠버네티스를 함께 설치할 경우 쿠버네티스는 컨테이너 오케스트레이션을 위해 도커에 포함된 컨테이너디 활용

	- 네트워크를 통한 호출로 동작하므로 구조적으로 다소 복잡한 편이지만 모두 도커에서 관리하므로 사용자가 신경안써도 됨

<img src="https://user-images.githubusercontent.com/101415950/199033128-a83454b1-6fdc-425b-b367-239509d87c9e.png" width="50%" height="50%">

<br></br>
### <도커 학습 내용 정리>

- 도커 이미지를 내려받아 컨테이너로 실행하고 도커 이미지와 컨테이너를 삭제하는 방법을 학습할 예정

1. 이미지 찾기
2. 실행하기
3. 디렉터리와 연결하기
4. 삭제하기

- 컨테이너 이미지는 베이그런트 이미지와 유사함

- 베이그런트 이미지는 이미지 자체로는 사용할 수 없고 베이그런트를 실행할 때 추가해야만 사용 가능

- 컨테이너 이미지도 그대로 사용할 수 없고 도커와 같은 CRI로 불러들여야 컨테이너가 실제로 동작

- 즉 컨테이너 이미지와 컨테이너는 실행된 파일과 실행 파일의 관계

- 따라서 컨테이너를 삭제할 때는 내려받은 이미지와 이미 실행된 컨테이너를 모두 삭제해야만 디스크 용량을 온전히 확보 가능

<img src="https://user-images.githubusercontent.com/101415950/199043441-2891be66-b8f1-4804-8eed-85be233296eb.png" width="80%" height="80%">
(출처 : https://devowen.com/249)

### <컨테이너 이미지 알아보기>

- 이미지는 레지스트리(registry) 저장소에 모여 있음

- 레지스트리는 도커 허브(https://hub.docker.com/)처럼 공개된 레지스트리일 수도 있고, 내부에 구축한 레지스트리일 수도 있음

- 이미지는 레지스트리 웹 사이트에서 직접 검색해도 되고, 슈퍼푸티 명령 창에서 쿠버네티스 마스터 노드에 접속해 검색할 수 있음

- 별도의 레지스트리를 지정하지 않으면 기본으로 도커 허브에서 이미지를 찾음

- docker search <검색어> : 특정한 이름(검색어)을 포함하는 이미지가 있는지 찾음

```
[root@m-k8s ~]# docker search nginx
이 검색결과는 나중에 할 예정(기억)
```

- docker search 명령 시 도출되는 열의 의미

	- INDEX
		
		- 이미지가 저장된 레지스트리

	- NAME
		
		- 검색된 이미지 이름
		
		- 공식 이미지를 제외한 나머지는 '레지스트리 주소/저장소 소유자/이미지 이름' 형태

	- DESCRIPTION
		
		- 이미지에 대한 설명

	- STARS
		- 해당 이미지를 내려받은 사용자에게 받은 평가 횟수

		- 사용자가 좋은 평가를 주고 싶을 때 스타(STAR) 추가 (Github star와 비슷)

		- 숫자가 클 수 록 신뢰성 높은 이미지

	- OFFICIAL
	
		- [OK] 표시는 해당 이미지에 포함된 애플리케이션, 미들웨어 등을 개발한 업체에서 공식적으로 제공한 이미지를 뜻함

	- AUTOMATED

		- [OK] 표시는 도커 허브에서 자체적으로 제공하는 이미지 빌드 자동화 기능을 활용하여 생성한 이미지를 뜻함

- docker search로 찾은 이미지는 docker pull로 내려받을 수 있음

```
[root@m-k8s ~]# docker pull nginx
이 검색결과는 나중에 할 예정(기억)
```

- 이미지를 내려받을 때 사용하는 태그, 레이어, 이미지의 고유 식별 값 등을 볼 수 있음

	- 태그(tag)

		- Using default tag와 함께 뒤에 따라오는 태그 이름을 통해 이미지를 내려받을 때 사용한 태그를 알 수 있음

		- 아무런 조건을 주지 않고 이미지 이름만으로 pull을 수행하면 기본으로 latest 태그(가장 최신 이미지를 뜻함)가 적용

		- 그러므로 내려받은 이미지 버전이 다를 수 있음

	- 레이어(layer)

		- 하나의 이미지는 여러 개의 레이어로 이루어져 있어서 레이어마다 Pull Complete 메시지가 발생

	- 다이제스트(digest)
	
		- 이미지 고유 식별자로, 이미지에 포함된 내용과 이미지의 생성 환경을 식별할 수 있음

		- 식별자는 Hash 함수로 생성되며 이미지가 동일한지 검증하는 데 사용

		- 이름이나 태그는 이미지를 생성할 때 임의로 지정하므로 이름이나 태그가 같다고 해서 같은 이미지라고 할 수 없음

		- 그러나 다이제스트는 고유한 값이므로 다이제스트가 같은 이미지는 이름이나 태그가 달라도 같은 이미지임

	- 상태(status)

		- 이미지를 내려받은 레지스트리, 이미지, 태그 등의 상태 정보를 확인할 수 있음

		- 형식은 '레지스트리 이름/이미지 이름:태그'

## 마크다운 언어 참조
https://gist.github.com/ihoneymon/652be052a0727ad59601
