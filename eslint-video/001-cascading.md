# Cascading
> Configuration Cascading and Hierarchy

~~~
When using .eslintrc and package.json files for configuration, you can take advantage of configuration cascading. For instance, suppose you have the following structure:
~~~

~~~
your-project
├── .eslintrc
├── lib
│ └── source.js
└─┬ tests
  ├── .eslintrc
  └── test.js
~~~