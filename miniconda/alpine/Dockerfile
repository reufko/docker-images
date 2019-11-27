FROM continuumio/miniconda3:4.7.12-alpine

USER root
	
RUN apk add screen git

RUN /opt/conda/bin/conda install jupyter -y && \
	/opt/conda/bin/conda install tensorflow -y && /opt/conda/bin/conda install keras -y 
	
VOLUME /notebooks

EXPOSE 8888
	
CMD screen -d -m /opt/conda/bin/jupyter notebook --notebook-dir=/notebooks --ip='*' --port=8888 \
	--no-browser --allow-root --NotebookApp.token='' && /bin/sh