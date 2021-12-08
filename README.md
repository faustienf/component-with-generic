<p align="center">
  <img src="https://raw.githubusercontent.com/faustienf/component-with-generic/main/logo.png" height="50">
</p>
<hr >

#### Define base types
```ts
type Row = Record<string, string>

type Column = {
  id: keyof Row;
  title: string;
}

type Props<C extends Column, R extends Row> = {
  columns: C[];
  rows: R[];
  onSelect: (row: R) => void;
}
```
#### Pass generics into Props
```ts
export const Table = <C extends Column, R extends Row>(props: Props<C, R>) => {
  ...
};
```

#### Define domain types
```tsx
type User = {
  id: string;
  firstName: string;
  lastName: string;
}

type UserColumn = {
  id: keyof User;
  title: string;
}

declare const userColumns: UserColumn[];
declare const users: User[];
```
#### Pass domain props
```tsx
<Table<UserColumn, User>
  columns={userColumns}
  rows={users}
  onSelect={(user/* infered User type */) => {}}
/>
```
`or`
```tsx
<Table
  columns={userColumns}
  rows={users}
  onSelect={(user/* infered User type */) => {}}
/>
```