# DataTable Component

A responsive and accessible data table component built with React and TypeScript.

## Features

- Display tabular data
- Column sorting (click on column headers)
- Row selection (single/multiple)
- Loading state
- Empty state
- Responsive design
- Accessibility features (ARIA labels)

## Usage

```tsx
import React from 'react';
import DataTable, { Column } from './components/DataTable';

interface User {
  id: number;
  name: string;
  email: string;
  age: number;
}

const users: User[] = [
  { id: 1, name: 'John Doe', email: 'john@example.com', age: 30 },
  { id: 2, name: 'Jane Smith', email: 'jane@example.com', age: 25 },
  { id: 3, name: 'Bob Johnson', email: 'bob@example.com', age: 40 },
];

const columns: Column<User>[] = [
  { key: 'id', title: 'ID', dataIndex: 'id' },
  { key: 'name', title: 'Name', dataIndex: 'name', sortable: true },
  { key: 'email', title: 'Email', dataIndex: 'email' },
  { key: 'age', title: 'Age', dataIndex: 'age', sortable: true },
];

const handleRowSelect = (selectedRows: User[]) => {
  console.log('Selected rows:', selectedRows);
};

const App = () => {
  return (
    <div className="app">
      <h1>Users</h1>
      <DataTable
        data={users}
        columns={columns}
        selectable={true}
        onRowSelect={handleRowSelect}
      />
    </div>
  );
};

export default App;
```

## Props

```typescript
interface Column<T> {
  key: string;        // Unique identifier for the column
  title: string;      // Display title for the column header
  dataIndex: keyof T; // Property name in data object to display
  sortable?: boolean; // Whether column is sortable (default: false)
}

interface DataTableProps<T> {
  data: T[];                              // Array of data objects to display
  columns: Column<T>[];                   // Column definitions
  loading?: boolean;                      // Show loading state (default: false)
  selectable?: boolean;                   // Enable row selection (default: false)
  onRowSelect?: (selectedRows: T[]) => void; // Callback when rows are selected
}
```

## Styling

The component includes responsive styling that adapts to different screen sizes. You can customize the appearance by modifying the `DataTable.css` file.