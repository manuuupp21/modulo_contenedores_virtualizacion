FROM python:3.11-slim
WORKDIR /AdoptAPI
COPY . .
RUN pip install -r requirements.txt
# el docker escucha peticiones HTTP en el puerto 8080.
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8080"]