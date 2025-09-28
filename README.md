# Занятие 1. Обновление ядра системы

## Цель домашнего задания
Научиться обновлять ядро в ОС Linux.

## Задание:
1) Запустить ВМ c Ubuntu.
2) Обновить ядро ОС на новейшую стабильную версию из mainline-репозитория.
3) Оформить отчет в README-файле в GitHub-репозитории.

## Выполнение:
uname -r  
output: 6.8.0-55-generic

mkdir kernel && cd kernel

wget https://kernel.ubuntu.com/mainline/v6.16.9/amd64/linux-headers-6.16.9-061609-generic_6.16.9-061609.202509250950_amd64.deb

wget https://kernel.ubuntu.com/mainline/v6.16.9/amd64/linux-headers-6.16.9-061609_6.16.9-061609.202509250950_all.deb

wget https://kernel.ubuntu.com/mainline/v6.16.9/amd64/linux-image-unsigned-6.16.9-061609-generic_6.16.9-061609.202509250950_amd64.deb

wget https://kernel.ubuntu.com/mainline/v6.16.9/amd64/linux-modules-6.16.9-061609-generic_6.16.9-061609.202509250950_amd64.deb

sudo dpkg -i *.deb

ls -al /boot
output:
lrwxrwxrwx  1 root root       29 Sep 28 19:27 vmlinuz -> vmlinuz-6.16.9-061609-generic
-rw-------  1 root root 16036352 Sep 25 12:50 vmlinuz-6.16.9-061609-generic
-rw-------  1 root root 14985608 Feb 12  2025 vmlinuz-6.8.0-55-generic
lrwxrwxrwx  1 root root       24 Mar  5  2025 vmlinuz.old -> vmlinuz-6.8.0-55-generic

sudo update-grub

sudo grub-set-default 0

uname -r  
output: 6.16.9-061609-generic

