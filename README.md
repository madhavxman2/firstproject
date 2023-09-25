

<!-- db.json -->
{
  "employees": [
    {
      "id": 1,
      "name": "mohan singh",
      "profession": "AutoCAD developer",
      "salary": 30000
    },
    {
      "id": 2,
      "name": "rohan singh",
      "profession": "WEbsite Designer",
      "salary": 45000
    },
    {
      "id": 3,
      "name": "joshi mishra",
      "profession": "AutoCAD developer",
      "salary": 33000
    }
  ]
}

<!-- demo.html -->
<!DOCTYPE html>
<html>
  <head>
    <title>Fetch API Example</title>
  </head>
  <body>
    <table id="employeeTable" border="1" style="text-align: center;">
      <thead>
        <tr>
          <th>ID</th>
          <th>Name</th>
          <th>Position</th>
          <th>Salary</th>
        </tr>
      </thead>
      <tbody>
        <!-- Table rows will be populated here -->
      </tbody>
      <tfoot>
        <tr>
          <td colspan="3">Total Salary</td>
          <td id="totalSalary"></td>
        </tr>
      </tfoot>
    </table>
    <script src="index.js"></script>
  </body>
</html>

<!-- index.js -->
// Your Fetch API code here
const apiUrl = "http://localhost:3050/employees";
fetch(apiUrl)
  .then((response) => response.json())
  .then((data) => {
    // Handle the retrieved data here
    const employeeTable = document.getElementById("employeeTable");
    const tbody = employeeTable.querySelector("tbody");
    const totalSalaryCell = document.getElementById("totalSalary");
    let totalSalary = 0;
    data.forEach((employee) => {
      totalSalary += employee.salary;
      const row = document.createElement("tr");
      row.innerHTML = `
        <td>${employee.id}</td>
        <td>${employee.name}</td>
        <td>${employee.profession}</td>
        <td>${employee.salary}</td>
        `;
      tbody.appendChild(row);
    });
    totalSalaryCell.textContent = totalSalary;
  })
  .catch((error) => {
    console.error("Error fetching data:", error);
  });

![image](https://github.com/madhavxman2/firstprojectpush/assets/68814428/12c352c8-eab0-4597-8d4e-3e4d708e122f)
