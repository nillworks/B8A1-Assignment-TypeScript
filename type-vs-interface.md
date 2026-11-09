# TypeScript type vs interface: Which One Should You Use?

## Introduction

Both type aliases and interface describe the shape of data in TypeScript, and
for plain objects they look almost identical. However, they differ in a few
important ways that affect how you design your code.

## Core Differences

Declaration merging.Interfaces with the same name are merged automatically. Type
aliases cannot be redeclared.

```ts
interface User {
  name: string;
}
interface User {
  age: number;
}

const userInformationType: User = { name: 'Rafi', age: 24 };
```

Flexibility. A type can name unions, primitives, and tuples. An interface can
only describe object shapes.

```ts
type Id = string | number;
type Point = [number, number];
type Status = 'idle' | 'loading' | 'done';
```

Extending. Interfaces use extends, while types combine with intersections (&).

```ts
interface Animal {
  name: string;
}
interface Dog extends Animal {
  bark(): void;
}

type Cat = Animal & { meow(): void };
```

## When to Choose Which

Use interface for object shapes, class contracts (implements), and public
library APIs, since merging lets consumers extend them. Use type for unions,
tuples, and complex compositions that an interface cannot express.
