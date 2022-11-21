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
### 도커의 장점과 단점

- 장점

	- 독립된 가상 환경인 컨테이너
	
		- 각각 다른 환경(ex. 리눅스, 윈도우 등)에서 실행 시 컨테이너 단위로 각 환경 관리 가능
	
	- 각 요소들이 설치된 모습을 이미지로 박제하여 저장
	
		- 서버 증설 및 교체 시 일일이 각 Tool을 설치하지 않고 이미지를 내려받아 한번에 해결 가능
		
	- 컨테이너화된 애플리케이션들이 단일 운영체제상에서 실행되도록 해주는 기술

		- 단일 운영체제 상에서 동작하므로 가상 컴퓨팅에 비해 가벼움

- 단점

	- 리눅스 운영체제를 사용하는 기술로 리눅스용 소프트웨어 밖에 지원하지 않음
	
	- 호스트 서버에 문제 발생 시 여러 컨테이너에 영향을 끼침
	
		- 물리 서버 한 대에 여러 대의 서버를 띄우는 형식

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

		- 형식은 '레지스트리 이름/이미지 이름:태그' (docker.io/nginx:latest)

- 이미지 태그

	- 태그는 이름이 동일한 이미지에 추가하는 식별자
	
	- 이름이 동일해도 도커 이미지의 버전이나 플랫폼(CPU 종류, 운영체제 등)이 다를 수 있으므로 이를 구분하는 데 사용
	
	- 이미지 이름만 사용하고 태그를 명시하지 않으면 latest 태그를 기본으로 사용
	
	- 이미지 태그와 관련된 정보는 해당 이미지의 도커 허브 메뉴 중 Tags 탭에서 확인할 수 있음

<img src="https://user-images.githubusercontent.com/101415950/200843911-c4c32a10-509e-4557-977c-3601ac15c195.png" width="80%" height="80%">

	- 향후 이미지 버전이 올라가면서 추가 또는 변경되는 기능에 따라 예상치 못한 오류가 생길 수 있음
	
	- 그러므로 컨테이너 배포 시 latest 태그가 아닌 검증된 버전(stable)으로 배포해야 문제가 생기지 않음

- 이미지의 레이어 구조

	- 컨테이너 이미지는 애플리케이션과 각종 파일을 포함하고 있는 압축 파일에 가까움(실행 기능 포함)

	- 압축 파일은 내용이 같은 파일들이 각 압축 파일에서 공간을 독립적으로 점유하므로 압축한 파일 수에 따라 전체 용량이 증가

	- 이미지는 이미지가 같은 내용일 경우 여러 이미지에 동일한 레이어를 공유하므로 전체 용량 감소

<img src="https://user-images.githubusercontent.com/101415950/200861069-a766e898-6f41-46a0-989c-d285ef75aac6.png" width="80%" height="80%">

---
### 5. 젠킨스(JenKins)

- 쿠버네티스를 사용하는 이유는 컨테이너 애플리케이션을 유연하고 빠르게 배포하고 운영하기 위함

- 새로 개발한 애플리케이션을 쿠버네티스에 사용하는 과정(파이프라인)

	- 깃허브 등 저장소에 저장된 애플리케이션 소스 코드를 내려받아 도커 컨테이너 이미지로 빌드
	
	- 빌드한 컨테이너 이미지를 쿠버네티스에서 사용할 수 있도록 레지스트리에 등록
	
	- 레지스트리에 등록된 이미지를 기반으로 쿠버네티스 오브젝트 생성
	
	- 생성한 오브젝트(파드/Deployment)를 외부에서 접속할 수 있도록 서비스 형태로 노출

<img src="https://user-images.githubusercontent.com/101415950/202891494-ed7d017b-a6ea-4361-bf1a-78e2d10b2c02.png" width="80%" height="80%">

- 대부분 IT 작업은 파이프라인을 통해 결과를 도출

- 이러한 파이프라인은 도구를 사용해 자동화가 가능

- 자동화는 크게 지속적 통합(CI, Continuous Integration), 지속적 배포(CD, Continuous Deployment)로 정의

- 지속적 통합(CI, Continuous Integration)

	- CI는 개발을 진행하면서 품질을 관리할 수 있도록 하는 것
    
    	- 여러 명이 하나의 코드에 대해서 수정을 진행해도 지속적으로 통합하여 관리할 수 있음을 의미

	- 빌드/테스트 자동화를 통해 수정한 코드를 브랜치에 병합하기만 하면 자동으로 빌드와 테스트 검증

- 지속적 배포(CD, Continuous Deployment)

	- CD는 소프트웨어가 항상 신뢰가능한 수준으로 배포될 수 있도록 관리하자는 개념
    
    	- CD는 빌드 및 테스트 병합까지 성공적이면 github와 같은 저장소에 업로드 하는 지속적 제공으로도 사용됨

    	- 성공적으로 병합된 내역을 저장소 뿐만 아니라 사용자가 사용할 수 있는 배포환경까지 릴리즈하는 것을 의미

- 즉 CI/CD는 실무적인 환경에서 변경 사항을 계속 추적하여 좀 더 안정화된 애플리케이션을 만들고, 이를 배포하는 과정을 자동화하여    
  시스템을 안정적으로 운영하는 것

### <컨테이너 인프라 환경에서 CI/CD>

- CI는 코드를 Commit하고 Build했을 때, 정상적으로 작동하는지 반복적으로 검증하여 애플리케이션 신뢰성을 높이는 작업

- CI 과정을 마친 애플리케이션은 신뢰할 수 있는 상태

- CD는 CI과정에서 생성된 신뢰할 수 있는 애플리케이션을 실제 상용 환경에 자동으로 배포하는 것

- 애플리케이션을 상용 환경에 배포할 때 고려해야 할 사항이 여러가지 있음

- 그러한 사항을 CD에 미리 정의하면 실수를 줄이고, 실제 적용 시간도 최소화 가능

<img src="https://user-images.githubusercontent.com/101415950/202891830-740326fa-597c-48a8-b49d-d4ece39818ee.png" width="80%" height="80%">

- 개발자가 소스를 Commit하고 Push하면 CI 단계로 들어감

- CI 단계에서는 애플리케이션이 자동 빌드되고 테스트를 거쳐 배포할 수 있는 애플리케이션인지 확인

- 테스트를 통과하면 신뢰할 수 있는 애플리케이션으로 간주하고 CD 단계로 들어감

- CD 단계에서 애플리케이션을 컨테이너 이미지로 만들어서 파드, Deployment, statefulset 등 다양한 오브젝트 조건에 맞춰  
  미리 설정한 파일을 통해 배포

### CI/CD 도구 비교

<img src="https://user-images.githubusercontent.com/101415950/202892624-e21629ba-64ad-47c9-a387-f8949df55074.png" width="80%" height="80%">

- 팀시티(Teamcity)

	- Kotlin을 기반으로 만든 Kotlin DSL이라는 스크립트 언어로 작업을 구성

	- 빌드 작업을 수행하는 에이전트 3개와 빌드 작업 100개를 무료로 사용 가능
	
	- 더 많은 에이전트 이용 시 유료 결제 필요

- 깃허브 액션(Github Action)

	- 깃허브에서 지원하는 Workflow 기반 CI/CD 도구

	- 깃허브에 저장한 소스 코트를 자동 분석한 결과를 기반으로 깃허브 액션이 추천하는 방식에 따라 Workflow를 구성할 수 있음

	- 사용자가 직접 Workflow를 정의하는 파일을 작성한 후 깃허브 저장소에 넣어 사용 가능

	- 깃허브 저장소에 소스코드를 공개할 경우 깃허브 액션을 한 달에 2000분까지 무료로 사용

	- 추가로 사용할 경우 분 단위 요금이 별도로 부과

- 뱀부(Bamboo)

	- 유료이며 사용자의 서버에 설치해 사용

	- 아틀라시안에서 만든 다른 협업 도구와 연계하여 사용하면 효율적임

- 젠킨스(Jenkins)

	- 오픈 소스 CI/CD 도구

	- 출시 당시 허드슨(Hudson)이라는 이름이였으나 현재 젠킨스로 이름이 정정됨

	- 사용자가 직접 UI에서 작업을 구성하거나 작업 순서를 코드로 정의할 수 있음

	- 오랜 시간 많은 사람이 사용했으므로 사용에 필요한 정보를 찾기 쉬움

	- 관련 커뮤니티 활동이 활발하여 인터넷에서 대부분의 플러그인을 쉽게 찾을 수 있음

	- 특정 언어나 환경에 구애받지 않고 범용적인 목적으로 무난하게 쓸 수 있음

	- 거의 모든 환경에 사용할 수 있도록 다양한 플러그인을 추가해 원하는 형태를 만드는 블록 방식으로 구성

- 퍼블릭 클라우드 기반의 시스템일 때는 클라우드 서비스 제공 업체에서 배포하는 CI/CD 도구(AWS  CodeBuild, Azure Pipelines 등) 도입 가능

- 배포가 중요한 환경에서는 CD 기능에 중점을 둔 스핀네이커(Spinnaker)나 아르고 CD(Argo Cd)를 선택적으로 도입 가능

### 젠킨스로 쿠버네티스 운영 환경 개선하기

- 애플리케이션 배표 영역에 쿠버네티스를 사용하면 개발자는 애플리케이션 개발에만 집중할 수 있게 됨

- 기존에는 환경이 다른 곳에 빌드한 애플리케이션을 배포하게 되면 개발자가 개별 환경에 맞춰 애플리케이션 코드를 일일이 수정

- 모든 배포 환경을 컨테이너 인프라로 일원화하고, CI/CD 도구를 사용하면 애플리케이션에 맞는 환경을 적용해 자동으로 배포 가능

- 통합 과정에서 만들어진 컨테이너 이미지를 기반으로 쿠버네티스가 존재하는 어떤 환경에서도 일관성있는 애플리케이션 배포 가능

<img src="https://user-images.githubusercontent.com/101415950/202897753-21aa77ed-23d4-47eb-9797-e3b1ab6476bd.png" width="80%" height="80%">

- 1. 개발자가 작성한 애플리케이션 코드를 소스 코드 저장소에 Push

- 2. 쿠버네티스 내부에 설치된 젠킨스는 애플리케이션 코드를 빌드하고 레지스트리에 Push한 후 쿠버네티스에서 사용가능한 형태로 배포

- 젠킨스는 작업 내용을 아이템(Item) 단위로 정의하고 조건에 따라 자동으로 작업을 수행해 효율을 높이고 실수를 줄임

- 컨테이너 인프라 환경에서 젠킨스를 사용하는 주된 이유는 애플리케이션을 컨테이너로 만들고 배포하는 과정을 자동화하기 위함

- 자동화 환경은 단순히 젠킨스용 파드만을 배포해서는 만들어지지 않음

- 젠킨스는 컨트롤러와 에이전트 형태로 구성한 다음 배포해야 하며 여기에 필요한 설정을 모두 넣어야 함

- 애플리케이션을 배포하기 위한 환경을 하나하나 구성하는 것은 매우 복잡하며 번거로움

- 고정된 값이 아니므로 매니페스트로 작성해 그대로 사용할 수 없음   
  (매니페스트 파일 : 컴퓨팅에서 집합의 일부 또는 논리정연한 단위인 파일들의 그룹을 위한 메타데이터를 포함하는 파일)

- 구성 환경에 따라 많은 부분을 동적으로 변경 필요

- 커스터마이즈와 헬름은 동적인 변경 사항을 간편하고 빠르게 적용할 수 있도록 도와주는 도구

### <젠킨스 설치를 위한 간편화 도구 살펴보기>

- 이전에 Nginx 애플리케이션을 사용할려면 Deployment를 생성하고 이를 서비스로 노출하는 오브젝트 생성 과정을 총 두 번 진행함

- 이 적은 수의 오브젝트로 모든 종류의 애플리케이션을 사용자가 사용할 수 있는 형태로 구현할 수 없음

- 필요에 따라서 다수의 오브젝트를 사용해야 하는데, 3장에서 수많은 오브젝트를 한 번에 생성하는 매니페스트를 실행한 적이 있음

- MetalLB를 구동하는 데 필요한 수많은 오브젝트를 미리 정의된 하나의 매니페스트에 넣고 바로 실행

- 모든 환경에서 단순히 오브젝트를 정의한 대로만 사용한다면 젠킨스, 커스터마이즈, 헬름 등은 필요없음

- 사용자마다 필요한 환경적 요소가 모두 다르므로 젠킨스, 커스터마이즈, 헬름 등을 사용하여 요구사항에 맞게 변경

### 배포 간편화 도구 비교하기

- kubectl은 binary 실행 파일로 짜인 배포 도구

- kubectl이 없으면 직접 코드를 작성하여 API 서버에 명령을 내려야 함

- 커스터마이즈와 헬름은 kubectl을 좀 더 확장해서 복잡한 오브젝트와 구성 환경을 자동으로 맞추는 도구

<img src="https://user-images.githubusercontent.com/101415950/202900107-41476279-32c2-4387-9df9-723c2f0504f1.png" width="50%" height="50%">

- 큐브시티엘(kubectl)

	- 쿠버네티스에 기본으로 포홈된 커맨드라인 도구

	- 추가 설치 없이 바로 사용 가능

	- 오브젝트 생성과 쿠버네티스 클러스터에 존재하는 오브젝트, 이벤트 등의 정보를 확인하는 데 사용하는 활용도 높은 도구

	- 오브젝트의 명세가 정의된 Yaml 파일을 인자로 입력받아 파일 내용에 따라 오브젝트를 배포할 수 있음

	- 정의된 매니페스트 파일을 그대로 배포하기 때문에 개별적인 오브젝트를 관리하거나 배포할 때 사용하는 것이 좋음

	- <b>고정적인 값으로 설정된 매니페스트를 그대로 사용할 수 밖에 없음</b>

- 커스터마이즈(Kustomize)

	- 오브젝트를 사용자의 의도에 따라 유동적으로 배포 가능

	- 별도의 커스터마이즈 실행 파일을 활용해 커스터마이즈 명세를 따르는 yaml 파일을 생성 가능

	- yaml 파일이 이미 존재한다면 kubectl로도 배포할 수 있는 옵션(-k)이 있을 정도로 kubectl과 매우 밀접하게 동작

	- 커스터마이즈는 명세와 관련된 yaml 파일에 변수나 템플릿을 사용하지 않음

	- 명령어로 배포 대상 오브젝트의 이미지 태그와 레이블 같은 명세를 변경하거나 일반 파일을 이용해 config 맵과 시크릿을   
	  생성하는 기능을 지원
	  
	- 운영 중인 환경에서 배포 시 가변적인 요소를 적용하는 데 적합

	- <b>일부 내용을 가변적으로 변경해 사용 가능</b>

- 헬름(Helm)

	- 쿠버네티스 사용자의 70% 이상이 사용하고 있을 정도로 널리 알려진 도구

	- 오브젝트 배포에 필요한 사양이 이미 정의된 차트(Chart)라는 패키지를 활용

	- 앞선 두 가지 도구와 달리 헬름 차트 저장소가 온라인에 있기 때문에 패키지를 검색하고 내려받아 사용하기가 매우 간편

	- 헬름 차트는 자체적인 템플릿 문법을 사용하므로 가변 인자를 배포할 때 적용해 다양한 배포 환경에 맞추거나 원하는 조건을 적용 가능

	- 오브젝트를 묶어 패키지 단위로 관리하므로 단순한 1개의 명령어로 애플리케이션에 필요한 오브젝트들을 구성 가능

	- <b>매니페스트의 일부가 아닌 모든 내용을 설정할 수 있는 값을 제공해 필요에 따라 사용자 환경에 맞는 설정값으로 변경 가능</b>

<img src="https://user-images.githubusercontent.com/101415950/202900728-d33fdde1-01b0-46db-b07e-652a6dac7288.png" width="80%" height="80%">

### 커스터마이즈로 배포 간편화하기

- 커스터마이즈를 통한 배포는 kubectl에 구성되어 있는 매니페스트를 고정적으로 이용해야 하는 기존 방식을 유연하게 만듬

- 커스터마이즈는 Yaml 파일에 정의된 값을 사용자가 원하는 값으로 변경 가능

- kubectl을 사용한 쿠버네티스에서 오브젝트에 대한 수정 사항을 반영하려면 사용자가 직접 yaml 파일을 편집기 프로그램으로 수정해야 함

- 수정해야 하는 Yaml 파일이 매우 많거나 하나의 Yaml 파일로 환경이 다른 여러 개의 쿠버네티스 클러스터에 배포해야 해서   
  LABEL이나 NAME 같은 일부 항목을 수정해야 한다면 매번 일일이 고치는 데 많은 노력이 듬

- 커스터 마이즈는 이를 위해 kustomize 명령을 제공

- kustomize 명령과 create 옵션으로 kustomization.yaml이라는 기본 매니페스트를 만들고, 이 파일에 변경해야 하는 값들을 적용

- 그리고 build 옵션으로 변경할 내용이 적용된 최종 yaml 파일을 저장하거나 변경된 내용이 바로 실행되도록 지정

[예시]

- MetalLB 0.9 버전부터 쿠버네티스에서 MetalLB를 구성할 때 컨트롤러와 에이전트인 스피커가 통신할 때 보안을 위해 쿠버네티스의   
  시크릿 오브젝트 사용

- 이에 따라 기존에는 매니페스트 방법만 안내되었지만, 0.9부터는 복잡한 설치 과정을 간편화할 수 있도록 커스터마이즈 방법 추가 안내

<img src="https://user-images.githubusercontent.com/101415950/202900976-b7eaf335-15f5-4055-a3ac-8edfaa95b6f9.png" width="80%" height="80%">

- 커스터마이즈를 사용하여 MetalLB를 만드는 것은 명세서인 kustomization.yaml을 만드는 과정과 같음

- 만들어진 kustomization.yaml을 통해 원하는 내용이 담긴 MetalLB 매니페스트를 생성하고 이 매니페스트를 통해 배포하는 것

- 즉 커스터마이즈는 단순히 최종 매니페스트 생성을 도와주는 도구

<b>[실습]</b>

- 1-1. 커스터마이즈 명령을 사용하기 위해 kustomize-install.sh를 실행

- 1-2. 커스터 마이즈 압축 파일을 내려받은 후에 이를 해제하고 /usr/local/bin으로 옮겨놓을 것

- 1-3. 이후 헬름도 동일한 과정을 통해서 배시 셸에서 바로 실행할 수 있게 만들 것

```
[root@m-k8s ~]# ~/_Book_k8sInfra/ch5/5.2.2/kustomize-install.sh
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100 12.4M  100 12.4M    0     0  4562k      0  0:00:02  0:00:02 --:--:-- 5379k
kustomize install successfully
```
![image](https://user-images.githubusercontent.com/101415950/202901560-288ade11-efab-44ee-9139-ad571a43101a.png)

- 2-1. 커스터마이즈에서 리소스 및 주소 할당 영역(Pool)을 구성할 때 사용할 파일들을 확인하기 위해 ~/ch5/5.2.2로 디렉터리 이동

- 2-2. metallb-l2config.yaml,  metallb.yaml,  namespace.yaml이 있는지 확인

- 2-3. 3장에서 네임스페이스 설정 부분이 matallb.yaml 배포에 포함됐으나, 리소스에 여러가지 항목이 포함될 수 있음을 표현하기 위해   
       네임스페이스 분리

```
[root@m-k8s ~]# cd ~/_Book_k8sInfra/ch5/5.2.2
[root@m-k8s 5.2.2]# ls
kustomize-install.sh  metallb-l2config.yaml  metallb.yaml  namespace.yaml
```
![image](https://user-images.githubusercontent.com/101415950/202901874-8a495eef-ce5d-40f1-b08f-fc1284895023.png)

- 3-1. 커스터마이즈로 변경될 작업을 정의하기 위해 kustomization.yaml을 생성

- --namespace는 작업의 네임스페이스를 설정

- --resources 명령은 커스터마이즈 명령을 이용하여 kustomization.yaml을 만들기 위한 소스파일을 정의

- 4-1. cat 명령어를 통해 kustomization.yaml 확인(리소스, 네임스페이스 확인)

```
[root@m-k8s 5.2.2]# kustomize create --namespace=metallb-system --resources namespace.yaml,metallb.yaml,metallb-l2config.yaml
[root@m-k8s 5.2.2]# cat kustomization.yaml
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
resources:
- namespace.yaml
- metallb.yaml
- metallb-l2config.yaml
namespace: metallb-system
```
![image](https://user-images.githubusercontent.com/101415950/202902915-0f114fb5-9aaf-4714-9ba8-7388094c2751.png)

- 5-1. 설치된 이미지를 안정적인 버전으로 유지하기 위해 kustomize edit set image 옵션을 이용하여   
     MetalLB controller와 speaker의 이미지 태그를 v0.8.2로 지정

- 6-1. cat 명령어를 통해 kustomization.yaml 확인(이미지 태그 정보 v0.8.2 확인)

```
[root@m-k8s 5.2.2]# kustomize edit set image metallb/controller:v0.8.2
[root@m-k8s 5.2.2]# kustomize edit set image metallb/speaker:v0.8.2
[root@m-k8s 5.2.2]# cat kustomization.yaml
apiVersion: kustomize.config.k8s.io/v1beta1
kind: Kustomization
resources:
- namespace.yaml
- metallb.yaml
- metallb-l2config.yaml
namespace: metallb-system
images:
- name: metallb/controller
  newTag: v0.8.2
- name: metallb/speaker
  newTag: v0.8.2
```
![image](https://user-images.githubusercontent.com/101415950/202903166-43486f6a-c959-456a-8cd3-907205193d1d.png)

- 7-1. kustomize build 명령으로 MetalLB 설치를 위한 매니페스트를 생성

- 7-2. metallb-l2config.yaml을 통해 config 맵이 만들어졌으며 이미지 태그인 v0.8.2가 적용된 것을 확인

```
[root@m-k8s 5.2.2]# kustomize build
apiVersion: v1
kind: Namespace
[중략]
data:
  config: |
    address-pools:
    - name: metallb-ip-range
      protocol: layer2
      addresses:
      - 192.168.1.11-192.168.1.19
kind: ConfigMap
[중략]
        - --config=config
        image: metallb/controller:v0.8.2
[중략]
        image: metallb/speaker:v0.8.2
        imagePullPolicy: IfNotPresent
[생략]
```
![image](https://user-images.githubusercontent.com/101415950/202903580-49629efb-8899-4fa8-88b2-4ee985f9fcfb.png)

- 8-1. 이를 파일로 저장해 MetalLB를 배포할 수도 있음

- 8-2. 편의를 위해 아래 명령으로 빌드한 결과가 바로 kubectl apply에 인자로 전달돼 배포하도록 실행
```
[root@m-k8s 5.2.2]# kustomize build | kubectl apply -f -
namespace/metallb-system created
serviceaccount/controller created
serviceaccount/speaker created
podsecuritypolicy.policy/speaker created
role.rbac.authorization.k8s.io/config-watcher created
clusterrole.rbac.authorization.k8s.io/metallb-system:controller created
clusterrole.rbac.authorization.k8s.io/metallb-system:speaker created
rolebinding.rbac.authorization.k8s.io/config-watcher created
clusterrolebinding.rbac.authorization.k8s.io/metallb-system:controller created
clusterrolebinding.rbac.authorization.k8s.io/metallb-system:speaker created
configmap/config created
deployment.apps/controller created
daemonset.apps/speaker created
```
![image](https://user-images.githubusercontent.com/101415950/202903731-ced918b0-6e52-49fb-bb55-bedbe0bd7ac6.png)

- 9-1. MetalLB가 정상적으로 배포되었는지 아래 명령을 통해 확인

```
[root@m-k8s 5.2.2]# kubectl get pods -n metallb-system
NAME                          READY   STATUS    RESTARTS   AGE
controller-5f98465b6b-7hnms   1/1     Running   0          2m34s
speaker-92n5l                 1/1     Running   0          2m34s
speaker-dbsgr                 1/1     Running   0          2m34s
speaker-pgbfk                 1/1     Running   0          2m34s
speaker-v4wwl                 1/1     Running   0          2m34s
[root@m-k8s 5.2.2]# kubectl get configmap -n metallb-system
NAME     DATA   AGE
config   1      3m4s
```

![image](https://user-images.githubusercontent.com/101415950/202903881-c6a727b1-56dc-4c61-9656-3281fd79c518.png)

- 10-1. 아래 명령으로 커스터마이즈를 통해 고정한 MetalLB의 태그가 v0.8.2인지 확인

```
[root@m-k8s 5.2.2]# kubectl describe pods -n metallb-system | grep Image:
    Image:         metallb/controller:v0.8.2
    Image:         metallb/speaker:v0.8.2
    Image:         metallb/speaker:v0.8.2
    Image:         metallb/speaker:v0.8.2
    Image:         metallb/speaker:v0.8.2
```
![image](https://user-images.githubusercontent.com/101415950/202904012-c0e17e7c-2c20-4e77-9e97-e99518f70ad4.png)

- 11-1. Deployment 1개를 배포한 다음 LoadBalancer 타입으로 노출하고 IP가 정상적으로 할당되었는지 확인

```
[root@m-k8s 5.2.2]# kubectl create deployment echo-ip --image=sysnet4admin/echo-ip
deployment.apps/echo-ip created
[root@m-k8s 5.2.2]# kubectl expose deployment echo-ip --type=LoadBalancer --port=80
service/echo-ip exposed
[root@m-k8s 5.2.2]# kubectl get service echo-ip
NAME      TYPE           CLUSTER-IP     EXTERNAL-IP    PORT(S)        AGE
echo-ip   LoadBalancer   10.105.16.68   192.168.1.11   80:30582/TCP   16s
```
![image](https://user-images.githubusercontent.com/101415950/202904175-064f4569-27cb-4622-88a0-395be545bbdd.png)

- 12-1. 호스트 PC(또는 노트북)에 192.168.1.11을 입력해 echo-ip가 정상적으로 응답하는지 확인

![image](https://user-images.githubusercontent.com/101415950/202904250-ad08b0e9-eebe-4b74-9000-4ef9524ace45.png)

- 13-1. 다음 실습을 위해 MetalLB를 삭제 후 배포했던 echo-ip 관련 오브젝트도 함께 삭제, 그리고 홈 디렉터리로 이동

```
[root@m-k8s 5.2.2]# kustomize build | kubectl delete -f -
namespace "metallb-system" deleted
serviceaccount "controller" deleted
serviceaccount "speaker" deleted
podsecuritypolicy.policy "speaker" deleted
role.rbac.authorization.k8s.io "config-watcher" deleted
clusterrole.rbac.authorization.k8s.io "metallb-system:controller" deleted
clusterrole.rbac.authorization.k8s.io "metallb-system:speaker" deleted
rolebinding.rbac.authorization.k8s.io "config-watcher" deleted
clusterrolebinding.rbac.authorization.k8s.io "metallb-system:controller" deleted
clusterrolebinding.rbac.authorization.k8s.io "metallb-system:speaker" deleted
configmap "config" deleted
deployment.apps "controller" deleted
daemonset.apps "speaker" deleted
[root@m-k8s 5.2.2]# kubectl delete service echo-ip
service "echo-ip" deleted
[root@m-k8s 5.2.2]# kubectl delete deployment echo-ip
deployment.apps "echo-ip" deleted
[root@m-k8s 5.2.2]# cd ~
[root@m-k8s ~]#
```
![image](https://user-images.githubusercontent.com/101415950/202905166-ce4d457b-40ff-47b7-b0d0-b7f125e1384e.png)

<b>[커스터 마이즈에서 config 맵을 쓰는 다른 방법]</b>

- 커스터 마이즈에는 Config 맵을 리소스로 넣는 것이 아니라 Config 맵의 내용만을 읽어 들일 수 있도록 하는 옵션을 제공

- 이렇게 읽어 들인 Config 맵을 Generator라는 요소를 통해 등록

- Generator는 Config 맵이나 시크릿의 데이터를 입력하면 각 형식에 맞게 생성

- 하지만 이렇게 넣는 경우 기존과 같은 이름의 구성 요소들이 존재할 수 있음

- 중복을 방지하기 위해 커스터마이즈에서는 이름에 Hash를 추가로 적용

- 그러나 MetalLB는 고정된 Config 맵 이름을 읽도록 설계돼 있으므로 Hash가 추가된 Config 맵을 불러올 수 없음

- 그러므로 MetalLB에 Config 맵이 적용되지 않았기 때문에 로드밸런서 서비스에 IP가 할당되지 않음

- 커스터마이즈의 GeneratorOptions를 disableNameSuffixHash: true로 변경해 문제를 해결할 수 있음

- 그러나 이런 과정은 다소 실습하기에 번거로움이 있어서 Config 맵 자체를 리소스에 포함하여 실습 진행

<img src="https://user-images.githubusercontent.com/101415950/202907453-87aeaa2f-f1e2-44a5-a636-ccee4c7f9a51.png" width="80%" height="80%">

<b>[정리]</b>

- 커스터마이즈를 이용하면 MetalLB의 다양한 설정을 사용자의 입맛에 맞게 변경하고 구현할 수 있음

- 그러나 여러 가지 변경할 부분을 사용자가 직접 kustomization.yaml에 추가하고 최종적으로 필요한 매니페스트를 만들어 배포해야 함

- 이러한 다소 수동적인 작성 방식이 아닌 선언적으로 필요한 내용을 제공하고 이에 맞게 배포하기 위해 헬름을 사용

- 헬름은 커스터마이즈를 통해서 변경할 수 없었던 주소 할당 영역과 같은 값도 배포 시에 같이 변경 가능

### 헬름으로 배포 간편화하기

- 헬름을 통한 배포는 커스터마이즈에서 제한적이었던 주소 할당 영역과 같은 값을 대체하면서 간단하게 설치 가능

<b>[헬름의 작동 원리]</b>

- 헬름은 쿠버네티스에 패키지를 손쉽게 배포할 수 있도록 패키지를 관리하는 쿠버네티스 전용 패키지 매니저

- 일반적으로 패키지는 실행 파일뿐만 아니라 실행 환경에 필요한 의존성 파일과 환경 정보들의 묶음

- 패키지 매니저는 외부에 있는 저장소에서 패키지 정보를 받아와 패키지를 안정적으로 관리하는 도구

- 패키지 매니저는 다양한 목적으로 사용됨

- 그 중 가장 중요한 목적은 설치에 필요한 의존성 파일들을 관리하고 간편하게 설치할 수 있도록 도와주는 것

- 플랫폼별 패키지 매니저의 저장소 위치와 사용 목적은 다음과 같음

<img src="https://user-images.githubusercontent.com/101415950/202908714-6ebe643a-92a3-4c88-a2ca-2567fc345187.png" width="80%" height="80%">

- 패키지 매니저의 역할은 패키지의 손쉬운 설치와 관리

- 모든 패키지 매니저는 다음과 같은 기능이 있음

	- 패키지 검색

		- 설정한 저장소에서 패키지를 검색하는 기능을 제공

		- 이때 대부분 저장소는 목적에 따라 변경 가능

	- 패키지 관리

		- 저장소에서 패키지 정보를 확인하고, 사용자 시스템에 패키지 설치, 삭제, 업그레이드, 되돌리기 등 가능

	- 패키지 의존성 관리

		- 패키지를 설치할 때 의존하는 소프트웨어를 같이 설치하고, 삭제할 때 같이 삭제 가능

	- 패키지 보안 관리

		- 디지털 인증서와 패키지에 고유하게 발행되는 체크섬(checksum) 값으로 해당 패키지의 소프트웨어나 의존성 변조를 검사 가능

- 컨테이너 인프라 환경에서 애플리케이션을 배포하려면 ConfigMap, ServiceAccount, PV, PVC, Secret 등 애플리케이션 배포 구성에 필요한 모든 쿠버네티스 오브텍트를 작성 

- kubecel 명령을 실행해서 쿠버네티스 클러스터에 설치

- 이때 커스터마이즈를 사용하면 많은 부분을 환경에 맞춰 변경할 수 있지만, 주소 할당 영역과 같은 정보는 값의 형태가 아니라서 변경 불가

- 이런 경우에 헬름을 사용하면 주소 할당 영역도 변경 가능

<img src="https://user-images.githubusercontent.com/101415950/202909049-cdba1fb6-1801-413f-aca1-6e2e0399ad17.png" width="80%" height="80%">

- 다수의 오브젝트 배포 Yaml 파일은 파일 구분자인 '---'로 묶어 단일 Yaml로 작성해 배포하는 경우를 가정

- 이런 경우 변경 사항을 추적할 때 모든 내용이 한 Yaml 파일에 담겨 있기 때문에 여러 사람이 동시에 작업하면 충돌 발생 가능

- 이를 해결하기 위해 목적에 맞게 디렉터리를 만들고 Yaml 파일을 분리해 관리하면서 배포 시 디렉터리를 Kubectl apply -f의 인자로 넘김

- 이런 방식은 요구 조건에 변경되는 Yaml 파일을 매번 개별 디렉터리를 작성해야 하고 디렉터리가 늘어날 수 록 관리 영역 증가

- 헬름을 사용하면 요구 조건 별로 리소스를 편집하거나 변수를 넘겨서 처리하는 패키지를 만들 수 있음

- 이렇게 다양한 요구 조건을 처리할 수 있는 패키지를 차트(chart)라고 하며 이를 헬름 저장소에 공개해 여러 사용자와 공유

- 각 사용자는 공개된 저장소에 등록된 차트를 이용해서 애플리케이션을 원하는 형태로 쿠버네티스에 배포 가능

- 헬름은 배포한 애플리케이션을 업그레이드하거나 되돌릴 수 있는 기능, 삭제할 수 있는 기능을 제공

- 이처럼 헬름을 이용하면 하나의 패키지로 다양한 사용자가 원하는 각자의 환경을 구성할 수 있으며 이를 자유롭게 배포, 관리, 삭제 가능

- 헬름의 기본 저장소는 아티팩트허브(artifacthub.io)로, 다른 패키지 매니저처럼 외부에 있음

- 다른 저장소와 달리 아티팩트허브에서는 설치할 패키지에 대한 경로만을 제공

- 추후 헬름을 좀 더 알아볼 때 이 부분이 큰 차이점이 되므로 인지할 필요가 있음

<img src="https://user-images.githubusercontent.com/101415950/202909775-634ee5ec-b575-4b3d-bd0f-6a82053aaedf.png" width="80%" height="80%">

- 헬름의 전반적인 흐름

<img src="https://user-images.githubusercontent.com/101415950/202909939-6c26a65d-1bfc-4eee-a830-56c3dcd77cf8.png" width="80%" height="80%">

- 생산자 영역

	- 생산자가 헬름 명령으로 작업 공간을 생성하면 templates 디렉터리로 애플리케이션 배포에 필요한 yaml 파일과 구성 파일을 작성 가능

	- 이때 templates 디렉터리에서 조건별 분기, 값 전달 등을 처리할 수 있도록 value.yaml에 설정된 키를 사용

	- 이때 값이 전달되지 않으면 기본값으로 처리하도록 value.yaml에 설정rksmd

	- 이렇게 필요한 패키지의 여러 분기 처리나 배포에 대한 구성이 완료되면 생산자는 차트 이름, 목적, 배포되는 애플리케이션 버전과 같은   
	  패키지 정보를 Charts.yaml에 채워 넣음
	  
	- 앞의 과정을 모두 거쳐 차트 구성이 완료되면 생산자가 생산자 저장소에 업로드

	- 그리고 업로드한 생산자 저장소를 아티팩트 허브에 등록하면 사용자는 아티팩트 허브에서 생산자가 만든 저장소를 찾을 수 있음

- 아티팩트허브 영역

	- 아티팩트허브 검색을 통해 사용자가 찾고자 하는 애플리케이션 패키지를 검색하면 해당 패키지가 저장된 주소를 확인

	- 이렇게 확인한 주소는 각 애플리케이션을 개발하는 주체가 관리

	- 헬름 버전2에서는 이러한 차트 저장소를 개인이 아닌 CNCF가 관리했으나 헬름 버전3가 배포되고 나서는 CNCF가 관리해야 하는   
	  차트가 많아지면서 모든 차트 저장소는 개인 및 단체에서 직접 관리하도록 정책을 변경
	  
	- CNCD가 직접 관리하던 헬름 버전2의 차트 저장소는 하위 호완성을 위해서 내려받기 기능만 제공

- 사용자 영역

	- 사용자는 설치하려는 애플리케이션의 차트 저장소 주소를 아티팩트 허브에서 얻으면 헬름을 통해서 주소를 등록

	- 이를 최신으로 업데이트한 이후 차트를 내려받고 설치

	- 이렇게 헬름을 통해 쿠버네티스에 설치된 애플리케이션 패키지를 릴리스(Release)라고 함

	- 헬름을 통해 배포된 릴리스를 다시 차트를 사용해 업그레이드할 수 있고 원래대로 되돌릴 수 있음

	- 또한, 사용하지 않는 헬름 릴리스를 제거할 수 있음

- 틸러

	- 헬름 버전3에서는 헬름 버전2보다 간결한 구조로 내부 구성을 변경해 기존의 구성 요소가 다수 사라짐

	- 헬름 버전2는 헬름 클라이언트를 설치하고 클라이언트가 쿠버네티스 API 서버와 통신하면서 오브젝트를 관리하는 방식

	- 이를 위해 틸러(Tiller)라는 서버를 설치

	- 이외에도 쿠버네티스와 틸러가 통신하기 위한 권한 설정 등이 필요

	- 헬름 버전3에서는 틸러는 사라진 구성 요소

<b>헬름으로 MetalLB 한 번에 만들기</b>

- 1-1. 헬름 명령을 사용하기 위해 ch5/5.2.3/helm-install.sh를 실행하여 헬름 설치

- 1-2. DESIRED_VERSION 환경변수를 설정해 헬름 버전을 최신 버전이 아닌 v3.2.1로 고정하여 설치(호환성 이슈 방지)

- 1-3. 헬름 실행 파일도 /usr/local/bin에 위치

```
[root@m-k8s ~]# export DESIRED_VERSION=v3.2.1; ~/_Book_k8sInfra/ch5/5.2.3/helm-install.sh
Downloading https://get.helm.sh/helm-v3.2.1-linux-amd64.tar.gz
Verifying checksum... Done.
Preparing to install helm into /usr/local/bin
helm installed into /usr/local/bin/helm
```
![image](https://user-images.githubusercontent.com/101415950/202910936-b9e9645a-d5ed-43ac-b1d1-4fc8c0ca8bd9.png)

- 2-1. MetalLB를 설치하려면 헬름 차트를 등록할 주소를 알아야 하므로 아티팩트허브에서 metallb를 검색하여 주소 확인

<img src="https://user-images.githubusercontent.com/101415950/202911293-6576f60b-c636-4fc2-9844-867d235c9175.png" width="80%" height="80%">

- 3-1. 상단에 위치한 아이템을 눌러 metallb 차트에 대한 정보를 확인

- 3-2. metallb 아이템을 클릭하면 차트에 대한 상세한 내용을 확인

<img src="https://user-images.githubusercontent.com/101415950/202911349-86ba124e-63b5-44a4-9ecf-75c9cbd89045.png" width="80%" height="80%">

- 4-1. metallb의 상세 페이지에서는 차트 저장소(helm-charts) 등록법 외에도 차트에 대한 다양한 정보를 함께 제공

- 4-2. 상세 페이지를 통해서 추가해야 하는 차트 주소 및 등록하는 방법도 함께 확인 가능

- 4-3. 아무런 설정값의 변경없이 기본적으로 제공하는 애플리케이션 버전(0.8.2)도 확인이 가능

<img src="https://user-images.githubusercontent.com/101415950/202911465-3bdcd889-8ff1-4e65-b2b8-7145de097b97.png" width="80%" height="80%">

- 5-1. 실제로 저장소를 helm repo add 명령으로 등록해서 MetalLB를 설치할 준비를 실시

- 5-2. 헬름 차트 저장소인 https://iac-source.github.io/helm-charts는 저자가 만든 저장소로, 아티팩트허브에는 이 경로만을 표시

- 5-3. edu는 헬름 차트 저장소를 대표하는 이름의 역할을 하는 것으로 자유롭게 변경 등록 가능 (책에서는 edu를 사용)

```
[root@m-k8s ~]# helm repo add edu https://iac-source.github.io/helm-charts
"edu" has been added to your repositories
```
![image](https://user-images.githubusercontent.com/101415950/202911667-a9b04e1e-5b1f-41b1-afc9-f91f4ce8b130.png)

- 6-1. 헬름 차트 저장소가 정상적으로 등록됐는지 helm repo list 명령으로 저장소 목록 확인 (edu 차트 저장소 등록 확인됨)
```
[root@m-k8s ~]# helm repo list
NAME    URL
edu     https://iac-source.github.io/helm-charts
```
![image](https://user-images.githubusercontent.com/101415950/202911728-a6489074-4f95-4e5d-bdd4-64a1faf4e4bd.png)

- 7-1. 헬름으로 차트 저장소를 추가한 시점의 차트를 로컬 캐시에 저장해 install과 같은 작업 수행시 먼저 로컬에 있는 캐시 차트 정보를 참조

- 7-2. 저장소 추가 이후에 변경된 차트가 있다면 변경된 정보를 캐시에 업데이트할 수 있도록 아래 명령을 통해 최신 차트 정보를 동기화

- 7-3. 이는 관습적으로 이루어지는 것으로 현재의 랩에서는 필요한 요소는 아니지만 이렇게 진행하는 것이 향후 문제를 방지할 수 있음

```
[root@m-k8s ~]# helm repo update
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "edu" chart repository
Update Complete. ⎈ Happy Helming!⎈
```
![image](https://user-images.githubusercontent.com/101415950/202911891-de22d7a6-6909-4c60-b443-b5b872a29721.png)

- 8-1. 앞서 등록 및 업데이트한 저장소 edu로부터 MetalLB를 설치

- 8-2. 헬름 차트를 설치할 때 사용하는 명령어는 helm install이며 커스터마이즈와 다르게 인자를 바로 명령줄에서 받아서 처리

- 8-3. 현재 사용하는 인자는 다음과 같음

	- --namespace
	
		- 헬름 차트를 통해 생성되는 애플리케이션이 위치할 네임스페이스를 지정
	
	- --create-namespace
	
		- 네임스페이스 옵션으로 지정된 네임스페이스가 존재하지 않는 경우 네임스페이스를 생성
	
	- --set

		- 헬름에서 사용할 변수를 명령 인자로 전달

		- key1=value1, key2=value2와 같이 쉼표를 사용해 한 줄에서 여러 인자를 넘겨줄 수 있음

		- 그러나 가독성을 높이기 위해 책에서는 이를 사용하지 않음

- 8-4. 일반적으로 배포 이후에 간략한 메시지와 함께 제작자가 작성한 사용 설명서가 함께 출력

- 8-5. 이를 통하여 배포가 완료됐음을 확인

- 8-6. 이후 실습에서 설치하는 헬름 차트는 지금보다 더 많은 부분의 인자를 입력받으므로 사전에 구성된 스크립트를 통해 차트 설치 예정

```
[root@m-k8s ~]# helm install metallb edu/metallb \
> --namespace=metallb-system \
> --create-namespace \
> --set controller.tag=v0.8.3 \
> --set speaker.tag=v0.8.3 \
> --set configmap.ipRange=192.168.1.11-192.168.1.29
NAME: metallb
LAST DEPLOYED: Mon Nov 21 00:53:24 2022
NAMESPACE: metallb-system
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
MetalLB load-balancer is successfully installed.
1. IP Address range 192.168.1.11-192.168.1.29 is available.
2. You can create a LoadBalancer service with following command below.
kubectl expose deployment [deployment-name] --type=LoadBalancer --name=[LoadBalancer-name] --port=[external port]
```
![image](https://user-images.githubusercontent.com/101415950/202912022-c9d67ada-5890-42aa-993c-64eb1606b9c8.png)

- 9-1. 설치된 MetalLB가 정상적인 상태인지 배포상태 확인

```
[root@m-k8s ~]# kubectl get pods -n metallb-system
NAME                          READY   STATUS    RESTARTS   AGE
controller-85478cc585-8qjwc   1/1     Running   0          7m32s
speaker-hxnjz                 1/1     Running   0          7m32s
speaker-k59jv                 1/1     Running   0          7m32s
speaker-lgvz8                 1/1     Running   0          7m32s
speaker-zktzw                 1/1     Running   0          7m32s
[root@m-k8s ~]# kubectl get configmap -n metallb-system
NAME     DATA   AGE
config   1      7m52s
```
![image](https://user-images.githubusercontent.com/101415950/202912402-692249af-5782-4bdf-bb3b-e98b4cac3cdb.png)

- 10-1. 아래 명령으로 헬름 set 옵션을 통해서 변경된 MetalLB의 태그가 v0.8.3인지 확인

```
[root@m-k8s ~]# kubectl describe pods -n metallb-system | grep Image:
    Image:         metallb/controller:v0.8.3
    Image:         metallb/speaker:v0.8.3
    Image:         metallb/speaker:v0.8.3
    Image:         metallb/speaker:v0.8.3
    Image:         metallb/speaker:v0.8.3
```

- 11-1. Deployment를 1개 배포하고 이를 LoadBalancer 타입으로 노출하고 IP가 정상적으로 할당되었는지 확인

```
[root@m-k8s ~]# kubectl create deployment echo-ip --image=sysnet4admin/echo-ip
deployment.apps/echo-ip created
[root@m-k8s ~]# kubectl expose deployment echo-ip --type=LoadBalancer --port=80
service/echo-ip exposed
[root@m-k8s ~]# kubectl get service echo-ip
NAME      TYPE           CLUSTER-IP      EXTERNAL-IP    PORT(S)        AGE
echo-ip   LoadBalancer   10.101.83.251   192.168.1.11   80:32393/TCP   12s
```
![image](https://user-images.githubusercontent.com/101415950/202912666-e9a77ace-a3b1-47d4-b9ec-693d2b12cd8a.png)

- 12-1. 호스트 노트북 또는 PC의 브라우저에 192.168.1.11을 입력하여 echo-ip가 정상적으로 응답하는지 확인
![image](https://user-images.githubusercontent.com/101415950/202912694-9352d0b0-177b-4584-a773-3684d1690c5d.png)

- 13-1. 이후 실습에서 MetalLB는 계속 사용할 것이므로, 배포했던 echo-ip 관련 오브젝트만 삭제

```
[root@m-k8s ~]# kubectl delete service echo-ip
service "echo-ip" deleted
[root@m-k8s ~]# kubectl delete deployment echo-ip
deployment.apps "echo-ip" deleted
```
![image](https://user-images.githubusercontent.com/101415950/202912741-e7070f58-8f3b-4d3a-b66f-34a1e09f79a7.png)

<b>[헬름에 필요한 set 값을 확인하는 방법]</b>

- 헬름에서 가변적인 인자를 사용하기 위해 --set 이후에 인자를 선언

- 3장의 custom-columns에서 값을 확인하는 법과 매우 유사

- 적용하려는 차트에 있는 values.yaml의 내용

```
controller:
  image: metallb/controller
  tag: v0.8.2
speaker:
  image: metallb/speaker
  tag: v0.8.2
configmap:
  ipRange: 192.168.1.11-192.168.1.13
```
<img src="https://user-images.githubusercontent.com/101415950/202913448-f5cba8ec-2a5a-4d00-b407-c3cc987765d9.png" width="50%" height="50%">

- 그리고 이 값을 치환하면 아래와 같음

	- controller.tag = v0.8.3

	- speaker.tag = v0.8.3

	- configmap.ipRange = 192.168.1.11-192.168.1.29

- 위와 같은 방법으로 헬름에서 변경하고 싶은 변수를 쉽게 확인하고 적용 가능

- helm show values [차트] 명령어로 터미널에서 간략히 확인 가능

<b>[정리]</b>

- 커스터 마이즈를 이용하면 매니페스트를 동적으로 이용할 수 있지만 일부 값들은 변경할 수 없는 한계가 있음을 확인

- 헬름을 이용하면 이 한계를 뛰어넘어 필요한 값을 동적으로 선언하고 사용할 수 있음을 확인

### <젠킨스 설치 및 설정하기>

- 헬름으로 젠킨스를 좀 더 쉽게 설치할 수 있지만 사전 준비가 필요

### 헬름으로 젠킨스 설치하기

- 이전 실습 때 사용했던 차트 저장소 edu에는 앞으로 사용할 모든 애플리케이션이 차트로 등록됨

- 그러므로 차트 저장소를 새로 등록하지 않고 바로 애플리케이션을 설치

[실습 저장소인 edu의 차트 목록]
<img src="https://user-images.githubusercontent.com/101415950/203037493-fcc774e6-debc-4199-b4cc-08414f477a7c.png" width="80%" height="80%">

- 1-1. 젠킨스로 지속적 통합을 진행하는 과정에서 컨테이너 이미지를 레지스트리에 Push하는 단계가 있음

- 1-2. 이때 이미지를 저장하는 레지스트리는 앞서 '4.4.2 레지스트리 구성하기'에서 구성한 이미지 레지스트리를 사용

- 1-3. 따라서 4장의 실습을 먼저 진행해야함

[4장 실습]
```
cd ~/_Book_k8sInfra/ch4/4.3.4/
cat Dockerfile
docker build -t multistage-img .
docker rmi $(docker images -f dangling=true -q)

~/_Book_k8sInfra/ch4/4.4.2/create-registry.sh
docker ps -f name=registry
docker tag multistage-img 192.168.1.10:8443/multistage-img
docker push 192.168.1.10:8443/multistage-img
docker images | grep multi
docker rmi -f (이미지 ID)
```

[레지스트리 확인]
```
[root@m-k8s ~]# docker ps -f name=registry
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                             NAMES
b9470db0a54b        registry:2          "/entrypoint.sh /etc…"   16 minutes ago      Up 16 minutes       5000/tcp, 0.0.0.0:8443->443/tcp   registry
```
![image](https://user-images.githubusercontent.com/101415950/203043075-84edfcbf-f956-421d-9524-73b2701aef2e.png)

- 2-1. 헬름으로 설치되는 젠킨스는 파드에서 동작하는 애플리케이션이므로 PV를 마운트하지않으면 파트가 다시 시작될 때   
       내부 볼륨에 저장하는 모든 데이터가 삭제됨

- 2-2. 이를 방지하기 위해 에플리케이션의 PV가 NFS를 통해 프로비저닝될 수 있게 NFS 디렉터리를 /nfs_shared/jenkins에 생성

- 2-3. 미리 정의된 nfs-exporter.sh jenkins를 실행(NFS용 디렉터리 생성 및 이를 NFS 서비스로 생성하는 과정이 담김)     
       (3.4.3 PV와 PVC 참조)

```
[root@m-k8s ~]# ~/_Book_k8sInfra/ch5/5.3.1/nfs-exporter.sh jenkins
Created symlink from /etc/systemd/system/multi-user.target.wants/nfs-server.service to /usr/lib/systemd/system/nfs-server.service.
```
![image](https://user-images.githubusercontent.com/101415950/203044833-a05beb08-e889-4445-a591-65cf0146d393.png)

- 3-1. 만들어진 디렉터리에 부여된 사용자 ID(uid)와 그룹 ID(gid)의 번호를 -n 옵션으로 확인

- 3-2. 0번은 root 사용자에 속해있다는 의미

```
[root@m-k8s ~]# ls -n /nfs_shared
total 0
drwxr-xr-x. 2 0 0 6 Nov 21 20:44 jenkins
```
![image](https://user-images.githubusercontent.com/101415950/203045034-aa6bcdb4-bec1-44ee-abf9-fc002fc7fc7f.png)

- 4-1. 젠킨스를 헬름 차트로 설치해 애플리케이션을 사용하게 되면 젠킨스의 여러 설정 파일과 구성파일들이 PVC를 통해 PV에 파일로 저장

- 4-2. 이때 PV에 적절한 접근 ID를 부여하지 않으면 PVC를 사용해 파일을 읽고 쓰는 기능에 문제가 발생할 수 있음

- 4-3. 이를 방지하기 위해 하기 명령어로 젠킨스 PV가 사용한 NFS 디렉터리에 대한 접근ID(uid, gid)를 1000번으로 설정

- 4-4. 1000번으로 설정한 이유는 젠킨스 컨트롤러 이미지에서 기본적으로 사용하는 uid와 gid가 1000번이기 때문

```
[root@m-k8s ~]# chown 1000:1000 /nfs_shared/jenkins/
[root@m-k8s ~]# ls -n /nfs_shared
total 0
drwxr-xr-x. 2 1000 1000 6 Nov 21 20:44 jenkins
```
![image](https://user-images.githubusercontent.com/101415950/203045816-376c35cc-318f-4eed-8b8c-d4575153ffe5.png)

- 5-1. 젠킨스는 사용자가 배포를 위해 생성한 내용과 사용자 계정 정보, 사용하는 플러그인 등 데이터를 저장하기 위해 PV와 PVC 구성이 필요

- 5-2. 사전 구성된 jenkins-volume.yaml을 이용하여 PV와 PVC를 구성하고, 구성된 PV와 PVC가 Bound 상태인지 확인

```
[root@m-k8s ~]# kubectl apply -f ~/_Book_k8sInfra/ch5/5.3.1/jenkins-volume.yaml
persistentvolume/jenkins created
persistentvolumeclaim/jenkins created
[root@m-k8s ~]# kubectl get pv jenkins
NAME      CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM             STORAGECLASS   REASON   AGE
jenkins   10Gi       RWX            Retain           Bound    default/jenkins                           17s
[root@m-k8s ~]# kubectl get pvc jenkins
NAME      STATUS   VOLUME    CAPACITY   ACCESS MODES   STORAGECLASS   AGE
jenkins   Bound    jenkins   10Gi       RWX                           23s
```
![image](https://user-images.githubusercontent.com/101415950/203052173-023c5055-7db6-4cbe-af84-3ae3b29f544c.png)

- 6-1. 젠킨스를 설치하는 데 필요한 인자가 많으므로 사전 구성된 jenkins-install.sh를 실행하여 젠킨스를 설치

- 6-2. 실행 후 나타나는 젠킨스 릴리스에 대한 정보 확인

	- NAME
	
		- jenkins가 설치된 릴리스 이름

		- 이후 헬름 관련 명령으로 젠킨스를 조회, 삭제, 변경 등을 수행할 때 이름을 사용

	- NAMESPACE

		- default 젠킨스가 배포된 네임스페이스는 default 입니다.

	- REVISION: 1

		- 배포된 릴리스가 몇 번째로 배포된 것인지 알려줌(이 젠킨스는 처음 설치된 것임을 알 수 있음)

		- helm upgrade 명령어를 사용해 젠킨스의 버전을 업그레이드할때마다 1씩 증가됨

		- 업그레이드 작업 후 이전 버전으로 돌아가기 위해 helm rollback 명령어 사용 가능

		- helm rollback 명령어 사용 시 REVISION 번호를 직접 지정하여 특정 리비전으로 돌아가도록 설정 가능

	- NOTES

		- 설치와 관련된 안내 사항을 몇 가지 표시하고 있음

		- 1번 항목은 젠킨스의 관리자 비밀번호를 얻어오기 위한 명령어

		- 2번은 젠킨스가 구동되는 파드에 접속할 수 있도록 외부 트래픽을 쿠버네티스의 파드로 전달하게 만드는 설정

		- 외부에서 쉽게 접속하기 위해 이 실습에서는 트래픽을 전달하는 설정 대신 로드밸런서 사용

		- 3번은 표시된 admin은 젠킨스 접속 시 사용할 유저 이름

```
[root@m-k8s ~]# ~/_Book_k8sInfra/ch5/5.3.1/jenkins-install.sh
NAME: jenkins
LAST DEPLOYED: Mon Nov 21 21:17:37 2022
NAMESPACE: default
STATUS: deployed
REVISION: 1
NOTES:
1. Get your 'admin' user password by running:
  printf $(kubectl get secret --namespace default jenkins -o jsonpath="{.data.jenkins-admin-password}" | base64 --decode);echo
2. Get the Jenkins URL to visit by running these commands in the same shell:
  NOTE: It may take a few minutes for the LoadBalancer IP to be available.
        You can watch the status of by running 'kubectl get svc --namespace default -w jenkins'
  export SERVICE_IP=$(kubectl get svc --namespace default jenkins --template "{{ range (index .status.loadBalancer.ingress 0) }}{{ . }}{{ end }}")
  echo http://$SERVICE_IP:80/login

3. Login with the password from step 1 and the username: admin

4. Use Jenkins Configuration as Code by specifying configScripts in your values.yaml file, see documentation: http:///configuration-as-code and examples: https://github.com/jenkinsci/configuration-as-code-plugin/tree/master/demos

For more information on running Jenkins on Kubernetes, visit:
https://cloud.google.com/solutions/jenkins-on-container-engine
For more information about Jenkins Configuration as Code, visit:
https://jenkins.io/projects/jcasc/
```
![image](https://user-images.githubusercontent.com/101415950/203052925-8f0c2464-c7dc-4aff-a965-4d335075c890.png)

- 7-1. Deployment가 정상적으로 배포되었는지 확인

```
[root@m-k8s ~]# kubectl get deployment
NAME      READY   UP-TO-DATE   AVAILABLE   AGE
jenkins   1/1     1            1           6m50s
```
![image](https://user-images.githubusercontent.com/101415950/203054894-7622041a-59af-4ec0-a775-f2caf26d426e.png)

- 8-1. 배포된 젠킨스가 외부에서 접속할 수 있는 상태인지 서비스 상태 확인(192.168.1.11로 젠킨스가 외부에 노출됨)

```
[root@m-k8s ~]# kubectl get service jenkins
NAME      TYPE           CLUSTER-IP      EXTERNAL-IP    PORT(S)        AGE
jenkins   LoadBalancer   10.109.36.244   192.168.1.11   80:30392/TCP   7m4s
```
![image](https://user-images.githubusercontent.com/101415950/203055136-d3924481-85f7-45cb-9a59-478dfb71abc5.png)

- 9-1. 젠킨스가 마스터 노드에 있는 것을 확인(마스터에도 파드가 배포될 수 있는지 의문사항이 생김)

```
[root@m-k8s ~]# kubectl get pod -o wide
NAME                       READY   STATUS    RESTARTS   AGE     IP              NODE    NOMINATED NODE   READINESS GATES
jenkins-76496d9db7-826gs   2/2     Running   0          7m13s   172.16.171.77   m-k8s   <none>           <none>
```
![image](https://user-images.githubusercontent.com/101415950/203055308-dc1a26ea-1f47-4382-adb1-9e9f798538d4.png)

- 10-1. 하기 명령을 통해서 상태를 비교(nl은 number lines of files의 약자로 줄 번호를 추가하는 역할)

```
[root@m-k8s ~]# kubectl get node m-k8s -o yaml | nl
     1  apiVersion: v1
     2  kind: Node
[중략]
    14      kubernetes.io/arch: amd64
    15      kubernetes.io/hostname: m-k8s
    16      kubernetes.io/os: linux
[중략]
   164    taints:
   165    - effect: NoSchedule
   166      key: node-role.kubernetes.io/master
[생략]
[root@m-k8s ~]# kubectl get deployments jenkins -o yaml | nl
     1  apiVersion: apps/v1
     2  kind: Deployment
     3  metadata:
     4    annotations:
     5      deployment.kubernetes.io/revision: "1"
     6      meta.helm.sh/release-name: jenkins
[중략]
   562        tolerations:
   563        - effect: NoSchedule
   564          key: node-role.kubernetes.io/master
   565          operator: Exists
[생략]
```
![image](https://user-images.githubusercontent.com/101415950/203056207-feab872f-5076-4e86-82ff-83d458798ada.png)
![image](https://user-images.githubusercontent.com/101415950/203056269-d77a1cc2-5ca6-44a2-b1e1-31f55eadfc00.png)

- 테인트(taints)와 톨러레이션(tolerations)으로 인해 젠킨스가 마스터 노드에 있음
	
- 테인트(taints)는 손에 잡기 싫은 것, 피하고 싶은 것, 가지말았으면 하는 것을 의미

- 테인트가 설정되면 그곳은 설거지가 끝난 이후 수채구멍과 같음

- 상황에 따라 테인트가 설정되어 있는 곳을 꼭 만져야 하는 경우가 있음

- 그러기 위해 톨러레이션, 즉 참아내는 인내가 필요

- 쿠버네티스의 테인트와 톨러레이션은 사전적인 의미와 반대

- 매우 특별하게 취급되어야 하는 곳에 테인트를 설정해, 쉽게 접근하지 못하는 소중한 것으로 설정

- 그리고 톨러레이션이라는 특별한 키를 가져야만 이곳에 출입 가능

- 즉 현재 상태에서는 마스터 노드에 테인트가 설정되어 있어 특별한 목적으로 사용되는 노드라는 것을 명시해둠

- 일반적으로 마스터 노드 이외에도 GPU 노드, DB 전용 노드 등의 특별한 목적으로 사용될 때 주로 사용

- 이 책에서는 관리의 편의를 위해 젠킨스 컨트롤러가 여러 곳에 스케쥴되지 않고 마스터 노드인 m-k8s에서만 스케쥴될 수 있도록 구성

- 앞으로 컨트롤러를 가지는 애플리케이션 배포 시 동일하게 마스터 노드에 컨트롤러를 구성

- 현재의 젠킨스 배포 구조는 다음 그림과 같음

<img src="https://user-images.githubusercontent.com/101415950/203066529-e68ade77-3e3b-413a-ac56-60e02ea3c658.png" width="80%" height="80%">

- 테인트와 톨러레이션은 관계를 정의하는 것에 따라 배포를 상당히 유연하게 만들 수 있음

- 테인트는 키(key)와 값(value) 그리고 키와 값에 따른 효과(effect)의 조합을 통해 테인트를 설정한 노드에 파드 배치 기준을 설정

- 톨러레이션은 테인트와 마찬가지로 키(key), 값(value), 효과(effect)를 가지고 있으며 이외에 연산자(operator)를 추가로 가짐

- 키와 값의 조합은 테인트를 설정한 노드가 어떤 노드인지를 구분하기 위해 사용

- 키는 필수로 설정해야 하지만 값은 생략 가능

- key: node-role.kubernetes.io/master는 이 노드가 마스터 역할을 한다는 것을 나타내기 위해 작성된 것

- 효과는 테인트와 톨러레이션의 요소인 키 또는 값이 일치하지 않는 파드가 노드에 스케쥴되려고 하는 경우 어떤 동작을 할 것인지 나타냄

- effect에 다른 노드의 동작은 하기 표와 같음

<img src="https://user-images.githubusercontent.com/101415950/203069310-d67d707c-46d1-412f-8788-7b229d6bfbc6.png" width="80%" height="80%">

- 톨러테이션은 테인트가 설정된 노드로 들어가기 위한 특별한 열쇠의 역할을 하며 키와 효과는 반드시 일치해야 함

- 톨러테이션은 키, 값, 효과를 사용하여 연산자를 통해 비교한 후 조건에 맞는 테인트를 식별

- 연산자는 기본적으로 Equal로 동작하여 테인트와 톨러레이션을 비교하는 역할 수행

- 키의 효과 중 생략된 요소가 있다면 해당 요소는 묵시적으로 모든 키 혹은 모든 효과를 의미

- 연산자를 생략할 경우 묵시적으로 Equal을 의미

- 조건 판단 결과 테인트와 톨러레이션의 조건이 맞다면 테인트가 설정된 노드에 톨러테이션을 가진 파드를 배치 가능

- 조건이 맞는 경우는 Equal 연산자 사용 시 키, 값, 효과까지 일치하는 경우를 뜻함

- Exists의 경우에는 비교할 키와 값이 존재한다는 가정으로 테인트에 진입할 수 있는 만능 키로 바꿔주는 역할을 함(간단하지 않음)

- Exists 연산자 사용 시 값은 반드시 생략해야 하며 이 상태에서 키와 효과의 일치 여부를 판단

- 키와 효과를 모두 생략한 Exists 연산자만 사용 시 테인트의 키와 효과는 모든 키와 모든 효과를 의미하므로    
  Exists 연산자 하나만으로도 테인트가 설정된 모든 노드에 대해서 해당 톨러테이션을 설정된 파드를 배포 가능

[테인트와 톨러레이션 조합에 따른 파드가 할당되는 조건과 안되는 경우]
<img src="https://user-images.githubusercontent.com/101415950/203072133-18009b50-e37e-47bc-920a-c7de187fb728.png" width="80%" height="80%">

<b>[호스트 디렉터리와 젠킨스 컨트롤러의 ID 관계]</b>

- 젠킨스 컨트롤러 설치 후에 내부의 유저 ID와 그룹 ID를 살펴보면 1000번으로 설정돼 있는 것을 확인 가능

```
[root@m-k8s ~]# kubectl exec -it jenkins-76496d9db7-826gs -- cat /etc/passwd
Defaulting container name to jenkins.
[중략]
dbus:x:81:81:System message bus:/:/sbin/nologin
jenkins:x:1000:1000::/var/jenkins_home:/bin/bash
```
![image](https://user-images.githubusercontent.com/101415950/203057099-d411b09c-a59b-4995-bade-eade85155c84.png)

- 따라서 PV로 사용되는 NFS 디렉터리의 접근 ID를 동일하게 설정하지 않는다면 젠킨스 컨트롤러에서 이루어지는 작업들이   
  정상적으로 수행되지 않고 'fatal: unable to look up current user in the passwd file: no such user'와 같은 에러 발생

- 젠킨스 설치 시 환경변수를 설정해서 해결하는 방법이 있으나 이는 수정해야 할 것들이 많음

- 현재의 랩 환경에서 가장 간단한 방법인 호스트 시스템의 ID와 젠킨스 컨트롤러 ID를 일치시켜 주는 방법으로 해결 가능

<b>[헬름으로 설치하는 애플리케이션 초기화하는 법]</b>

- 헬름을 통해 젠킨스가 잘 설치되는 경우도 있지만 시스템 및 환경에 따라서 Ready 값이 '0/1'에서 멈춰 있는 경우도 있음

- 이 경우에는 kubectl get pods 명령으로 상태를 추가 확인하고 확인 결과가 init:0/1 상태(초기화 컨테이너 구동 대기)인지 확인

- 위 경우는 주로 젠킨스에 필요한 파일(플러그인)을 내려받는 것이 느리거나 문제가 생긴 것을 뜻함

- 따라서 최대 20분 정도 대기한 후 해결되지 않는다면 하기 명령으로 내려받은 파일들을 삭제 및 초기화시킨 후 다시 젠킨스 설치

- 프로메테우스와 그라파나 설치 또는 사용 중에 문제가 발생한 경우 동일하게 문제 해결 가능

```
[root@m-k8s ~]# kubectl get deployment
NAME      READY   UP-TO-DATE   AVAILABLE   AGE
jenkins   0/1     1            1           23m

[root@m-k8s ~]# kubectl get pods
NAME                       READY   STATUS    RESTARTS   AGE
jenkins-76496d9db7-826gs   0/2     Running   0          24m

[root@m-k8s ~]# helm uninstall jenkins
release "jenkins" uninstalled

[root@m-k8s ~]# rm -rf /nfs_shared/jenkins/*
[root@m-k8s ~]# ~/_Book_k8sInfra/ch5/5.3.1/jenkins-install.sh
[생략]
```

<b>[jenkins-install.sh 내용 분석]</b>
```
#!/usr/bin/env bash
jkopt1="--sessionTimeout=1440"
jkopt2="--sessionEviction=86400"
jvopt1="-Duser.timezone=Asia/Seoul"
jvopt2="-Dcasc.jenkins.config=https://raw.githubusercontent.com/sysnet4admin/_Book_k8sInfra/main/ch5/5.3.1/jenkins-config.yaml"
jvopt3="-Dhudson.model.DownloadService.noSignatureCheck=true"

helm install jenkins edu/jenkins \
--set persistence.existingClaim=jenkins \
--set master.adminPassword=admin \
--set master.nodeSelector."kubernetes\.io/hostname"=m-k8s \
--set master.tolerations[0].key=node-role.kubernetes.io/master \
--set master.tolerations[0].effect=NoSchedule \
--set master.tolerations[0].operator=Exists \
--set master.runAsUser=1000 \
--set master.runAsGroup=1000 \
--set master.tag=2.249.3-lts-centos7 \
--set master.serviceType=LoadBalancer \
--set master.servicePort=80 \
--set master.jenkinsOpts="$jkopt1 $jkopt2" \
--set master.javaOpts="$jvopt1 $jvopt2 $jvopt3"

```


## 마크다운 언어 참조

https://gist.github.com/ihoneymon/652be052a0727ad59601
