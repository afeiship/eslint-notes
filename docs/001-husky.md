# husky:

## install
```shell
npm install husky --save-dev
```

## config:
```json
// package.json
{
  "husky": {
    "hooks": {
      "pre-commit": "npm test",
      "pre-push": "npm test",
      "...": "..."
    }
  }
}
```

## test:
git commit -m 'Keep calm and commit'