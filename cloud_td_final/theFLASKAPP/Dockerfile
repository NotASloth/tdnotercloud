FROM python:latest

WORKDIR /app/

COPY requirements.txt requirements.txt
RUN wget https://raw.githubusercontent.com/vishnubob/wait-for-it/master/wait-for-it.sh -P /scripts
RUN chmod +x /scripts/wait-for-it.sh
ENTRYPOINT ["/scripts/wait-for-it.sh", "db:5432", "--"]

RUN pip install -r requirements.txt
COPY app.py /app/
COPY config.py /app/
COPY model_saved /app/
COPY tests /app/
COPY templates /app/

EXPOSE 5000
CMD ["python", "app.py", "runserver", "--host=0.0.0.0", "--threaded"]