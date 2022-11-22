FROM python:3.12-rc-buster
WORKDIR /usr/src/jupyterlab/

RUN pip install jupyterlab
COPY ./StructuralPatternMatching.ipynb /usr/src/jupyterlab/

EXPOSE 8888/tcp
ENTRYPOINT ["jupyter", "notebook", "--allow-root", "--ip=0.0.0.0", "--no-browser", "--notebook-dir='/usr/src/jupyterlab/'", "--NotebookApp.token=''", "--NotebookApp.password=''"]