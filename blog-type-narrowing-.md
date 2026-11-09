# What Is Type Narrowing in TypeScript?

## Introduction

Type narrowing is an important feature of TypeScript that helps developers work safely with different data types. It allows TypeScript to identify a variable's specific type within a particular block of code. This reduces type errors and makes applications more reliable.

## Understanding Type Narrowing

TypeScript supports several techniques for narrowing types. Three commonly used approaches are `typeof`, `instanceof`, and the `in` operator.

### 1. Using typeof

The `typeof` operator checks the type of a variable at runtime. It is useful when working with union types such as strings and numbers.

```typescript
function processValue(value: string | number): string {
  if (typeof value === "string") {
    return value.toUpperCase();
  }

  return value.toString();
}
```

Here, TypeScript understands that `value` is a string inside the first condition and a number outside it.

### 2. Using instanceof

The `instanceof` operator checks whether an object belongs to a particular class.

```typescript
class Developer {
  writeCode(): string {
    return "Writing TypeScript code";
  }
}

function checkDeveloper(person: Developer | Date): string {
  if (person instanceof Developer) {
    return person.writeCode();
  }

  return person.toDateString();
}
```

### 3. Using the in Operator

The `in` operator checks whether an object contains a specific property.

```typescript
type Admin = { role: string; permissions: string[] };
type User = { name: string };

function getUserInfo(person: Admin | User): string {
  if ("permissions" in person) {
    return person.role;
  }

  return person.name;
}
```

## Conclusion

Type narrowing makes TypeScript code safer, cleaner, and easier to maintain. By using `typeof`, `instanceof`, and the `in` operator, developers can handle different data types confidently without relying on unnecessary type assertions.
