
# 🔷 1. **Project Overview**

A web-based system where users can:

* Register/Login
* Create tasks & projects
* Assign deadlines
* Track progress
* Store data in database
* Access via REST API
* Run using Docker

---

# 🔷 2. **Technologies**

* **Frontend:** ASP.NET Core MVC (or Razor Pages)
* **Backend:** C#
* **Database:** SQL Server
* **API:** ASP.NET Core Web API
* **Deployment:** Docker + Docker Compose

---

# 🔷 3. **System Architecture**

```
[ User ]
   ↓
[ ASP.NET UI ]
   ↓
[ REST API (C#) ]
   ↓
[ SQL Server Database ]
```

---

# 🔷 4. **OOP Concepts (IMPORTANT for marks)**

Use clearly:

* **Encapsulation**

  ```csharp
  public class Task
  {
      public int Id { get; set; }
      public string Title { get; set; }
      public bool IsCompleted { get; set; }
  }
  ```

* **Inheritance**

  ```csharp
  public class User
  {
      public string Name { get; set; }
  }

  public class Admin : User
  {
      public void DeleteTask() { }
  }
  ```

* **Polymorphism**

  ```csharp
  public virtual void Display()
  {
      Console.WriteLine("Task");
  }
  ```

---

# 🔷 5. **Database Design**

### Tables:

* Users
* Tasks
* Projects

### Example SQL:

```sql
CREATE TABLE Users (
    Id INT PRIMARY KEY IDENTITY,
    Username NVARCHAR(50),
    Password NVARCHAR(50)
);

CREATE TABLE Tasks (
    Id INT PRIMARY KEY IDENTITY,
    Title NVARCHAR(100),
    IsCompleted BIT,
    UserId INT,
    FOREIGN KEY (UserId) REFERENCES Users(Id)
);
```

---

# 🔷 6. **REST API Example**

```csharp
[HttpGet]
public IActionResult GetTasks()
{
    var tasks = _context.Tasks.ToList();
    return Ok(tasks);
}
```

---

# 🔷 7. **Docker Setup (VERY IMPORTANT)**

## ✅ Dockerfile

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY . .
ENTRYPOINT ["dotnet", "YourApp.dll"]
```

---

## ✅ docker-compose.yml (BONUS MARKS 💯)

```yaml
version: '3.4'

services:
  app:
    build: .
    ports:
      - "5000:80"
    depends_on:
      - db

  db:
    image: mcr.microsoft.com/mssql/server
    environment:
      SA_PASSWORD: "Your_password123"
      ACCEPT_EULA: "Y"
    ports:
      - "1433:1433"
```

---

# 🔷 9. **Lab Report **

### 2. Problem Description

Managing tasks efficiently

### 3. Objectives

* Build full-stack system
* Apply OOP
* Deploy using Docker

### 4. System Design

(Add UML diagram)

### 5. Implementation

Explain:

* UI
* Backend
* Database
* API

### 6. Docker Explanation

* Dockerfile
* Image build
* Container run

### 8. Results

Application works in container

### 9. Conclusion

System successfully deployed

---



👉 *"Make lab report"* OR
👉 *"Teach Docker step by step"*
