# Commandline Client

## Directory Layout

The `ssp` binary operates on an directory containing both `*.pkg.ssp` package definitions and `*.comp.ssp` composition definitions. By default it will process all of them.

## Subcommands

### Graph

Extracts the composition graph in the dot graph-format for further consumption.

```
ssp graph --output <OUTPUT> <DIRNAME>
```

The individual dotfiles can be converted to image files with the `dot` utility (graphviz)

```
dot -T svg outdir/Composition.dot > outdir/Composition.svg
```

### Check

Run all transformations (in particular do typechecking) but do not generate outputs.

```
ssp check <DIRNAME>
```

### SMT

Produce smt output for all compositions

```
ssp smt <DIRNAME>
```

One can use `z3` to verify things basically look OK (it should return `sat`)

```
ssp smt <DIRNAME> | z3 -smt2 -in
```

Though one needs additional code to actually solve anything
