# Test

## Jest

we hava a xxx.js

create a xxx.test.js

![](.gitbook/assets/image%20%289%29.png)

![](.gitbook/assets/image%20%282%29.png)

#### Using Babel

To use [Babel](http://babeljs.io/), install required dependencies via `yarn`

"dependencies": { "babel-core": "^6.26.3", "babel-jest": "^23.6.0", "babel-preset-env": "^1.7.0", "jest": "^24.0.0" }

![](.gitbook/assets/image%20%283%29.png)

#### Using webpack

Jest can be used in projects that use [webpack](https://webpack.github.io/) to manage assets, styles, and compilation. 



### Common Matchers

The simplest way to test a value is with exact equality.

```text
test('two plus two is four', () => {
  expect(2 + 2).toBe(4);
});
```



![](.gitbook/assets/image%20%2817%29.png)

![](.gitbook/assets/image%20%2818%29.png)

## Working Flow

Github own branch

Use jest to test, and then push to my branch.

Other for CI/CD, use jenkins and pull my code, and build and deploy and test in Jenkins.

If there is problem, report to jira. And report this bug, then release new code and fix bug.

Github: version control.  Jenkins: CI/CD.  Jira: show the whole process and report bug.

 

