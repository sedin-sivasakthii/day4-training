### Task 1: Escape Callback Hell

**Objective:** Refactor the provided legacy code. Convert the nested callbacks into a clean `async/await` structure using modern Promise-based architecture. Apply the Single Level of Abstraction principle.

**Starter Code:**

```javascript
function getUser(id, callback) {
  setTimeout(() => {
    console.log("Fetched user...");
    callback({ userId: id, username: "admin" });
  }, 1000);
}

function getPermissions(user, callback) {
  setTimeout(() => {
    console.log("Fetched permissions...");
    callback(["read", "write", "delete"]);
  }, 1000);
}

function verifyAccess(permissions, callback) {
  setTimeout(() => {
    console.log("Verifying access...");
    const hasAccess = permissions.includes("delete");
    callback(hasAccess);
  }, 1000);
}

getUser(42, (user) => {
  getPermissions(user, (permissions) => {
    verifyAccess(permissions, (isGranted) => {
      if (isGranted) {
        console.log("Access Granted.");
      } else {
        console.log("Access Denied.");
      }
    });
  });
});

```

### Task 2: The Data Aggregator (Promise.all)

**Objective:** You are building a live dashboard for a logistics company. You need to fetch data from three separate legacy systems simultaneously.

**Constraints:**

1.  You must use `Promise.all`.
    
2.  The final output must be a single combined object.
    
3.  If any single API fails, your function must catch the error and return a fallback object: `{ error: true, message: "System degradation" }`. Use guard clauses to handle the error state early.
    

**Starter Code:**


```javascript
const fetchFleetStatus = () => new Promise(resolve => setTimeout(() => resolve({ activeVehicles: 12 }), 800));
const fetchWarehouseInventory = () => new Promise(resolve => setTimeout(() => resolve({ packagesPending: 430 }), 1200));
const fetchWeatherAlerts = () => new Promise((resolve, reject) => {
  setTimeout(() => {
    // Change true to false to test the error constraint
    const isSuccess = true; 
    isSuccess ? resolve({ alerts: "Clear skies" }) : reject("Weather API Timeout");
  }, 500);
});

async function aggregateDashboardData() {
  // Your code here
}

aggregateDashboardData().then(console.log);

```

### Task 3: Vanilla Weather Dashboard

**Problem Statement:** Build a weather dashboard using Vanilla JavaScript and the native `fetch` API. You must request data from a public weather endpoint. Implement strict error handling to manage and display specific UI messages for network failures, 404 Not Found errors, and 500 Server errors. Keep the DOM manipulation simple (KISS).
