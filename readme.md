## Bulletproof Fontface CSS

This method has the deepest support possible. The font-face rule should be added to the stylesheet before any styles.

```scss
$path: '../fonts';  //  path to font files

@font-face {
  font-family: 'My Font';
  src: url('#{$path}/myfont.eot'); //  IE9 Compat Modes
  src: url('#{$path}/myfont.eot?#iefix') format('embedded-opentype'), //  IE6-IE8
       url('#{$path}/myfont.woff2') format('woff2'), //  Super Modern Browsers
       url('#{$path}/myfont.woff') format('woff'), // Modern Browsers
       url('#{$path}/myfont.ttf')  format('truetype'), // Safari, Android, iOS
       url('#{$path}/myfont.svg#svgFontName') format('svg'); // Legacy iOS
}
```

### SASS font variants loop

Loops through the your font variants and generates the declarations.

Adjust the ```$path``` ```$name``` and ```$variants``` variables to suit your needs. Your font files will have to be named accordingly. In this case ```myfont-ultra-light```, ```myfont-regular``` and so on.

```scss

$path: '../fonts';  //  path to font files
$name: 'myfont';  //  base font name
$variants: 'ultra-light', 'light', 'regular', 'medium', 'bold', 'extra-bold' 'black';  //  font variant
$number: length($variants);  //  number of font variants

@for $i from 1 through $number {
    @font-face {
      font-family: '#{$name}-#{nth($variants, $i)}';
      src: url('#{$path}/#{$name}-#{nth($variants, $i)}.eot'); //  IE9 Compat Modes
      src: url('#{$path}/#{$name}-#{nth($variants, $i)}.eot?#iefix') format('embedded-opentype'), //  IE6-IE8
           url('#{$path}/#{$name}-#{nth($variants, $i)}.woff2') format('woff2'), //  Super Modern Browsers
           url('#{$path}/#{$name}-#{nth($variants, $i)}.woff') format('woff'), // Pretty Modern Browsers
           url('#{$path}/#{$name}-#{nth($variants, $i)}.ttf')  format('truetype'), // Safari, Android, iOS
           url('#{$path}/#{$name}-#{nth($variants, $i)}.svg#svgFontName') format('svg'); // Legacy iOS
    }
}

```
