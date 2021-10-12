* `async` and `await` are syntactic sugar for `Promises`.
* `await` can be user in `async` function
* `await` pauses the executin of `async` function untill the `Promise` is resolved a.k.a the result is known. 
* if `Promise` is rejected the rejection reason is thrown. Therefore itis better to use `Error` instance as a reason.
* the following is possible `let res = await promise.catch(err => console.error(err));`. `res` will be indefined in promise was rejected.
