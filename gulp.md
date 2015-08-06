#Gulp Style Guide

[GulpJS](http://gulpjs.com/) is a JavaScript/Node task runner providing streamlined build processes and task management.
The following is some best practices and standards in organizing and building gulp tasks.

##Naming Conventions

- Tasks should be all lower case. Private tasks or tasks not for regular development use should have a leading underscore. Example: `_subtask1` and `primarytask`.
- When naming sub tasks use the `.` notation. Example `build`, `_build.sass`, `build.typescript`, ect.
- Use `--` for modified eviroment tasks. Example `build` for production builds and `build--dev` for development builds.


##Configuration
- `gulp build` should be reserved to run production ready builds. This makes integrating gulp builds into a automated system simpler.
- Magic strings such as file paths or locations should be stored in a configuration object in the `gulp.config.js`. 

Example `gulp.config.js`: 
``` javascript
  module.exports = function() {
   var config = {
          src: {
              sass: [
                './styles/app.scss'
              ],
              typescript: [
                './app/**/*.ts',
              ]
          }
   	}
      return config;
  }
```


##Documenting Gulp Tasks
- Use `gulp-help` or a equivalent plugin to document available tasks in your gulp api. 
- The default Gulp task should be the help task.

Example: 

![Example image of a gulp help task](https://raw.githubusercontent.com/vintage-software/javascript/master/assets/gulp-help.PNG)
