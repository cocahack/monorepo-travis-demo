# monorepo-travis-demo

Test CI/CD in monorepo and apply git branch strategy.

## How configured you this project?

1. First, make yarn workspace

    ```bash
    user@~ $ mkdir monorepo-travis-demo && cd monorepo-travis-demo
   
    user@~/monorepo-travis-demo $ cat << EOF >> package.json 
    {
      "private": true,
      "name": "monorepo-travis-demo",
      "workspaces": [
        "packages/*"
      ],
      "scripts": {}
    }
    EOF
    ```

2. Create react app

    ```bash
    user@~/monorepo-travis-demo $ yarn create react-app packages/client --template typescript
    ```

    After installing react project, all dependencies locate `node_modules` directory in root.
 
3. Create nest.js app

    ```bash
    user@~/monorepo-travis-demo $ nest n --directory packages -p yarn server
    ```
  
****
Project structure

```
.
├── README.md
├── monorepo-travis-demo.iml
├── node_modules // All dependencies locate here
├── package.json
├── packages
│   ├── client
│   │   ├── README.md
│   │   ├── node_modules // Symbolic links locate here
│   │   ├── package.json
│   │   ├── public
│   │   ├── src
│   │   ├── tsconfig.json
│   │   └── yarn.lock
│   └── server
│       ├── README.md
│       ├── nest-cli.json
│       ├── node_modules // Symbolic links locate here
│       ├── package.json
│       ├── src
│       ├── test
│       ├── tsconfig.build.json
│       ├── tsconfig.json
│       └── tslint.json
└── yarn.lock
```

