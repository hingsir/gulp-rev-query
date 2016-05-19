# gulp-rev-query
chang gulp-rev manifest to url query format


### Usage

* Pipe `revQ()` after `rev.manifest()`

```js
var rev = require('gulp-rev');
var revQ = require('gulp-rev-query');
var revCollectorQ = require('gulp-rev-collector-query');

gulp.task('revCss', function() {
    return gulp.src('src/static/**/*.css')
        .pipe(gulp.dest('static'))
        .pipe(rev())
        .pipe(rev.manifest())
        .pipe(revQ('v')) // ?v=xxxxxxxxx
        .pipe(gulp.dest('static/css'))
}
```

* use `gulp-rev-collector-query`

```js
gulp.task('revCollectorCss', function(){
    return gulp.src(['static/css/**/*.json', 'views/**/*.{html,ejs,jade}'])
        .pipe(revCollectorQ({
            replaceReved: true,
        }))
        .pipe(gulp.dest('views'))
})

```
