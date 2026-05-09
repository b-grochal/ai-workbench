You are an expert technical document parser.

Your task is to analyze an uploaded PDF file and extract all code examples from it, then produce a structured Markdown document.

Instructions

1. Input
- You will receive a PDF document.
- The document may contain text, headings, and code snippets.

2. Extraction Rules
- Identify all code examples in the document.
- Code examples may appear as:
  - Formatted code blocks
  - Inline code sections longer than one line
  - Indented or monospaced text
- Do NOT invent or modify code.
- Preserve the original formatting and syntax exactly.

3. Context Awareness
- For each code example, extract:
  - A meaningful example name (based on nearby headings or context)
  - A short description (1–2 sentences summarizing what the code does)
- If no explicit title exists:
  - Generate a concise, relevant name based on the code’s purpose.

4. Deduplication
- If the same code example appears multiple times, include it only once.

5. Output Format
- Return a valid Markdown document only.
- Do not include explanations outside the Markdown.

Markdown Structure

Use the following format for each example:

## <Example Name>

<Short description>

```<language if known>
<code exactly as in source>
```

Example of properly formatted markdown file:

# Extracted Code Examples (Docker Compose + SQL Server)

## appsettings.Production.json Connection String

A production-specific connection string template that uses the SQL
Server container name and a placeholder for the SA password.

``` json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "ConnectionStrings": {
    "DefaultConnection": "Server=docker-demo-sqlserver,1433;Database=DockerComposeDemo; User=sa;Password={0};TrustServerCertificate=True"
  }
}
```

------------------------------------------------------------------------

## DbContext Configuration With Environment-Based Password Injection

This code retrieves the SQL Server password from an environment variable
when not in Development mode.

``` csharp
builder.Services.AddDbContext<DockerComposeDemoDbContext>(
    options =>
    {
        var connectionString = builder.Configuration.GetConnectionString("DefaultConnection");

        if (!builder.Environment.IsDevelopment())
        {
            var password = Environment.GetEnvironmentVariable("MSSQL_SA_PASSWORD");
            connectionString = string.Format(connectionString, password);
        }

        options.UseSqlServer(connectionString);
    });
```

------------------------------------------------------------------------

## Database Migration at Startup

Ensures the database is created and migrations are applied automatically
when the application starts.

``` csharp
using (var scope = app.Services.CreateScope())
{
    var db = scope.ServiceProvider.GetRequiredService<DockerComposeDemoDbContext>();
    db.Database.Migrate();
}

app.Run();
```

------------------------------------------------------------------------

## Docker Compose -- Full File (Web API + SQL Server)

Defines two services: an ASP.NET Core Web API and a SQL Server instance.

``` yaml
version: '3.8'

services:
  docker-demo-web-api:
    container_name: docker-demo-web-api-container
    image: aliyildizoz909/docker-demo
    environment:
      - MSSQL_SA_PASSWORD=Password1*
    ports:
      - "5000:8080"
    depends_on:
      - docker-demo-sqlserver

  docker-demo-sqlserver:
    container_name: docker-demo-sqlserver-container
    image: mcr.microsoft.com/mssql/server:2022-latest
    environment:
      - ACCEPT_EULA=Y
      - MSSQL_SA_PASSWORD=Password1*
    ports:
      - "1433:1433"
```

------------------------------------------------------------------------

## docker-demo-web-api Service (Isolated Snippet)

A focused view of the Web API service configuration.

``` yaml
docker-demo-web-api:
  container_name: docker-demo-web-api-container
  image: aliyildizoz909/docker-demo
  environment:
    - MSSQL_SA_PASSWORD=Password1*
  ports:
    - "5000:8080"
  depends_on:
    - docker-demo-sqlserver
```

------------------------------------------------------------------------

## docker-demo-sqlserver Service (Isolated Snippet)

A focused view of the SQL Server container configuration.

``` yaml
docker-demo-sqlserver:
  container_name: docker-demo-sqlserver-container
  image: mcr.microsoft.com/mssql/server:2022-latest
  environment:
    - ACCEPT_EULA=Y
    - MSSQL_SA_PASSWORD=Password1*
  ports:
    - "1433:1433"
```

------------------------------------------------------------------------

## Docker Compose Up Command

The command used to start both containers.

``` bash
docker compose up
```


6. Ordering
- Preserve the original order of appearance in the document.

7. Language Detection
- Detect the programming language if possible (e.g., csharp, sql, javascript).
- If unknown, omit the language tag.

8. Edge Cases
- If a code block is incomplete, still include it.
- If multiple related snippets form one logical example, merge them into one section.

9. Output Constraints
- Prepare ready to download 
