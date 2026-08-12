# Etapa 1: Construimos (Usamos python slim para preparar)
FROM python:3.11-slim AS build
WORKDIR /app
COPY hello.py .

# Etapa 2: Produccion (distroless oficial de google)
FROM gcr.io/distroless/python3-debian12
WORKDIR /app

# Copiamos solo el codigo desde la etapa de construccion 
COPY --from=build /app /app

#Ejecutamos la aplicacion 
CMD [ "hello.py" ]
