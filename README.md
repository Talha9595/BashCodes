#!/bin/bash

function add_user {

  printf "Please Enter The Unique Username:\n"

  read username

  printf "Please Enter The UserGroup:\n"

  read usergrp

  grep -w $username /etc/passwd

  if [ $? -ne 0 ]; then

   useradd -G $usergrp $username
   printf "Please enter the Password:\n"
   passwd $username
  else
   printf "*****Sorry!*****\nUsername Already Exist:\n"
  fi
}

while [  1 ]
 do
   add_user
   printf "*****Press Y: Add more user.*****\n*****Press N:Exit.*****\n"
   read opt
  case $opt in
   Y) add_user ;;
   y) add_user ;;
   *) break
  esac
done
