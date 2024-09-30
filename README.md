Linux_setting
=============

   
# Ubuntu 20.04 install
  Following: https://shanepark.tistory.com/230/   
  normal보단 minimal이 나음.   
   

# Apt 저장소 변경
  Following: https://bigbigpark.github.io/linux/change_repo/   
   

# Chrome, Git, Vim, Terminator, Etc.
  ```bash
  # Chrome
  wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
  sudo apt install ./google-chrome-stable_current_amd64.deb

  # Git
  sudo apt install git-all

  ## Vim
  sudo apt-get update
  sudo apt-get install vim

  # Terminator
  sudo apt-get install terminator

  # Etc.
  sudo apt-get install htop
  sudo apt-get install gpustat
  sudo apt-get install imagemagick # can use 'display' command in terminal to view image
  sudo snap install vlc
  ```

  ```bash
  # Termiator: ctrl+shift+e가 잘 안되면
  ibus-setup
  # 이후에 emoji 단축키 삭제
  ```
   

# miniConda
miniconda: https://docs.conda.io/projects/miniconda/en/latest/
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
   

# Vscode
  ```bash
  sudo apt update
  sudo apt install software-properties-common apt-transport-https
  ```
  ```bash
  wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
  sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
  sudo apt install code
  ```
   

# AnyDesk
  ```bash
  sudo apt update
  wget -qO - https://keys.anydesk.com/repos/DEB-GPG-KEY | sudo apt-key add -
  echo "deb http://deb.anydesk.com/ all main" | sudo tee /etc/apt/sources.list.d/anydesk-stable.list
  
  sudo apt update
  sudo apt install anydesk
  ```

   
# CUDA & Pytorch

1. Check gpu hardware and CUDA version

  ```bash
  nvcc --version or nvcc -V # check CUDA version
  nvidia-smi # check whether the GPU is correctly detected
  ```

2. [https://pstudio411.tistory.com/entry/Ubuntu-2004-Nvidia드라이버-설치하기](https://pstudio411.tistory.com/entry/Ubuntu-2004-Nvidia%EB%93%9C%EB%9D%BC%EC%9D%B4%EB%B2%84-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0)
3. CUDA [link](https://developer.nvidia.com/cuda-toolkit-archive) --> run_file(local)로 해야함. ".run" 실행후 driver 설치는 체크 해제해야함. 안 그러면 사전에 깔려있는 driver 지워짐 [[link](https://velog.io/@seok990301/Nvidia-driver-cuda-%EB%B2%84%EC%A0%84)]

  ```bash
  #set CUDA path 
  #(set to the symlink cuda rather than explicit cudaX.X for cases when you use multiple CUDA version)
  vim ~/.bashrc
  export PATH="/usr/local/cuda/bin:$PATH"
  export LD_LIBRARY_PATH="/usr/local/cuda/lib64:$LD_LIBRARY_PATH"
  
  source ~/.bashrc
  ```

  4. cudNN 설치
  [download link](https://developer.nvidia.com/rdp/cudnn-archive) [install guide1](https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html) [install guide2](https://kyumdoctor.co.kr/30)
  5. https://pytorch.org/ 여기서 진행
   
   
# Etc.

## GCC compile
  ```bash
  sudo apt install gcc
  ```
  
  
## ROS 설치
  Ros noetic설치: https://robostack.github.io/GettingStarted.html
  
  
## Tips
  - Capture = Prt sc 버튼 활용 (shift 누르면 범위지정)
  
  
### 한글 설정
  Following: https://ieworld.tistory.com/4


## Reference: 
1. Ubuntu 20.04 install: https://shanepark.tistory.com/230
2. Chrome install: https://jjeongil.tistory.com/1944
3. Vscode install: https://chunggaeguri.tistory.com/entry/Ubuntu-2004-Visual-Studio-Code-%EC%84%A4%EC%B9%98%EB%B0%A9%EB%B2%95
4. Pytorch, CUDA, CUDNN install: https://github.com/5sik/Linux-setting
5. Apt 저장소 변경: https://bigbigpark.github.io/linux/change_repo/
6. Vim 설치: https://gabii.tistory.com/entry/Ubuntu-vim-%EC%84%A4%EC%B9%98-%EB%B0%8F-%EC%84%A4%EC%A0%95
7. Ubuntu 한글 설정: https://ieworld.tistory.com/4
