# https://docs.streamlit.io/knowledge-base/tutorials/deploy/docker

FROM python:3.11-slim-buster as runtime

WORKDIR /app

RUN apt-get update && apt-get install -y \
    build-essential \
    curl \
    software-properties-common \
    git \
    && rm -rf /var/lib/apt/lists/*

#RUN git clone https://github.com/amiune/streamlit-agent.git .
COPY * ./

RUN pip3 install -r requirements.txt

EXPOSE 8501

HEALTHCHECK CMD curl --fail http://localhost:8504/_stcore/health

ENTRYPOINT ["streamlit", "run", "minimal_agent.py", "--server.port=8501", "--server.address=0.0.0.0"]