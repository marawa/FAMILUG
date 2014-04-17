Thỉnh thoảng khi bạn cài đặt một số package trên ubuntu bạn sẽ gặp phải những lỗi như thế này:

root@thanhnguyen:/home/thanhnguyen# sudo apt-get install git
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following extra packages will be installed:
  git-man liberror-perl
Suggested packages:
  git-daemon-run git-daemon-sysvinit git-doc git-el git-arch git-cvs git-svn
  git-email git-gui gitk gitweb
The following NEW packages will be installed:
  git git-man liberror-perl
0 upgraded, 3 newly installed, 0 to remove and 90 not upgraded.
Need to get 5,963 kB/6,617 kB of archives.
After this operation, 15.2 MB of additional disk space will be used.
Do you want to continue [Y/n]?
WARNING: The following packages cannot be authenticated!
  liberror-perl git-man git
Install these packages without verification [y/N]?
E: Some packages could not be authenticated

=> lỗi:
E: Some packages could not be authenticated

nghĩa là trong quá trình download và cài đặt, có một số lỗi đã xảy ra khiến cho package git của bạn không được authenticated( lỗi chứng thực)

Để fix lỗi này, bạn cần làm những bước sau:

#  autoremove các gói phụ thuộc package git đã được download

sudo apt-get autoremove

# làm sạch( clean) APT's cache của package git đã được download\

# nhưng chưa thành công do xuất hiện lỗi trên

sudo apt-get cleandownload

# update lại APT database

sudo apt-get update

# install lại package git

sudo apt-get install -y -v git

Đó là tất cả những gì bạn phải làm :V



