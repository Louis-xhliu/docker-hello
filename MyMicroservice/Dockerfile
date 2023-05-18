
# The build environment using dotnet sdk image
FROM mcr.microsoft.com/dotnet/sdk:7.0 as build
WORKDIR /src
# Copy everything
COPY . .
RUN ls -la
# Run dotnet commands to have the release package
RUN dotnet restore
RUN dotnet publish -c release -o /app


# The running environment using dotnet runtime image
FROM mcr.microsoft.com/dotnet/aspnet:7.0
WORKDIR /app
COPY --from=build /app .
RUN ls -la
# Setup the entry point to run dotnet application
ENTRYPOINT [ "dotnet", "MyMicroservice.dll" ]
