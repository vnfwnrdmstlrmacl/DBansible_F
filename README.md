# DBansible_F
ssh-keygen -t ed25519 -a 64 -f /root/.ssh/id_ed25519_ansible -N "" -C "proxy1-ansible"
ssh-copy-id root@<ip>

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



