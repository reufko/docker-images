FROM ubuntu:18.04

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV PATH /opt/conda/bin:$PATH

RUN apt-get update --fix-missing && apt-get install -y wget bzip2 ca-certificates \
    libglib2.0-0 libxext6 libsm6 libxrender1 \
    git mercurial subversion screen
	
RUN wget https://repo.anaconda.com/archive/Anaconda3-2020.07-Linux-x86_64.sh -O ~/anaconda.sh && \
    /bin/bash ~/anaconda.sh -b -p /opt/conda && \
    rm ~/anaconda.sh && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate base" >> ~/.bashrc && \
	echo "Anaconda successfully installed"
	
RUN /opt/conda/bin/conda update --prefix /opt/conda anaconda -y

RUN /opt/conda/bin/conda install scikit-learn -y
	
RUN /opt/conda/bin/conda install jupyter -y && \
	/opt/conda/bin/conda install tensorflow -y && /opt/conda/bin/conda install keras -y 

RUN /opt/conda/bin/conda install -c conda-forge pyldavis -y
	
RUN python3 -c "import nltk; nltk.download('book')"

VOLUME /notebooks

EXPOSE 8888
	
CMD screen -d -m /opt/conda/bin/jupyter notebook --notebook-dir=/notebooks --ip='*' --port=8888 \
	--no-browser --allow-root --NotebookApp.token='' && /bin/bash