FROM ubuntu:xenial 

RUN useradd scuser \
&& apt-get update \
&& apt-get install -y sudo \
&& echo 'scuser ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers

USER scuser

ENV USER=scuser

RUN sudo apt-get update \
&& sudo apt-get install net-tools \
&& sudo apt-get install -y python-pip \
virtualenv \
git \
vim \
software-properties-common 
# && sudo apt-get update \
# && sudo add-apt-repository ppa:deadsnakes/ppa \
# && sudo apt-get update \
# && sudo apt-get install -y python3.6 

 WORKDIR home/scuser/Programming/robotics-prototype/ 

# clone the repo
RUN sudo git clone --recursive https://github.com/space-concordia-robotics/robotics-prototype . ; exit 0

# run the autosetup
RUN sudo ./EnvironmentSetup.sh

# ENV VIRTUAL_ENV=venv
# RUN sudo virtualenv --python=/usr/bin/python3.6 $VIRTUAL_ENV  
# ENV PATH="$VIRTUAL_ENV/bin:$PATH"
# # && /bin/bash -c ". venv/bin/activate" \

# RUN sudo cp /root/.bashrc ~/ \
# && sudo chown -R scuser /home/scuser/ \
# && python -m pip install --upgrade pip \
# && python -m pip install -r requirements.txt -r requirements-dev.txt \
# && python setup.py develop \
# && pytest \
# && sudo apt-get install -y ros-kinetic-rosbridge-suite \
# ros-kinetic-cv-camera \
# ros-kinetic-web-video-server \
# && echo '\n#local mode\nexport ROS_MASTER_URI=http://localhost:11311\nexport ROS_HOSTNAME=localhost\n#competition mode\n#export ROS_MASTER_URI=http://172.16.1.30:11311\n#export ROS_HOSTNAME=$USER\n. ~/Programming/robotics-prototype/robot/rospackages/devel/setup.bash\n. ~/Programming/robotics-prototype/venv/bin/activate\nsource ~/Programming/robotics-prototype/robot/basestation/config/.bash_aliases' >> ~/.bashrc \
# && robot/basestation/env.sh >| robot/basestation/static/js/env.js 
# # && cp commit-message-hook.sh .git/hooks/prepare-commit-msg && cp branch_name_verification_hook.py .git/hooks/post-checkout 
