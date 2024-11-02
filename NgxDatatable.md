### Step 1: Install `@swimlane/ngx-datatable`

First, ensure that you have `@swimlane/ngx-datatable` installed. You can add it to your Angular project using npm:

```bash
npm install @swimlane/ngx-datatable
```

### Step 2: Import `NgxDatatableModule`

Import the `NgxDatatableModule` in your module file (e.g., `app.module.ts`):

```typescript
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';
import { NgxDatatableModule } from '@swimlane/ngx-datatable';

import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    NgxDatatableModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

### Step 3: Set Up Your Component

Now add the table to your component. For example, in the `app.component.ts`, you could define your data and columns like this:

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  // Sample data
  rows = [
    {
      acct: 'Account 1',
      client: 'John Doe',
      symbol: 'XYZ',
      no: 1,
      nav: 100,
      shares: 50,
      totalValue: 5000,
      allocation: '20%'
    },
    {
      acct: 'Account 2',
      client: 'Jane Doe',
      symbol: 'ABC',
      no: 2,
      nav: 200,
      shares: 25,
      totalValue: 5000,
      allocation: '30%'
    }
    // Add more data as needed
  ];

  columns = [
    { prop: 'acct', name: 'Account Name' },
    { prop: 'client', name: 'Name' },
    { prop: 'symbol', name: 'Symbol' },
    { prop: 'no', name: 'No.' },
    { prop: 'nav', name: 'NAV' },
    { prop: 'shares', name: 'Shares' },
    { prop: 'totalValue', name: 'Total Value' },
    { prop: 'allocation', name: 'Allocation' },
    { name: 'Action' } // No prop as it's for client side actions
  ];
}
```

### Step 4: Create the Template

In your `app.component.html`, you can now create the HTML template for your data table:

```html
<ngx-datatable
  class="material"
  [rows]="rows"
  [columns]="columns"
  [columnMode]="'force'"
  [headerHeight]="50"
  [footerHeight]="50"
  [rowHeight]="'auto'">
  
  <!-- Custom Template for Action Column -->
  <ngx-datatable-column name="Action">
    <ng-template ngx-datatable-cell-template let-row="row">
      <!-- Client-side actions here -->
      <button (click)="onEdit(row)">Edit</button>
      <button (click)="onDelete(row)">Delete</button>
    </ng-template>
  </ngx-datatable-column>

</ngx-datatable>
```

### Step 5: Implement the Action Methods

In `app.component.ts`, implement the methods for handling actions:

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  // ... data and columns ...

  onEdit(row: any): void {
    console.log('Edit row:', row);
    // Implement your edit logic here
  }

  onDelete(row: any): void {
    console.log('Delete row:', row);
    // Implement your delete logic here
  }
}
```
