FROM mcr.microsoft.com/dotnet/sdk:7.0

# Set the working directory inside the container
WORKDIR /app

# Copy the project file(s) and restore dependencies
COPY *.csproj ./
RUN dotnet restore

# Copy the entire application source code
COPY . .

# Build the application in release mode
RUN dotnet publish -c release -o /out

# Set the working directory to the published output
WORKDIR /out

# Expose port 80 for the application
EXPOSE 80

# Run the application using the .NET runtime
ENTRYPOINT ["dotnet", "Worker.dll"]
