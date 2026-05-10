FROM mcr.microsoft.com/dotnet/aspnet:10.0 AS base
USER app
WORKDIR /app

EXPOSE 8080
EXPOSE 8081

FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build
ARG BUILD_CONFIGURATION=Release

WORKDIR /workspace

COPY ["global.json", "."]
COPY ["NorthwindElementary.slnx", "."]

COPY ["src/Northwind.Api/Northwind.Api.csproj", "src/Northwind.Api/"]

# Identity
COPY ["src/Modules/Identity/Northwind.Modules.Identity/Northwind.Modules.Identity.csproj", "src/Modules/Identity/Northwind.Modules.Identity/"]

COPY ["src/Modules/Identity/Northwind.Modules.Identity.Contracts/Northwind.Modules.Identity.Contracts.csproj", "src/Modules/Identity/Northwind.Modules.Identity.Contracts/"]

# People
COPY ["src/Modules/People/Northwind.Modules.People/Northwind.Modules.People.csproj", "src/Modules/People/Northwind.Modules.People/"]

COPY ["src/Modules/People/Northwind.Modules.People.Contracts/Northwind.Modules.People.Contracts.csproj", "src/Modules/People/Northwind.Modules.People.Contracts/"]

# Academic
COPY ["src/Modules/Academic/Northwind.Modules.Academic/Northwind.Modules.Academic.csproj", "src/Modules/Academic/Northwind.Modules.Academic/"]

COPY ["src/Modules/Academic/Northwind.Modules.Academic.Contracts/Northwind.Modules.Academic.Contracts.csproj", "src/Modules/Academic/Northwind.Modules.Academic.Contracts/"]

# Assessment
COPY ["src/Modules/Assessment/Northwind.Modules.Assessment/Northwind.Modules.Assessment.csproj", "src/Modules/Assessment/Northwind.Modules.Assessment/"]

COPY ["src/Modules/Assessment/Northwind.Modules.Assessment.Contracts/Northwind.Modules.Assessment.Contracts.csproj", "src/Modules/Assessment/Northwind.Modules.Assessment.Contracts/"]

RUN dotnet restore "NorthwindElementary.slnx"

COPY . .

WORKDIR /workspace/src/Northwind.Api

RUN dotnet build "Northwind.Api.csproj" \
    -c $BUILD_CONFIGURATION \
    --no-restore

FROM build AS publish

ARG BUILD_CONFIGURATION=Release

RUN dotnet publish "Northwind.Api.csproj" \
    -c $BUILD_CONFIGURATION \
    -o /app/publish \
    /p:UseAppHost=false \
    --no-build

FROM base AS final

WORKDIR /app

COPY --from=publish /app/publish .

ENTRYPOINT ["dotnet", "Northwind.Api.dll"]
