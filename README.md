# gulp-rev-query
chang gulp-rev manifest to url query format


### Usage

* Pipe `revQ()` after `rev.manifest()`

```js
var rev = require('gulp-rev');
var revQ = require('gulp-rev-query');
var revCollector = require('revCollector');

gulp.task('revCss', function() {
    return gulp.src('src/static/**/*.css')
        .pipe(rev())
        .pipe(gulp.dest('static'))
        .pipe(rev.manifest())
        .pipe(revQ('v')) // ?v=xxxxxxxxx
        .pipe(gulp.dest('static/css'))
}
```

* Specifies `revSuffix`

```js
gulp.task('revCollectorCss', function(){
    return gulp.src(['static/css/**/*.json', 'views/**/*.{html,ejs,jade}'])
        .pipe(revCollector({
            revSuffix: '\\\?v=[0-9a-f]{8,10}',//required
            replaceReved: true,
        }))
        .pipe(gulp.dest('views'))
})

```
