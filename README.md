# Linux_setting
# Ubuntu 환경 구축

https://github.com/5sik/Linux-setting

자주 포맷할 수 있으니, 작성해둠.

## 우분투 설치

우선, 처음에 우분투 20.04 버전으로 설치: https://shanepark.tistory.com/230

이 때, normal이 아닌 minimal로 하는 것이 좋음.

## 한글 설정

그 다음에 한글 설정해야됨: https://ieworld.tistory.com/4

## GCC compile 설치

```bash
sudo apt install gcc
```

## Chrome

https://jjeongil.tistory.com/1944

```bash
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo apt install ./google-chrome-stable_current_amd64.deb
```

## Github 설치

```bash
sudo apt install git-all
```

## Terminator

https://makepluscode.tistory.com/90

```bash
sudo apt-get install terminator
```

ctrl+shift+e가 잘 안되면

```bash
ibus-setup
```

이후에 emoji 단축키 삭제

## miniConda

miniconda 홈페이지: https://docs.conda.io/projects/miniconda/en/latest/

```bash
mkdir -p ~/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda3/miniconda.sh
bash ~/miniconda3/miniconda.sh -b -u -p ~/miniconda3
rm -rf ~/miniconda3/miniconda.sh
```

```bash
~/miniconda3/bin/conda init bash
~/miniconda3/bin/conda init zsh
```

## Vscode

https://chunggaeguri.tistory.com/entry/Ubuntu-2004-Visual-Studio-Code-%EC%84%A4%EC%B9%98%EB%B0%A9%EB%B2%95

```bash
sudo apt update
sudo apt install software-properties-common apt-transport-https
```

```bash
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
sudo apt install code
```

## Raisim

[Raisim 설치](https://www.notion.so/Raisim-ac124338d75e4200a3be11615b8608c0?pvs=21)

## AnyDesk

```bash
sudo apt update
wget -qO - https://keys.anydesk.com/repos/DEB-GPG-KEY | sudo apt-key add -
echo "deb http://deb.anydesk.com/ all main" | sudo tee /etc/apt/sources.list.d/anydesk-stable.list

sudo apt update
sudo apt install anydesk
```

## Apt 저장소 변경

```bash

```

## 기타 중요한 설치들

```bash
sudo apt-get install htop
sudo apt-get install gpustat
sudo apt-get install imagemagick # can use 'display' command in terminal to view image
sudo snap install vlc
```

## CUDA 및 Pytorch 설치

1. 먼저 확인

```bash
nvcc --version or nvcc -V # check CUDA version
nvidia-smi # check whether the GPU is correctly detected
```

1. [https://pstudio411.tistory.com/entry/Ubuntu-2004-Nvidia드라이버-설치하기](https://pstudio411.tistory.com/entry/Ubuntu-2004-Nvidia%EB%93%9C%EB%9D%BC%EC%9D%B4%EB%B2%84-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0)
2. CUDA [link](https://developer.nvidia.com/cuda-toolkit-archive) --> run_file(local)로 해야함. ".run" 실행후 driver 설치는 체크 해제해야함. 안 그러면 사전에 깔려있는 driver 지워짐 [[link](https://velog.io/@seok990301/Nvidia-driver-cuda-%EB%B2%84%EC%A0%84)]

```bash
#set CUDA path 
#(set to the symlink cuda rather than explicit cudaX.X for cases when you use multiple CUDA version)
vim ~/.bashrc
export PATH="/usr/local/cuda/bin:$PATH"
export LD_LIBRARY_PATH="/usr/local/cuda/lib64:$LD_LIBRARY_PATH"

source ~/.bashrc
```

1. cudNN 설치
[download link](https://developer.nvidia.com/rdp/cudnn-archive) [install guide1](https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html) [install guide2](https://kyumdoctor.co.kr/30)
2. https://pytorch.org/ 여기서 진행

---

## Etc.

### 단축키 설정

우선 vim 설치: https://gabii.tistory.com/entry/Ubuntu-vim-%EC%84%A4%EC%B9%98-%EB%B0%8F-%EC%84%A4%EC%A0%95

```bash
# Update and install vim
sudo apt-get update
sudo apt-get install vim
```

vim은 insert누르고 편집시작, esc :wq누르면 저장종료

그러고나서, vim ~/.bashrc

하고나서 최하단에 alias <단축키> = ‘줄이고 싶은 단축키’설정하면 됨.

**반드시 작은 따옴표로 감싸줘야하고, =과 ‘사이에 띄어쓰기가 있으면 안된다!**

```bash
//Example
alias ros_env=‘mamba activate ros_env’ // 매번 activate 치는 거 길고 tap도 안먹혀서 만들어줌.
alias catkin_make_and_source=‘catkin_make & source devel/setup.sh’ // 매번 setup.sh해주는 거 귀찮음.
```

### Realsense Viewer

https://github.com/IntelRealSense/librealsense/blob/master/doc/distribution_linux.md

### ROS 설치

Ros noetic설치: https://robostack.github.io/GettingStarted.html **(base에 설치하면 안됨. 반드시, conda activate <env>해주고 설치하길)**

## office 설치

그리고, minimal로 설치했으면 기본 office가 없음. libreoffice가 우분투 기본이니깐 설치.

http://sjava.net/2011/07/ubuntu%EC%97%90-libreoffice-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0/ 2번까지만 하면 됨.

근데, 이거 설치하고 나서부터 한글이 입력이 안될 수가 있음.

그러면 여기 참고. https://namu.wiki/w/%EB%A6%AC%EB%B8%8C%EB%A0%88%EC%98%A4%ED%94%BC%EC%8A%A4 여기서 9. 버그 참고

→ sudo gedit /usr/share/X11/xkb/symbols/kr 하고 kr106앞에 있는 default 항목 kr 104로 끌어오면 됨. Default 뒤에 띄어쓰기 2개 주의.

## Tips

- Capture = Prt sc 버튼 활용 (shift 누르면 범위지정)

