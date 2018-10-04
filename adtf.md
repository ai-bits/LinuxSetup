```
#aadc2018 160er on 2017er 1030831961
#data types in /home/aadc/AADC/description/aadc.description xml
#for every struct in aadc.description there is a typedef in /home/aadc/AADC/include/aadc_structs.h
#Sessions > +; select

#aadc2018 64 GB USB on Dell - complete uninstall; too complicated dependencies for AADC builds
#install adtf 3.3.3
cd Downloads
./adtf-3.3.3-U1604_x64_gcc54.run #into /opt/ADTF/3.3.3 W/O SUDO! though in /opt w/ owner root
#edit version in ADTF Configration Editor.desktop in ~/aadc/Desktop/ and ~/AADC/config/ and ~/AADC/config/start_adtf_ce_editor.sh

#aadc2018 Windows on Dell w/ dependencies like in /opt from Digitalwerk / Mario
#d/l https://git.digitalwerk.net/aadc/adtf-basic-software and unzip content to c:\AADC
#install adtf 3.3.3 to c:\SDK\ADTF\3.3.3 and unzip dependencies of adtf-3.3.3-WIN7_x64_vc140.exe to c:\SDK
#replace ADTF 3.3.1 refs in AADC\AADCConfig.cmake (2) #used 3.3.3 because 3.3.1 had errors and crashed
#environment variable user ADTF_DIR c:\SDK\ADTF\3.3.3; ADTF3_DIR %ADTF_DIR%
#C:/SDK/adtf/3.3.3/ADTFMacros.cmake:53 changed from OFF to ON:
#option(ADTF_ALLOW_UNSUPPORTED_COMPILER "Allow building ADTF with an unsupported compiler (version)." ON)
#install http://www.stack.nl/~dimitri/doxygen/download.html#srcbin into C:\Tools\doxygen and
#add C:\Tools\doxygen\bin to (user) path
#d/l ADTF displaytoolbox and install to C:\SDK\adtf\3.3.3\addons
https://support.digitalwerk.net/projects/download-center/repository/changes/adtf-toolboxes/adtf-display-toolbox/release-3.1.0/displaytoolbox-3.1.0-adtf3.3.0-WIN7_x64_vc140.exe
cd C:\SDK\adtf\3.3.3\addons\displaytoolbox
build_examples.bat #questions: ADTF3_DIR? c:\SDK\ADTF\3.3.3 QT directory? C:\SDK\qt\5.9.5\msvc2015_64
#Build files have been written to: C:/SDK/adtf/3.3.3/addons/displaytoolbox/build
#Build sln? VS must be in path! Befeht devenv nicht gefunden!
#build sln in C:\SDK\adtf\3.3.3\addons\displaytoolbox\build manually w/ VS

#adtf gitlab #aadc gitlab on Windows and VMware cloned into C:\ and ~
git clone https://git.bioinf.jku.at/aadc/adtf.git #ends up in adtf (not AADC)

#20180619_AADC_ADTF_1_Training_record.mp4
#1:36:30 mySession sample implemented as my_camera_session w/ my_camera_stream & my_camera_filter
#for stream drag
#2:17:50 emergency break user filter
#/home/aadc/AADC/src/aadcUser/CMakeLists.txt append line:
add_subdirectory(EmergencyBreak)
#copy /home/aadc/AADC/src/aadcUser/TemplateFilter folder and rename to EmergencyBreak
#rename .cpp & .h too and edit CMakeLists.txt project and .cpp & .h references
#project(template_filter) -> project(emergency_break) #mind spelling and _filter not in name inconsistency
#TemplateFilter.h -> EmergencyBreak.h and TemplateFilter.cpp -> EmergencyBreak.cpp
#in EmergencyBreak.h:
#?#define CID_TEMPLATEFILTER_DATA_TRIGGERED_FILTER -> #define CID_EMERGENCYBREAK_DATA_TRIGGERED_FILTER
#template_filter.filter.user.aadc.cid -> emergency_break.filter.user.aadc.cid
#replace all cTemplateFilter with cEmergencyBreak
#in EmergencyBreak.cpp:
#include "TemplateFilter.h" -> #include "EmergencyBreak.h"
#"TemplateDataFilter" -> "EmergencyBreak"
#replace all cTemplateFilter with cEmergencyBreak

#LaneDetection ~/AADC/src/aadcDemo/algorithms/LaneDetection -> ~/AADC/src/aadcUser/GueLaneDetection
#MyLaneDetection == Lukas
#rn .cpp & .h to GueLaneDetection
#edit GueLaneDetection/CMakeLists.txt and add Gue to .cpp & .h and gue_ to lane_detection
#edit CMakeLists.txt and add add_subdirectory(GueLaneDetection)
#in GueLaneDetection.h: change "lane_detection.filter.demo.aadc.cid" to:
#define CID_CLANEDETECTION_DATA_TRIGGERED_FILTER "gue_lane_detection.filter.user.aadc.cid"
#in GueLaneDetection.cpp:
#include "LaneDetection.h" -> #include "GueLaneDetection.h"
#did NOT change class name cLaneDetection

#adtf session with Dell #webcam #UVC-Webcam Universal Video Class
#Dell XPS 9550: Sunplus Innovation Technology Inc: Bus 001 Device 004: ID 1bcf:2b95

#ADTF remote with #Jetson smb://tegra-ubuntu/homes/ADTF/
cd ~/ADTF/bin #on Jetson
./adtf_launcher -session="../src/examples/projects/ADTF_Project/adtfsessions/demo_playback.adtfsession" -run -console

#ADTF remote with #AudiCar 2017
#locally on target
cd /opt/ADTF/3.3.1/bin
./adtf_launcher -session="../src/examples/projects/ADTF_Project/adtfsessions/demo_playback.adtfsession" -run -console
#locally on controller to control ADTF session remotely
cd /opt/ADTF/3.3.1/bin
./adtf_control
lsof -i #adtf_laun 3778 aadc    3u  IPv4  89522      0t0  TCP localhost:8000 (LISTEN)

#Mario Georg
xrandr --fb 1920x1080 #nomachine resolution change w/o monitor
#sync.sh #on aadcUser
smb://192.168.2.17/share
ssh -keygen #?

#### Qt Creator
#open project /home/aadc/AADC/src/aadcUser/CMakeLists.txt
#Build Dir: /home/aadc/AADC/_build_user
#according to video only 3.3.1?: Projects vertical item > Build Env > Add ADTF_DIR /opt/ADTF/3.3.1/

#file:///opt/ADTF/3.3.1/doc/adtf_html/adtf3_getting_started.html
cd /opt/ADTF/3.3.1/bin
./adtf_control
launch ../src/examples/projects/ADTF_Project/adtfsessions/demo_playback.adtfsession

#### CANbus #CANbus #PCANBasic
##prerequisite: PEAK driver and UserMan https://www.peak-system.com/fileadmin/media/linux/index.htm#download
#un-tar.gz to ~/Downloads/peak-linux-driver-8.6.0/
#PCAN-Driver-Linux_UserMan_eng.pdf install page 7:
cd ~/Downloads/peak-linux-driver-8.6.0
make clean
make

##docs: F:\Prg\Audi\AADC2018\Lukas\CAN\PCAN_Basic_Linux-4.2.2\pcanbasic\PCANBasic_enu.chm
#/home/aadc/CAN/PCAN_Basic_Linux-4.2.2/readme.txt line 94:
#PCAN-Basic library install:
#cd /home/aadc/CAN/PCAN_Basic_Linux-4.2.2/pcanbasic/
#make error:
#/home/aadc/CAN/PCAN_Basic_Linux-4.2.2/pcanbasic/src/libpcanfd/pcan.h not found

#### YOLO 1 Yasser > Mo
#freeze model?
#### Darknet https://pjreddie.com/darknet #YOLOv3 #SLAM
git clone https://github.com/pjreddie/darknet.git
cd darknet
#GPU with CUDA 9.2 on gnub16044 #cuDNN:
cd Downloads
sudo dpkg -i libcudnn7_7.3.1.20-1+cuda9.2_amd64.deb
sudo dpkg -i libcudnn7-dev_7.3.1.20-1+cuda9.2_amd64.deb #:
#update-alternatives: using /usr/include/x86_64-linux-gnu/cudnn_v7.h to provide /usr/include/cudnn.h (libcudnn) in auto mode
sudo dpkg -i libcudnn7-doc_7.3.1.20-1+cuda9.2_amd64.de
gedit Makefile #GPU=1 CUDNN=1
#/GPU
make #./darknet #test should return: usage: ./darknet <function> #GPU=1: NVCC not found
wget https://pjreddie.com/media/files/yolov3.weights
./darknet detect cfg/yolov3.cfg yolov3.weights data/dog.jpg
./darknet detect cfg/yolov3.cfg yolov3.weights data/3barbies.jpg
```
