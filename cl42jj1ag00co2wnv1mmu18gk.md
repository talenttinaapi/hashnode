## #1.Basic algorithms problems for frontend developers.

There are many many ways to solve the below algorithms but I am just using the more readable ones. I will share 1 algorithm per post to allow sufficient engagement. If you have any other solutions you can always post the in the comments section.

1. Reverse a string without using revers() JavaScript method.

```
const str = 'Hello world';

const reversString = string => {
  // first - create a new helper string
  let stringReversed = '';

  // second - split the string to get an array from it
  const arrFromString = string.split('');

  // third - loop trough the array
  for (let el of arrFromString) {
    /* forth add each letter from the array 
  in front of the empty helper sting*/
    stringReversed = el + stringReversed;
  }
  // fifth - return the new reversed string
  return stringReversed;
};``` 

