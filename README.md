node--sass --watch /pathFrom -o /pathTo -w

/pathTo auto initialization

Fix 'unreadable file error' in watch mode after a save in vscode:
  https://github.com/marcosbozzani/node-sass/blob/bug-vscode-watch/lib/render.js

---------------------------------------------------------------------------------



npm run start <=> npm start

"scripts": {
  "start": "npm-run-all -p watch-css start-js",
  "build": "npm run build-css && react-scripts build",
  "watch-css": "npm run build-css && node-sass-chokidar --include-path ./src --include-path ./node_modules src/ -o src/ --watch --recursive",
  "build-css": "node-sass-chokidar --include-path ./src --include-path ./node_modules src/ -o src/",
  "start-js": "react-scripts start"
},
