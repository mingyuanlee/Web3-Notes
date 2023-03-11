## Work with files

### Packages

1. mime: npm packages working with file types
1. fs: node.js module working with file system
1. path: node.js module working with file system paths

### Read file

```
const content = await fs.promises.readFile(filePath)
```

### Get file type

```
const type = mime.getType(filePath)
```

### Get file name

```
path.basename(filePath)
```


## Environment

1. ```dotenv```: loads environment variables from a .env file into process.env
1. Create a ```.env``` file in the root of the project.
1. Import: ```require('dotenv').config()```
1. Load variables: ```const { CONTRACT_ADDRESS, PUBLIC_ADDRESS } = process.env;```

