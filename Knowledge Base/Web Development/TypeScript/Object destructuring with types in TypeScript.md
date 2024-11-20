I was using [TypeScript](https://flaviocopes.com/typescript/) in [Deno](https://flaviocopes.com/deno/) to build a sample project and I had to destructure an object. I am familiar with TypeScript basics but sometimes I hit a problem.

Object destructuring was one of those.

I wanted to do

```js
const { name, age } = body.value
```

I tried adding the `string` and `number` types like this:

```ts
const { name: string, age: number } = body.value
```

But this didn’t work. It apparently worked, but in reality this is assigning the `name` property to the `string` variable, and the `age` property value to the `number` variable.

The correct syntax is this:

```ts
const { name, age }: { name: string; age: number } = body.value
```

The best way to approach this would be to create a type or interface for that data:

```ts
interface Dog {
  name: string
  age: number
}
```

Then you can write the above in this way, which is shorter:

```ts
const dog: Dog = body.value
```