# Etape 1 : build avec le SDK complet
FROM mcr.microsoft.com/dotnet/sdk:7.0.410 AS build

WORKDIR /src

COPY Worker.csproj .
RUN dotnet restore

COPY . .
RUN dotnet publish -c Release --no-restore --self-contained false -o /app/publish

# Etape 2 : image finale avec runtime
FROM mcr.microsoft.com/dotnet/runtime:7.0.20 AS runtime

WORKDIR /app

COPY --from=build /app/publish .

HEALTHCHECK --interval=30s --timeout=10s --retries=3 \
    CMD pgrep -x dotnet || exit 1

CMD ["dotnet", "Worker.dll"]

