# Employee Management Dashboard

A simple **ASP.NET Web Forms + C#** project for managing employee
records through a browser-based dashboard.

## Team

  Name              Enrollment No.   Division
  ----------------- ---------------- ----------
  Yash Jadhav       2405101200015    D
  Jaivin Vachhani   2405101200043    D
  Tirth Bariya      2405101200050    D

## Features

-   Employee dashboard with total employee count
-   Add employee form
-   Name, email, department, and salary validation
-   Employee table using ASP.NET `GridView`
-   Delete employee functionality
-   Server-side event handling in C#
-   Employee state maintained using `ViewState`
-   Styled dashboard interface

## Technology Stack

-   **Frontend:** ASP.NET Web Forms, HTML, CSS
-   **Backend:** C#
-   **Framework:** .NET Framework / ASP.NET Web Forms
-   **Controls:** TextBox, DropDownList, Button, Validators, GridView,
    Label
-   **State Management:** ViewState

## Application Architecture

``` mermaid
flowchart TD
    A[User / Browser] --> B[WebForm1.aspx]
    B --> C[ASP.NET Server Controls]
    C --> D[WebForm1.aspx.cs]
    D --> E[Employee List]
    E --> F[ViewState]
    D --> G[BindEmployees]
    G --> H[GridView]
    H --> B
```

## Application Flow

``` mermaid
flowchart LR
    A[Open Dashboard] --> B[Load Employee Data]
    B --> C[Display GridView]
    C --> D{User Action}
    D -->|Add| E[Validate Input]
    E --> F[Create Employee Object]
    F --> G[Add to Employee List]
    G --> H[Rebind GridView]
    D -->|Delete| I[Select Row]
    I --> J[Remove Employee]
    J --> K[Reassign IDs]
    K --> H
    D -->|View| L[Read Employee List]
    L --> H
```

## CRUD Operations

### Create

The user enters employee name, email, department, and salary. ASP.NET
validators check the input. `btnAdd_Click` creates an `Employee` object,
adds it to the employee list, and refreshes the GridView.

### Read

`Page_Load` initializes sample employee records on the first request.
`BindEmployees()` assigns the employee list to the `GridView` and
updates the total employee count.

### Update

The current interface does **not** contain a dedicated Edit/Update
button. The employee collection can be modified in server-side C#, but a
separate UPDATE UI is not implemented in the current version.

### Delete

The GridView provides a Delete command. `gvEmployees_RowDeleting`
removes the selected employee, reassigns IDs, and refreshes the table.

## Validation

-   Employee name is required.
-   Email is required and checked with a regular expression.
-   Department selection is required.
-   Salary is required.
-   Salary accepts numbers only.

## Code Structure

``` text
ASP_Project/
├── WebForm1.aspx
├── WebForm1.aspx.cs
├── WebForm1.aspx.designer.cs
├── Site.Master
├── Web.config
└── ...
```

## Page Architecture

``` mermaid
flowchart TD
    A[WebForm1.aspx] -->|CodeBehind| B[WebForm1.aspx.cs]
    B --> C[Employee Class]
    A --> D[ASP.NET Server Controls]
    D --> B
    B --> E[ViewState]
    B --> F[GridView Data Binding]
```


## Result

The project demonstrates a working employee management dashboard using
ASP.NET Web Forms, C# event-driven programming, server controls,
validation, ViewState-based state management, and CRUD-oriented employee
record management.
