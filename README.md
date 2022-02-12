# algorithm

## Union Find

* Quick Find



```js
class QuickFindUF{

  constructor(n) {
    this.id = new Array(n)
    for (let i=0; i < n; i++) {
      this.id[i] = i
    }
  }

  // TC: O(1)
  connected(p, q) {
  	const id = this.id
    return id[p] === id[q];
  }

  // TC: O(N)
  union(p, q) {
    const pid = this.id[p];
    const qid = this.id[q];
    for(let i=0; i<this.id.length; i++) {
      if(this.id[i] == pid) {
        this.id[i] = qid;
      }
    }
  }

  get() {
		return this.id
  }
}

const qf = new QuickFindUF(5)
console.log(qf.connected(1,2)) // false
console.log(qf.get()) // [0, 1, 2, 3, 4]
qf.union(1,2)
console.log(qf.connected(1,2)) // true
console.log(qf.get()) // [0, 2, 2, 3, 4]
```

* Quick Union

```js
class QuickUnionUF{

  constructor(n) {
    this.id = new Array(n)
    for (let i=0; i < n; i++) {
      this.id[i] = i
    }
  }

  // TC: O(1)
  // try to find the root
  find(i) {
  	while (this.id[i] !== i) {
      i = this.id[i]
    }
    return i
  }

  // TC: O(N)
  union(p, q) {
    let i = this.find(p)
    let j = this.find(q)
    this.id[i] = j
  }

  get() {
		return this.id
  }
}

const qf = new QuickUnionUF(5)
console.log(qf.get()) // [0, 1, 2, 3, 4]
qf.union(1,2)
console.log(qf.get()) // [0, 2, 2, 3, 4]
qf.union(1,4)
console.log(qf.get()) // [0, 2, 4, 3, 4]
console.log(qf.find(1)) // 4
```

```js

function quickSort(array, left, right) {
  left = left || 0
  right = right || array.length-1

  const pivot = partition(array, left, right)
  //console.log(pivot)
  if (left < pivot - 1) {
    quickSort(array, left, pivot-1)
  }

  if (right > pivot) {
    quickSort(array, pivot, right)
  }

  return array
}

function partition(array, left, right) {
  const p = Math.floor((left + right) / 2)
  while (left <= right) {
    while (array[left] < array[p]) {
      left++
    }
    while (array[right] > array[p]) {
      right--
    }

    if (left <= right) {
      [array[left], array[right]] = [array[right], array[left]];
      console.log(array)
      left++
      right--
    }
  }
  return left
}
//const arr1 = [11, 53, 233, 11]
const arr1 = [11, 53, 233, 53]
console.log(quickSort(arr1))

```