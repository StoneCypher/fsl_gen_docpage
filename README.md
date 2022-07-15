# fsl_gen_docpage
CLI tool to create a documentation page from an FSL machine, suitable for documentation generators like TypeDoc, Swagger, ESDoc, or unix man

```
npm install --save fsl_gen_docpage
fsl_gen_docpage -i ./src/fsl/**/*.fsl -f typedoc -P -S -I -d ./docs/docs/machines
```




&nbsp;

&nbsp;

## Quick start

To:

* take a file called `tcp_ip.fsl`, 
    * `-i tcp_ip.fsl`
* render it formatted for [typedoc](https://typedoc.org/), 
    * `-f typedoc`
* output under the filename `tcp_ip.md`, 
    * `-o tcp_ip.md`
* generate a `PNG` image under the name `tcp_ip.fsl.png`, 
    * `-P`
* generate an `SVG` image under the name `tcp_ip.fsl.svg`, 
    * `-S`
* make the machine interactive in a browser
    * `-I`
* make the machine to put the documentation file, image file, CSS, and 
  javascript file into a directory called `./docs/docs/machines`, 
    * `-d ./docs/docs/machines`
  
issue the following command:

```
fsl_gen_docpage -i tcp_ip.fsl -f typedoc -o tcp_ip.md -P -S -I -d ./docs/docs/machines
```

In this configuration, `fsl_gen_docpage` will throw one markdown file, one PNG, one 
SVG, one javascript file, and one CSS file into the nominated directory.

Globs are also valid, so you might see something like

```
fsl_gen_docpage -i ./src/fsl/**/*.fsl -f typedoc -P -S -I -d docs/docs/machines
```

In this configuration, `fsl_gen_docpage` will throw a bunch of markdown files, the same
number of PNGs, and of SVGs, but still just one javascript file and one CSS file into 
the same nominated directory.

Note that with the output name omitted, the formatting plugin will choose the output
name; the typedoc plugin adds `.md` onto the existing filename, so will write to
`tcp_ip.fsl.md` and so forth.

When using `**` in a glob, `fsl_gen_docpage` will honor the directory structure it 
finds.  So, if your `./src/fsl` in this example has subdirectories, so will the output
directories.  The single JS and single CSS will be at the named output directory and
referenced with `..` from the generated content.
