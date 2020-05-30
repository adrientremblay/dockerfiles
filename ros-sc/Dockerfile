FROM ros:kinetic 

# creating user and group
# RUN groupadd mygroup
# RUN useradd -ms /bin/bash -G mygroup john

RUN apt-get update && apt-get install -y python-pip \
virtualenv \
git \
vim \
software-properties-common && apt-get update && add-apt-repository ppa:deadsnakes/ppa && apt-get update && apt-get install -y python3.6 
# installed vim too for the memes

WORKDIR root/Programming/robotics-prototype/ 

# clone the repo
RUN git clone --recursive https://github.com/space-concordia-robotics/robotics-prototype . ; exit 0

RUN virtualenv --python=/usr/bin/python3.6 venv && . venv/bin/activate && pip install -r requirements.txt -r requirements-dev.txt && python setup.py develop && pytest && apt-get install -y ros-kinetic-rosbridge-suite \
ros-kinetic-cv-camera \
ros-kinetic-web-video-server && echo '\n\n#competition mode\n#export ROS_MASTER_URI=http://172.16.1.30:11311\n#export ROS_HOSTNAME=$USER\n. ~/Programming/robotics-prototype/robot/rospackages/devel/setup.bash\n. ~/Programming/robotics-prototype/venv/bin/activate\nsource ~/Programming/robotics-prototype/robot/basestation/config/.bash_aliases' >> ~/.bashrc && robot/basestation/env.sh >| robot/basestation/static/js/env.js && sed -i '2s|.*|ROBOTICS_WS="/root/Programming/robotics-prototype"|' ~/Programming/robotics-prototype/robot/basestation/config/.bash_aliases && cp commit-message-hook.sh .git/hooks/prepare-commit-msg && cp branch_name_verification_hook.py .git/hooks/post-checkout
# replaced the 2nd line of .bash_aliases.  Kind of a retared solution
