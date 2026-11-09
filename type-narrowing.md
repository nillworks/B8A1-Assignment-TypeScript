# Type Narrowing in TypeScript: typeof, instanceof, and in

## Introduction

Type narrowing is how TypeScript refines a broad type, such as a union, into a
more specific one inside a block of code. The compiler reads your checks and
automatically updates the type, so you can safely access properties without
unsafe casting.

## Narrowing with typeof

Use typeof for primitive types.

```ts
const format = (value: string | number): string => {
  if (typeof value === 'string') {
    return value.toUpperCase();
  }
  return value.toFixed(2);
};
```

## Narrowing with instanceof

Use instanceof to distinguish class instances, which is very common with errors.

```ts
const handleError = (err: Error | TypeError): string => {
  if (err instanceof TypeError) {
    return `Type problem: ${err.message}`;
  }

  return `Error: ${err.message}`;
};
```

## Narrowing with in

Use the in operator to check whether a property exists on an object.

```ts
type Car = { drive(): void };
type Boat = { sail(): void };

const move = (vehicle: Car | Boat) => {
  if ('drive' in vehicle) {
    vehicle.drive();
  } else {
    vehicle.sail();
  }
};
```
