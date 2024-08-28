```javascript
// App.js
import React from 'react';
import { BrowserRouter as Router, Route, Link, Routes } from 'react-router-dom';
import TotalSales from './components/TotalSales';
import SalesGrowth from './components/SalesGrowth';
import NewCustomers from './components/NewCustomers';
import RepeatCustomers from './components/RepeatCustomers';
import GeographicalDistribution from './components/GeographicalDistribution';
import CustomerLifetimeValue from './components/CustomerLifetimeValue';

function App() {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li><Link to="/">Total Sales</Link></li>
            <li><Link to="/sales-growth">Sales Growth</Link></li>
            <li><Link to="/new-customers">New Customers</Link></li>
            <li><Link to="/repeat-customers">Repeat Customers</Link></li>
            <li><Link to="/geographical-distribution">Geographical Distribution</Link></li>
            <li><Link to="/customer-lifetime-value">Customer Lifetime Value</Link></li>
          </ul>
        </nav>

        <Routes>
          <Route path="/" element={<TotalSales />} />
          <Route path="/sales-growth" element={<SalesGrowth />} />
          <Route path="/new-customers" element={<NewCustomers />} />
          <Route path="/repeat-customers" element={<RepeatCustomers />} />
          <Route path="/geographical-distribution" element={<GeographicalDistribution />} />
          <Route path="/customer-lifetime-value" element={<CustomerLifetimeValue />} />
        </Routes>
      </div>
    </Router>
  );
}

export default App;

// components/TotalSales.js
import React from 'react';
import { Line } from 'react-chartjs-2';
import { Chart as ChartJS, CategoryScale, LinearScale, PointElement, LineElement, Title, Tooltip, Legend } from 'chart.js';

ChartJS.register(CategoryScale, LinearScale, PointElement, LineElement, Title, Tooltip, Legend);

const demoData = {
  labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
  datasets: [
    {
      label: 'Total Sales',
      data: [12000, 19000, 15000, 22000, 18000, 25000],
      borderColor: 'rgb(75, 192, 192)',
      tension: 0.1,
    },
  ],
};

const options = {
  responsive: true,
  plugins: {
    legend: {
      position: 'top',
    },
    title: {
      display: true,
      text: 'Total Sales Over Time',
    },
  },
};

function TotalSales() {
  return (
    <div>
      <h2>Total Sales Over Time</h2>
      <Line options={options} data={demoData} />
    </div>
  );
}

export default TotalSales;

// components/SalesGrowth.js
import React from 'react';
import { Bar } from 'react-chartjs-2';
import { Chart as ChartJS, CategoryScale, LinearScale, BarElement, Title, Tooltip, Legend } from 'chart.js';

ChartJS.register(CategoryScale, LinearScale, BarElement, Title, Tooltip, Legend);

const demoData = {
  labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
  datasets: [
    {
      label: 'Sales Growth Rate (%)',
      data: [5, 8, -2, 12, 3, 7],
      backgroundColor: 'rgba(53, 162, 235, 0.5)',
    },
  ],
};

const options = {
  responsive: true,
  plugins: {
    legend: {
      position: 'top',
    },
    title: {
      display: true,
      text: 'Sales Growth Rate Over Time',
    },
  },
};

function SalesGrowth() {
  return (
    <div>
      <h2>Sales Growth Rate Over Time</h2>
      <Bar options={options} data={demoData} />
    </div>
  );
}

export default SalesGrowth;

// components/NewCustomers.js
import React from 'react';
import { Line } from 'react-chartjs-2';
import { Chart as ChartJS, CategoryScale, LinearScale, PointElement, LineElement, Title, Tooltip, Legend } from 'chart.js';

ChartJS.register(CategoryScale, LinearScale, PointElement, LineElement, Title, Tooltip, Legend);

const demoData = {
  labels: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun'],
  datasets: [
    {
      label: 'New Customers',
      data: [50, 65, 45, 80, 70, 90],
      borderColor: 'rgb(255, 99, 132)',
      tension: 0.1,
    },
  ],
};

const options = {
  responsive: true,
  plugins: {
    legend: {
      position: 'top',
    },
    title: {
      display: true,
      text: 'New Customers Added Over Time',
    },
  },
};

function NewCustomers() {
  return (
    <div>
      <h2>New Customers Added Over Time</h2>
      <Line options={options} data={demoData} />
    </div>
  );
}

export default NewCustomers;

// components/RepeatCustomers.js
import React from 'react';
import { Bar } from 'react-chartjs-2';
import { Chart as ChartJS, CategoryScale, LinearScale, BarElement, Title, Tooltip, Legend } from 'chart.js';

ChartJS.register(CategoryScale, LinearScale, BarElement, Title, Tooltip, Legend);

const demoData = {
  labels: ['Daily', 'Monthly', 'Quarterly', 'Yearly'],
  datasets: [
    {
      label: 'Repeat Customers',
      data: [10, 50, 150, 500],
      backgroundColor: 'rgba(75, 192, 192, 0.6)',
    },
  ],
};

const options = {
  responsive: true,
  plugins: {
    legend: {
      position: 'top',
    },
    title: {
      display: true,
      text: 'Number of Repeat Customers',
    },
  },
};

function RepeatCustomers() {
  return (
    <div>
      <h2>Number of Repeat Customers</h2>
      <Bar options={options} data={demoData} />
    </div>
  );
}

export default RepeatCustomers;

// components/GeographicalDistribution.js
import React from 'react';
import { Pie } from 'react-chartjs-2';
import { Chart as ChartJS, ArcElement, Tooltip, Legend } from 'chart.js';

ChartJS.register(ArcElement, Tooltip, Legend);

const demoData = {
  labels: ['New York', 'Los Angeles', 'Chicago', 'Houston', 'Phoenix'],
  datasets: [
    {
      data: [300, 250, 200, 150, 100],
      backgroundColor: [
        'rgba(255, 99, 132, 0.6)',
        'rgba(54, 162, 235, 0.6)',
        'rgba(255, 206, 86, 0.6)',
        'rgba(75, 192, 192, 0.6)',
        'rgba(153, 102, 255, 0.6)',
      ],
    },
  ],
};

const options = {
  responsive: true,
  plugins: {
    legend: {
      position: 'top',
    },
    title: {
      display: true,
      text: 'Geographical Distribution of Customers',
    },
  },
};

function GeographicalDistribution() {
  return (
    <div>
      <h2>Geographical Distribution of Customers</h2>
      <Pie options={options} data={demoData} />
    </div>
  );
}

export default GeographicalDistribution;

// components/CustomerLifetimeValue.js
import React from 'react';
import { Bar } from 'react-chartjs-2';
import { Chart as ChartJS, CategoryScale, LinearScale, BarElement, Title, Tooltip, Legend } from 'chart.js';

ChartJS.register(CategoryScale, LinearScale, BarElement, Title, Tooltip, Legend);

const demoData = {
  labels: ['Jan 2023', 'Feb 2023', 'Mar 2023', 'Apr 2023', 'May 2023', 'Jun 2023'],
  datasets: [
    {
      label: 'Customer Lifetime Value',
      data: [500, 600, 550, 700, 650, 800],
      backgroundColor: 'rgba(255, 159, 64, 0.6)',
    },
  ],
};

const options = {
  responsive: true,
  plugins: {
    legend: {
      position: 'top',
    },
    title: {
      display: true,
      text: 'Customer Lifetime Value by Cohorts',
    },
  },
};

function CustomerLifetimeValue() {
  return (
    <div>
      <h2>Customer Lifetime Value by Cohorts</h2>
      <Bar options={options} data={demoData} />
    </div>
  );
}

export default CustomerLifetimeValue;

```

This React code structure provides a foundation for your data visualization project. Here's a breakdown of what's included:

1. `App.js`: The main component that sets up routing and navigation between different charts.
2. Individual components for each chart type:
   - `TotalSales.js`
   - `SalesGrowth.js`
   - `NewCustomers.js`
   - `RepeatCustomers.js`
   - `GeographicalDistribution.js`
   - `CustomerLifetimeValue.js`

Each component uses demo data to render a chart using react-chartjs-2. The charts are responsive and include titles and legends.

To set up and run this project:

1. Create a new React project:
   ```
   npx create-react-app ecommerce-analytics
   cd ecommerce-analytics
   ```

2. Install necessary dependencies:
   ```
   npm install react-router-dom chart.js react-chartjs-2
   ```

3. Replace the contents of `src/App.js` with the provided `App.js` code.

4. Create a `components` folder in the `src` directory and add the individual chart component files.

5. Run the development server:
   ```
   npm start
   ```

This will give you a working React application with demo data visualizations. To connect it with your backend:

1. Create an API service file (e.g., `api.js`) to handle API calls using axios or fetch.
2. Replace the demo data in each component with API calls to fetch real data from your backend.
3. Update the chart configurations as needed to match your actual data structure.

Remember to handle loading states and potential errors when fetching data from the API. You may also want to add more interactivity, such as date range selectors or filters, to make the dashboard more dynamic and user-friendly.

Let me know if you need any clarification or have questions about implementing specific features!
