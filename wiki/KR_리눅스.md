### 1. 리눅스란?

Linux는 1991년 Linus Torvals가 개발한 운영체제이다. Linux는 Unix 운영체제를 기반으로 만들어진 운영체제로 유닉스 클론 운영체제이다.

Unix와 마찬가지로 다중 사용자, 다중작업 다중 스레드를 지원하는 네트워크 운영체제를 의미한다.

또한 Unix가 애초부터 통신 네트워크를 지향해 설계된 것 처럼 Linux 역시 서버로 작동하는데 최적화 되어있다.

또한 Linux는 자유 소프트 라이센스로 누구나 소스코드를 활용, 수정 및 재 배포가 가능해서 지속적인 업그레이드가 이루어진다.

- **커널**
  - 시스템 리소스 관리와 하드웨어와 소프트웨어 간의 통신을 담당하는 Linux의 핵심 부분이다.
- **Shell**
  - 운영 체제와 상호 작용하는 명령줄 인터페이스이다.
- **파일 시스템**
  - 데이터가 저장되고 검색되는 방식을 구성한다. Linux는 루트(**`/`**)부터 시작하는 계층적 디렉터리 구조를 사용한다.
- **프로세스**
  - 프로그램의 실행 중인 인스턴스이다.
- **사용자 및 그룹 관리**
  - Linux는 여러 사용자가 리소스를 공유하고 액세스할 수 있는 다중 사용자 시스템이다.

---

### 2. 레드햇 vs 데비안 (시스템)

| 특징                        | 레드햇                                | 데비안                                        |
| --------------------------- | ------------------------------------- | --------------------------------------------- |
| **Package Manager**         | `yum` / `dnf`                         | `apt`                                         |
| **Package Format**          | RPM                                   | DEB                                           |
| **Release Cycle**           | RHEL로 고정, 페도라로 롤링            | 테스트 & 불안정 분기로 안정적인 릴리스 사이클 |
| **Default Init System**     | `systemd`                             | `systemd` (데비안 8 제시 이후)                |
| **Supported Architectures** | IBM Z 및 Power를 포함한 광범위한 범위 | i386 및 amd64에 중점을 둔 광범위한 범위       |
| **Security Updates**        | Red Hat에서 구독과 함께 제공          | Debian Security Team에서 제공                 |
| **Commercial Support**      | 레드햇에서 제공                       | 타사를 통해 제공                              |
| **Community**               | 커뮤니티 주도 혁신을 위한 페도라      | 데비안은 전적으로 커뮤니티 주도               |
| **Enterprise Focus**        | Red Hat Enterprise Linux로 강력함     | Debian stable을 통해 제공                     |

---

### 3. RedHat vs Debian (명령어 및 패키지 관리)

| 작업                               | Debian (APT 사용)                                                             | Red Hat (YUM/DNF 사용)                                                                                             |
| ---------------------------------- | ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| **패키지 설치**                    | `sudo apt install package_name`                                               | `sudo yum install package_name` 또는 `sudo dnf install package_name`                                               |
| **패키지 제거**                    | `sudo apt remove package_name`                                                | `sudo yum remove package_name` 또는 `sudo dnf remove package_name`                                                 |
| **패키지 검색**                    | `apt search package_name`                                                     | `yum search package_name` 또는 `dnf search package_name`                                                           |
| **패키지 인덱스 업데이트**         | `sudo apt update`                                                             | `sudo yum check-update` 또는 `sudo dnf check-update`                                                               |
| **패키지 업그레이드**              | `sudo apt upgrade`                                                            | `sudo yum update` 또는 `sudo dnf upgrade`                                                                          |
| **저장소 추가**                    | `sudo add-apt-repository 'deb [options] url distribution component'`          | `sudo yum-config-manager --add-repo repository_url` 또는 `sudo dnf config-manager --add-repo repository_url`       |
| **저장소 제거**                    | `sudo add-apt-repository --remove 'deb [options] url distribution component'` | `sudo yum-config-manager --remove-repo repository_url` 또는 `sudo dnf config-manager --remove-repo repository_url` |
| **설치된 패키지 목록**             | `apt list --installed`                                                        | `yum list installed` 또는 `dnf list installed`                                                                     |
| **파일을 제공하는 패키지 찾기**    | `apt-file search filename`                                                    | `yum provides filename` 또는 `dnf provides filename`                                                               |
| **사용하지 않는 패키지 자동 제거** | `sudo apt autoremove`                                                         | `sudo yum autoremove` 또는 `sudo dnf autoremove`                                                                   |
| **패키지 정보 보기**               | `apt show package_name`                                                       | `yum info package_name` 또는 `dnf info package_name`                                                               |
| **패키지 캐시 정리**               | `sudo apt clean`                                                              | `sudo yum clean all` 또는 `sudo dnf clean all`                                                                     |
| **파손된 의존성 확인**             | `sudo apt check`                                                              | `sudo yum check` 또는 `sudo dnf check`                                                                             |

---

### 4. 리눅스 시스템 관리 명령어

#### 시스템 모니터링

| 명령어   | 설명                                                                     | 설치 방법                                         |
| -------- | ------------------------------------------------------------------------ | ------------------------------------------------- |
| `top`    | 시스템에서 가장 많은 CPU를 사용하는 프로세스 목록을 실시간으로 보준다.   |                                                   |
| `htop`   | `top` 명령어의 확장 버전으로, 사용자 인터페이스가 개선되어 있다.         | `sudo apt install htop` / `sudo yum install htop` |
| `vmstat` | 시스템의 메모리, 프로세스, 인터럽트, CPU 활동 등에 대한 정보를 보여준다. |                                                   |

#### 디스크 사용량

| 명령어 | 설명                                                    |
| ------ | ------------------------------------------------------- |
| `df`   | 파일 시스템별로 사용 가능한 디스크 공간을 보여준다.     |
| `du`   | 특정 디렉토리나 파일이 사용하는 디스크 공간을 보여준다. |

#### 프로세스 관리

| 명령어  | 설명                                             |
| ------- | ------------------------------------------------ |
| `ps`    | 현재 실행 중인 프로세스 목록을 보여준다.         |
| `kill`  | 특정 PID(Process ID)를 가진 프로세스를 종료한다. |
| `pkill` | 프로세스 이름으로 프로세스를 종료한다.           |

#### 네트워크 관리

| 명령어     | 설명                                                         | 설치 방법                                                   |
| ---------- | ------------------------------------------------------------ | ----------------------------------------------------------- |
| `ifconfig` | 네트워크 인터페이스 구성을 보거나 수정한다.                  | `sudo apt install net-tools` / `sudo yum install net-tools` |
| `netstat`  | 네트워크 연결, 라우팅 테이블, 인터페이스 통계 등을 보여준다. |                                                             |
| `ss`       | 소켓 통계를 보여주며, `netstat`보다 더 빠르다.               |                                                             |

#### 시스템 정보

| 명령어  | 설명                                    |
| ------- | --------------------------------------- |
| `uname` | 시스템에 대한 정보를 보여준다.          |
| `lscpu` | CPU 아키텍처 정보를 보여준다.           |
| `lsblk` | 장착된 블록 디바이스의 목록을 보여준다. |

---

### 5. 리눅스 기본 명령어

| 명령어    | 설명                                                               |
| --------- | ------------------------------------------------------------------ |
| `ls`      | 디렉토리 내용을 나열한다.                                          |
| `cd`      | 현재 디렉토리를 변경한다.                                          |
| `pwd`     | 현재 작업 중인 디렉토리 경로를 출력한다.                           |
| `mkdir`   | 새 디렉토리를 생성한다.                                            |
| `rmdir`   | 비어 있는 디렉토리를 제거한다.                                     |
| `rm`      | 파일이나 디렉토리를 제거한다.                                      |
| `cp`      | 파일이나 디렉토리를 복사한다.                                      |
| `mv`      | 파일이나 디렉토리를 이동하거나 이름을 변경한다.                    |
| `touch`   | 비어 있는 파일을 생성하거나 기존 파일의 타임스탬프를 갱신한다.     |
| `echo`    | 인자로 전달된 텍스트/문자열을 출력한다.                            |
| `cat`     | 파일의 내용을 연결하여 보여준다.                                   |
| `more`    | 파일 내용을 한 페이지씩 표시한다.                                  |
| `less`    | `more`와 유사하지만, 앞뒤로 움직일 수 있다.                        |
| `head`    | 파일의 처음 부분을 표시한다, 기본적으로 처음 10줄을 보여준다.      |
| `tail`    | 파일의 마지막 부분을 표시한다, 기본적으로 마지막 10줄을 보여준다.  |
| `grep`    | 파일에서 패턴을 검색한다.                                          |
| `find`    | 디렉토리 계층에서 파일을 검색한다.                                 |
| `chmod`   | 파일 모드(권한)를 변경한다.                                        |
| `chown`   | 파일이나 디렉토리의 소유자를 변경한다.                             |
| `df`      | 디스크 사용량을 표시한다.                                          |
| `du`      | 파일 공간 사용량을 추정한다.                                       |
| `clear`   | 터미널 화면을 지운다.                                              |
| `exit`    | 셸 또는 현재 세션을 종료한다.                                      |
| `history` | 명령어 이력을 표시한다.                                            |
| `sudo`    | 다른 사용자의 권한으로 명령어를 실행한다, 기본적으로는 `root`이다. |
| `man`     | 명령어의 매뉴얼 페이지를 표시한다.                                 |
| `which`   | 셸 명령어의 전체 경로를 보여준다.                                  |

---

### 6. /etc/skel

/etc/skel 디렉토리는 Ubuntu를 포함한 Linux/Unix 시스템의 "템플릿" 디렉토리이다. useradd 또는 adduser와 같은 도구를 사용하여 새 사용자 계정을 생성하면 `/etc/skel` 의 내용이 새 사용자의 홈 디렉토리(예: `/home/username` )에 복사된된. 이렇게 하면 새 사용자가 몇 가지 기본 구성 파일과 디렉터리 구조로 시작할 수 있다.

#### /etc/skel 디렉토리 목적

- `/etc/skel` 내부의 파일과 디렉터리는 새로운 사용자에게 `.bashrc, .bash_profile` 또는 `.profile`과 같은 기본 구성 파일과 때로는 `Documents,Downloads,etc..` 와 같은 디렉토리를 제공하기 위한 것이다.
- 이러한 기본 구성 파일은 환경 변수, 셸 동작, 기본 경로 등을 설정한다.
- 시스템 관리자는 `/etc/skel` 의 내용을 수정하여 새로운 사용자를 위한 기본 환경을 사용자 정의할 수 있다. 예를 들어 특정 스크립트, 환경 변수 또는 사전 정의된 디렉터리 구조를 추가할 수 있다.

#### /etc/skel의 공통 파일

- `.bashrc`: 사용자가 새 셸을 열 때 실행되는 bash 셸 구성 파일
- `.profile`: 사용자 환경을 구성하기 위해 로그인 세션 중에 실행되는 스크립트
- `.bash_profile`: bash 쉘 사용자를 위한 .profile의 대안으로 로그인 시 실행
- `.bash_logout`: 사용자가 셸 세션에서 로그아웃할 때 실행되는 스크립트

#### /etc/skel 활용

- 예를 들어, 모든 신규 사용자가 프롬프트를 사용자 정의하는 `.bashrc` 파일을 받도록 하려면 `.bashrc` 파일을 `/etc/skel` 에 배치할 수 있다. 새 사용자를 생성하면 이 `.bashrc` 파일이 홈 디렉토리에 복사되고 사용자는 자동으로 사용자 정의된 프롬프트를 갖게 된다.

```bash
somaz /etc/skel$ ls -al
total 20
drwxr-xr-x   2 root root 4096 Apr 21  2022 .
drwxr-xr-x 119 root root 4096 Oct 24 17:25 ..
-rw-r--r--   1 root root  220 Feb 25  2020 .bash_logout
-rw-r--r--   1 root root 3771 Feb 25  2020 .bashrc
-rw-r--r--   1 root root  807 Feb 25  2020 .profile
```

#### /etc/skel 사용방법

`-m` 옵션과 함께 `useradd` 를 사용하거나 `adduser` 를 사용하여 새 사용자를 생성하면 `/etc/skel` 의 파일과 디렉터리가 새 사용자의 홈 디렉터리에 자동으로 복사된다.

```bash
sudo useradd -m somaz
```

- 이 명령은 새로운 사용자 somaz를 생성하고 /etc/skel의 내용을 /home/somaz에 복사된다.
- `-m` 옵션(또는 다른 도구에서 이에 상응하는 옵션)을 사용하지 않으면 사용자의 홈 디렉터리가 생성되지 않으며 `/etc/skel` 의 파일이 복사되지 않는다.

#### 이미 생성된 유저에게 /etc/skel 적용하는 방법

가끔식 또는 실수로 인해 `-m` 옵션을 붙이지 않거나 오류로 인해 skel이 복사되지 않아서, home 디렉토리가 생성되지 않는 경우가 있다.
해결 방법은 아래와 같다.

```bash
sudo su -

sudo mkdir /home/somaz
sudo cp -r /etc/skel/. /home/somaz
sudo chown -R somaz:somaz /home/somaz

# vi /etc/passwd
somaz:x:1001:1001::/home/somaz:/bin/sh -> somaz:x:1001:1001::/home/somaz:/bin/bash
```

- 위와 같이 적용하면 정상적으로 home 디렉토리가 생성되면서 bash shell이 적용되리 home 디렉토리에 `/etc/skel` 의 모든 파일이 복사된다.

---

### 7. Linux Kernel
운영 체제의 핵심: 커널은 모든 운영 체제의 핵심 부분이다. 하드웨어와 직접 통신하고 애플리케이션과 시스템 프로세스에 필수적인 서비스를 제공하는 계층이다.

Monolithic Kernel로서의 Linux 커널: Linux는 특히 " Monolithic" 커널이다. 즉, 대부분의 핵심 시스템 기능(예: 파일 시스템 관리, 장치 드라이버, 메모리 관리 등)이 단일 대형 바이너리 내에 포함되어 있음을 의미한다.

이는 모듈화 및 보안을 위해 이러한 구성 요소를 별도의 프로세스에 유지하지만 효율성이 떨어질 수 있는 마이크로커널 설계와 다르다.

#### Linux Kernel 주요 역할
커널은 하드웨어 자원 관리, 프로세스의 효율적인 운영 보장, 애플리케이션이 의존하는 필수 서비스 제공을 담당한다. 이러한 책임을 세분화해 보겠다.
- 프로세스 관리
- 메모리 관리
- 장치 관리
- 파일 시스템 관리
- 네트워크 스택

#### Linux 커널의 주요 구성요소
- 시스템 호출 인터페이스: 이는 사용자 공간 애플리케이션과 커널 사이의 게이트웨이이다. 시스템 호출을 통해 애플리케이션은 커널에서 파일 작업, 프로세스 제어, 네트워크 통신과 같은 특정 서비스를 요청할 수 있다.
- 커널 모듈: 커널에서 동적으로 로드할 수 있는 부분이다. 여기에는 장치 드라이버, 파일 시스템 드라이버 및 네트워크 프로토콜 처리기가 포함된다. 모듈은 시스템을 재부팅하지 않고도 로드 및 언로드할 수 있으므로 유연성을 제공한다.
- 프로세스 간 통신(IPC): 커널은 파이프, 메시지 큐, 공유 메모리 등 프로세스가 서로 통신할 수 있는 메커니즘을 제공한다. IPC는 여러 프로세스가 함께 작동하는 복잡한 애플리케이션에 필수적이다.
- 보안 및 액세스 제어: Linux 커널에는 SELinux(보안 강화 Linux) 및 AppArmor와 같은 강력한 보안 메커니즘이 포함되어 있다. 이러한 프레임워크는 엄격한 액세스 제어 정책을 시행하여 프로세스 및 파일 수준에서 세분화된 보안 설정을 허용한다.

#### Reference

- [What is Linux Kernel?](https://somaz.tistory.com/345)

---