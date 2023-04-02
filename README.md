#!/bin/bash
# This Bash Script was created by Fulahahax for free to You all. 
# Do We allow using it for free? Yes we are allowing. Do we allow earn on it money? No we do not allowing. Knowlegde is free.
# You find the mistake - write to us.
# You want to join us? Sorry we choose who deserve to join us.
# We 2BE we are Free forlk of Net. Educate Yourself. 

# What is KVM? KVM - KERNEL VIRTAUL MACHINE - Like name tell ya all it's the Virtual Machine perfect for all linux distribution. 
# What you can install on it? All Linux, Windows, Android OS, Apple OS. But remeber  check  what you need more for each of distributions.


# Time to Check if KVM is already installed

dpkg -s qemu-kvm
if [ $? -eq 0 ]; then
  echo "KVM is already installed"
else
  # Installing KVM
  sudo apt-get update
  sudo apt-get install -y qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils
fi

#Now Checking if the current user is in the libvirt group
id -nG | grep -qw libvirt
if [ $? -eq 0 ]; then
  echo "Current user is already in the libvirt group"
else
  # Add the current user to the libvirt group
  sudo usermod -aG libvirt "$USER"
  echo "Added current user to the libvirt group"
fi

# Check if GUI tools are installed
dpkg -s virt-manager
if [ $? -eq 0 ]; then
  echo "virt-manager is already installed"
else
  # Prompt to install virt-manager
  read -p "Do you want to install virt-manager (y/n)? " response
  if [ "$response" == "y" ]; then
    sudo apt-get install -y virt-manager
  fi
fi

dpkg -s gnome-boxes
if [ $? -eq 0 ]; then
  echo "gnome-boxes is already installed"
else
  # Prompt to install gnome-boxes
  read -p "Do you want to install gnome-boxes (y/n)? " response
  if [ "$response" == "y" ]; then
    sudo apt-get install -y gnome-boxes
  fi
fi

# The sjon is done. 

