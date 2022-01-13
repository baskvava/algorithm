# algorithm

## Quick Union

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

  // TC: O(N ^ 2)
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
