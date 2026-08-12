# ---------------------------------------------------
# ETAPA 1: Compilación (Usamos el SDK pesado)
# ---------------------------------------------------
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Copiamos todo el código y compilamos los binarios en /app/publish
COPY . .
RUN dotnet publish -c Release -o /app/publish

# ---------------------------------------------------
# ETAPA 2: Producción (Usamos el Runtime liviano)
# ---------------------------------------------------
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS final
WORKDIR /app

# Traemos SOLO los binarios terminados de la etapa anterior
COPY --from=build /app/publish .

ENTRYPOINT ["dotnet", "Multistage.dll"]