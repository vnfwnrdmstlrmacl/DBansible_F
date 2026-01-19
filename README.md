# 1) SSH 키 생성
ssh-keygen -t ed25519 -a 64 -f /root/.ssh/id_ed25519_ansible -N "" -C "proxy1-ansible" && \

# 2) SSH 키 배포 (대상 호스트 입력 필요)
ssh-copy-id root@<TARGET_HOST> && \

# 3) 기본 패키지 설치
dnf install -y \
  ansible-core \
  openssh-clients \
  sshpass \
  rsync \
  git \
  python3-libselinux && \

# 4) EPEL 및 CRB 활성화
dnf install -y epel-release && \
dnf config-manager --set-enabled crb || true && \
dnf makecache && \

# 5) Ansible 컬렉션 설치 (dnf + galaxy)
dnf install -y \
  ansible-collection-ansible-posix \
  ansible-collection-community-general && \

ansible-galaxy collection install \
  community.postgresql \
  ansible.posix

