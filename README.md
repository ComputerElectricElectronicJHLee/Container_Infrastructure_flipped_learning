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

#### <쿠버네티스(k8s) 구성 요소간 통신>

- 관리자 or 개발자가 파드 배포 명령을 수행했을 때 실행되는 순서는 하기 그림과 같음

<img src="https://user-images.githubusercontent.com/101415950/197653986-0e0c9c1f-f55d-4071-b344-d753e54be574.png" width="80%" height="80%">

- 0 : kubectl

	- 쿠버네티스 클러스터에 명령을 내리는 역할
	
	- 바로 실행되는 명령 형태인 binary로 배포되므로 Master Node에 있을 필요 없음
	
	- 통상적으로 API 서버와 주로 통신하므로 API 서버가 위치한 Master Node에 구성할 수 있음

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

## 마크다운 언어 참조
https://gist.github.com/ihoneymon/652be052a0727ad59601
