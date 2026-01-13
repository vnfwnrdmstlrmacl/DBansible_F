# DBansible_F
dnf install -y ansible-core
dnf install -y \
  openssh-clients \
  sshpass \
  rsync \
  git \
  python3-libselinux

dnf install -y epel-release
dnf config-manager --set-enabled crb || true
dnf makecache
dnf install -y ansible-collection-ansible-posix
dnf install -y ansible-collection-community-general


