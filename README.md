# Image Gallery with React and Tailwind CSS

### Reference website - [Smashing Magazine Article](https://www.smashingmagazine.com/2020/02/tailwindcss-react-project/)

## Tailwind setup

1) npm uninstall tailwindcss @tailwindcss/postcss7-compat
2) npm install tailwindcss@latest postcss@latest autoprefixer@latest postcss-cli-simple

### Reference website - [PostCSS7 Compatibility build](https://tailwindcss.com/docs/installation#post-css-7-compatibility-build)

3) npx tailwind init tailwind.js --full

##### This creates the full tailwind.js config file in the project

4) touch postcss.config.js

##### This creates the postcss.config.js file in the project

In that file, add the following code ...

```
const tailwindcss = require('tailwindcss')

module.exports = {
  plugins: [
    tailwindcss('./tailwind.js'),
    require('autoprefixer')
  ]
}
```
5) Create an assets folder in the src folder and create the files tailwind.css and main.css in that folder.

6) Add the following code in the tailwind.css file ...

```
@import "tailwindcss/base";
@import "tailwindcss/components";
@import "tailwindcss/utilities";
```

##### Do not add any code in the main.css file - this file will be auto populated.

7) Add the following 2 lines under the "scripts" in the package.json file ...
```
"build:css": "postcss --use autoprefixer -c postcss.config.js src/assets/tailwind.css -o src/assets/main.css",
"watch:css": "postcss --use autoprefixer -c postcss.config.js src/assets/tailwind.css -o src/assets/main.css"
```

8) Also in the package.json file, modify the "start" and "build" commands under "scripts" to the following ...
```
"start": "npm run watch:css && react-scripts start",
"build": "npm run build:css && react-scripts build",
```


