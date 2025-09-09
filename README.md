🔹 2. pyenv 사용

여러 버전의 Python을 동시에 설치/관리하는 도구입니다.

설치:

sudo apt update
sudo apt install -y make build-essential libssl-dev zlib1g-dev \
    libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
    libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev

curl https://pyenv.run | bash


.bashrc (또는 .zshrc)에 추가:

export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init -)"


다시 로그인 후:

# 원하는 버전 설치
pyenv install 3.9.19
pyenv install 3.11.9

# 글로벌 기본 버전 설정
pyenv global 3.11.9

# 특정 폴더에서만 다른 버전 사용
cd my_project
pyenv local 3.9.19


-----------------------------

1) ARM64 전용 Miniconda/Miniforge 설치

공식 Miniconda는 ARM 빌드를 제공하지 않아서, 보통 Miniforge를 씁니다.
라즈베리파이에 가장 잘 맞습니다.

# Miniforge 다운로드 (ARM64 전용)
wget https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-aarch64.sh

# 설치 (홈 디렉토리에 설치 권장)
bash Miniforge3-Linux-aarch64.sh


설치 후에는 터미널 재시작하거나:

source ~/miniforge3/bin/activate

2) Conda 환경 생성 예시
conda create -n myenv python=3.10 -y
conda activate myenv

3) exec format error 원인

x86_64 바이너리를 ARM 기기에서 실행했을 때 발생

즉, Miniconda3-latest-Linux-x86_64.sh를 받아서 실행했을 가능성이 높습니다
👉 반드시 aarch64 빌드를 사용하세요.
