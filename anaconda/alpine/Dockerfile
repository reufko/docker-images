FROM continuumio/anaconda3:2019.10-alpine

USER root
	
RUN apk add screen git
	
RUN /opt/conda/bin/conda update --prefix /opt/conda anaconda -y

RUN /opt/conda/bin/conda install scikit-learn -y

RUN /opt/conda/bin/conda install jupyter -y && \
	/opt/conda/bin/conda install tensorflow -y && /opt/conda/bin/conda install keras -y 

RUN /opt/conda/bin/conda install -c conda-forge pyldavis -y
	
RUN /opt/conda/bin/python3 -c "import nltk; nltk.download('book')"
	
VOLUME /notebooks

EXPOSE 8888
	
CMD screen -d -m /opt/conda/bin/jupyter notebook --notebook-dir=/notebooks --ip='*' --port=8888 \
	--no-browser --allow-root --NotebookApp.token='' && /bin/sh