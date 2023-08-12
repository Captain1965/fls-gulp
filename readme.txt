некоторые новые версии плагинов (в том числе imagemin) не работают через 
requare(), нужно проверять в документации, поэтому необходимо переписать код используя import и export.
import gulp from 'gulp'
import imagemin from 'gulp-imagemin'
import concat from 'gulp-concat'
import sync from 'browser-sync'
const browserSync = sync.create();
import uglify from 'gulp-uglify-es'
и так далее.
Далее все функции оставляете как есть, только перед внутренними методами src, dest, watch, parallel, serises дописуете gulp, то есть где у вас src пишете gulp.src и т.д.
Чтобы экспортировать функцию для запуска с терминала, вместо exports.styles = styles пишете export const stylesRun = styles. Теперь функция styles доступна к выполнению через терминал командой gulp stylesRun. И т.д
И самое главное, что бы это все работало, в файле package.json должно быть прописано свойство "type": "module", как в выложенном файле ТС:
{
"name": "gulp-start",
"version": "1.0.0",
"description": "",
"main": "index.js",
"type": "module", <-----вот сдесь
"scripts": {
"test": "echo \"Error: no test specified\" && exit 1"
},