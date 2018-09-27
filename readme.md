### Bulletproof Fontface CSS

This is the method with the deepest support possible. The font-face rule should be added to the stylesheet before any styles.

```scss
$path: '../fonts';  //  path to font files

@font-face {
  font-family: 'My Font';
  src: url('#{$path}/myfont.eot'); //  IE9 Compat Modes
  src: url('#{$path}/myfont.eot?#iefix') format('embedded-opentype'), //  IE6-IE8
       url('#{$path}/myfont.woff2') format('woff2'), //  Super Modern Browsers
       url('#{$path}/myfont.woff') format('woff'), // Pretty Modern Browsers
       url('#{$path}/myfont.ttf')  format('truetype'), // Safari, Android, iOS
       url('#{$path}/myfont.svg#svgFontName') format('svg'); // Legacy iOS
}
```
