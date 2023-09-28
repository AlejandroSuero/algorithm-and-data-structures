# The last Algorithms Course You'll Need

Course about algorithms and data structures, tought by @ThePrimeagen (he works
at Netflix btw) in the
[FrontendMasters website](https://frontendmasters.com/courses/algorithms).

<p align="center">
  <img src="https://theprimeagen.github.io/fem-algos/images/TheStartup.jpeg" alt="ThePrimeagen, CEO of TheStartup™ TryHarder™" />
</p>

> The course uses TypeScript to show the algorithms and data structures. Learn your types.

```ts
// Is this an array?
const a = [];
```

<p align="center">
    <img src="https://theprimeagen.github.io/fem-algos/images/morphius.jpg" alt="Morphius what if I told you meme, telling you that const a = []; is not an array" />
</p>

Contents:

- [Big O complexity](#big-o-complexity)
- [Data Structures](#data-structures)
- [Algorithms](#algorithms)

## Big O complexity

Categorizes your algorithms time or memory requirements based on input. It's
not meant to be a exact measuremnet. It will not tell you how many CPU cycles it
takes, instead it is meant to generalize the growth of your algorithm.

Example: When someone says O(n), they mean your algorithm will grow linearly
based on input.

Easiest way to tell the Big O complexity, **look for loops**

### O(n)

```ts
function sumCharCodes(n: string): number {
  let sum = 0;
  for (let i = 0; i < n.length; ++i) {
    // every single character in the string
    sum += n.charCodeAt(i);
  }
  return sum;
}
```

### O(n^2)

```ts
function sumCharCodes(n: string): number {
  let sum = 0;
  for (let i = 0; i < n.length; ++i) {
    // every single character in the string
    for (let j = 0; j < n.length; ++j) {
      // every single character in the string
      sum += n.charCodeAt(j);
    }
  }
  return sum;
}
```

## Data Structures

### Arrays

Well if `const a = []` is not an array, what is it?

An array is structure that is a contiguous memory space, meaning unbreaking
memory space (a certain amount of bytes).

```ts
const a = new ArrayBuffer(6);
// a = ArrayBuffer { [Uint8Contents]: <00 00 00 00 00 00>, byteLength: 6 }

const a8 = new Uint8Array(a); // creates a view for the array 'a' of 8 bits
a8[0] = 45;
// a = ArrayBuffer { [Uint8Contents]: <2d 00 00 00 00 00>, byteLength: 6 }
a8[2] = 45;
// a = ArrayBuffer { [Uint8Contents]: <2d 00 2d 00 00 00>, byteLength: 6 }

const a16 = new Uint16Array(a); // creates a view for the array 'a' of 16 bits
// a = ArrayBuffer { [Uint8Contents]: <2d 00 2d 00 00 00>, byteLength: 6 }
a16[2] = 0x4545; // 17733
// a = ArrayBuffer { [Uint8Contents]: <2d 00 2d 00 45 45>, byteLength: 6 }
```

> Note: This happens because the firts memory allocations where of 8 bits, so
> we walked the array in 8 bits positions. But the second time we tried to allocate
> a 16 bits memory, so we walked the array in 16 bits positions. Meaning that
> the second position of 8 bits was `<__ 2d __ __ __ __>` while the second
> position of the 16 bits was `<__ __ __ __ 45 45>`

An array can't grow, so you can't insert data in it, you can overwrite the data
in the memory, but this makes it so you cant't go out of bounds and delete other
memory information.

The same for deletion, you don't "delete" in an array, you overwrite the memory
so it contains nothing, like setting it to 0 or null.

Arrays:

- Fixed size, contiguous memory chunks
- You can't grow it
- There is no "insertAt" or push or pop. Although you can write those functions
  🙄

## Algorithms

### Linear Search

As the name suggests, it will search in O(n) because worst case, it will search
the entire array.
