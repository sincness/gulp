# 🎊 Gulp Quick Setup
Gulp Compiler Setup 🌵

> **1.** npm init --y

> **2.** npm i -D gulp gulp-rename gulp-connect gulp-sourcemaps

> **3.** Ændre ***package.json***
> - **"main": "gulpfile.js"**,
> - *Under scripts {}*
> > **"dev": "gulp"**

> **4.** Opret din ***gulpfile.js***


> ~~~~
> const gulp = require('gulp');
> const sourcemaps = require('gulp-sourcemaps');
> const rename = require('gulp-rename');
> const connect = require('gulp-connect');
> 
> function defaultTask(done) {
>     console.log('defaultTask() complete')
>     // placer koden for den almindeligvis kørte opgave her
>     gulp.src("src/html/**/*.html")
>         .pipe(sourcemaps.init())
>         .pipe(
>             rename(function(path){
>                 if (path.basename != "index") {
>                     path.dirname = path.basename;
>                     path.basename = "index";
>                     path.extname = ".html";
>                 } else {
>                     path.extname = ".html";
>                 }
>             })
>             )
>         .pipe(gulp.dest("dist"));
> 
>     connect.server({
>         livereload: true,
>         root: "dist"
>     })
>     done();
> }
> 
> exports.default = defaultTask;
> ~~~~
