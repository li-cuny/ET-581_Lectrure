# Project — Compile & Run Guide

## Compile

### Enable recursive globbing in the shell

```sh
shopt globstar        # check current globstar status (off by default)
shopt -s globstar     # enable globstar (turn on recursive ** support)
```

### Compile your project

```sh
# If globstar is enabled:
javac -d out src/**/*.java

# If globstar is not enabled or you want a shell-independent method:
javac -d out $(find src -name "*.java")
```

> After compilation, your project should have the following structure:

```sh
shopping-system/  # project root
├── data/         # runtime data files
├── src/          # source code (.java)
└── out/          # compiled classes (.class)
```

---

## Run your project

```sh
# Make sure you are in the project root. 
# If not, navigate using "cd folder" or "cd .."
java -cp out com.store.app.Main
```

> This will execute your `Main` class and use the compiled classes in `out/`. The program will read data from the `data/` folder.
This ensures ps.loadProducts("`data/products.txt`") works correctly.
