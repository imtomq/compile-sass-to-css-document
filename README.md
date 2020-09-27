# Compile SASS to CSS

## Cài đặt, tìm hiểu và sử dụng gói node-sass

```bash
npm install node-sass --save
```

or

```bash
npm install --save-dev node-sass
```

- Ở đây chúng ta muốn cài đặt 1 package có tên là **node-sass**, hỗ trợ compile code Sass sang Css. Ta sẽ sử dụng ***npm install node-sass --save***.
- Ở đây mình muốn để node-sass ở dev dependencies vì nó ***chỉ là công cụ hỗ trợ compile code*** chứ ***không phải là 1 phần của project khi chạy thực tế***.

``` js
"devDependencies": {
    "node-sass": "^4.14.1"
  }
```

### Add compile SASS to CSS command in Package.js file

Trong phần **Scripts**, chúng ta thêm lệnh compile SASS sang CSS:

``` js
"scripts": {
    "scss:compile": "node-sass --watch src/assets/scss/ -o src/assets/css/ ",
    ...
  }
```

#### Hãy tìm hiểu từng chi tiết một trong dòng code này.

- ***node-sass***: Là gói gói node-sass.
- ***--watch***: Một cờ hiệu không bắt buộc có nghĩa là **"giám sát tất cả các tập tin .scss trong thư mục scss/ và biên dịch lại chúng mỗi khi có sự thay đổi."**
- ***-w***: sẽ giúp npm theo dõi, cứ mỗi khi file main.scss thay đổi (sau khi save bằng tổ hợp Ctrl +S ) thì sẽ tự động compile sang css.
- ***src/assets/scss/***: Đường dẫn và tên thư mục mà chúng ta đặt tất cả các tập tin .scss của chúng ta.
- ***-o src/assets/css/***: Đường dẫn và thư mục đầu ra cho CSS đã được biên dịch của chúng ta.

## Cài đặt, tìm hiểu và sử dụng node-sass-chokidar

Tương tự như **node-sass**:

``` bash
npm install --save-dev node-sass-chokidar
```

### Add compile SASS to CSS command in Package.js file

Trong phần **Scripts**, chúng ta thêm các lệnh compile SASS sang CSS:

``` js
"scripts": {
  "start": "npm-run-all -p watch-css start-js",
  "build-css": "node-sass-chokidar --include-path  ./src --include-path ./node_modules src/assets/scss/main.scss -o src/assets/css/main.css",
  "watch-css": "npm run build-css && node-sass-chokidar --include-path  ./src --include-path ./node_modules src/assets/scss/main.scss -o src/assets/css/main.css -w -r --usePolling --polling-interval 500",
  "start-js": "react-scripts start",
  ...
}
```

Để hiểu hơn về [node-sass-chokidar](https://www.npmjs.com/package/node-sass-chokidar).

## Tìm hiểu lệnh React-scripts start và luồng chạy

<img src="https://github.com/ImTomQ/Compile-sass-to-css-document/blob/master/src/assets/img/AgqTe.png" width="100%"></img>

Các hộp màu xanh là các tham chiếu đến các tập lệnh, tất cả chúng có thể được thực thi trực tiếp bằng một **npm run <script-name>** lệnh. Nhưng như bạn có thể thấy, thực tế chỉ có 2 luồng thực tế:

- **npm run start**
- **npm run build**

Các hộp màu xám là các lệnh có thể được thực thi từ dòng lệnh.

Vì vậy, ví dụ, nếu bạn chạy **npm start** (hoặc **npm run start**) thực sự dịch sang **npm-run-all -p watch-css start-js** lệnh, được thực thi từ dòng lệnh.

Trong trường hợp của tôi, tôi có **npm-run-all** lệnh đặc biệt này , đây là một plugin phổ biến tìm kiếm các tập lệnh bắt đầu bằng ***"build:"*** và thực thi tất cả các plugin đó. Nó cũng có thể được sử dụng để chạy song song nhiều lệnh, được thực hiện ở đây, bằng cách sử dụng công **-p <command1> <command2>** tắc. **Vì vậy, ở đây nó thực thi 2 script, tức là ***watch-css*** và ***start-js*****.

- Các **watch-css** đảm bảo rằng các **.scss** tập tin được phiên dịch sang **.css** các file, và ngoại hình để cập nhật trong tương lai.

- Các **start-js** điểm để **react-scripts start** lưu trữ trang web trong chế độ phát triển.

Kết luận, **npm start** lệnh có thể cấu hình. Nếu bạn muốn biết nó làm gì, thì bạn phải kiểm tra ***package.json*** tệp. (và bạn có thể muốn tạo một sơ đồ nhỏ khi mọi thứ trở nên phức tạp).

[Bài viết gốc](https://qastack.vn/programming/50722133/what-exactly-is-the-react-scripts-start-command)

# Tổng hợp những bài viết hướng dẫn fix lỗi

[Fix 'unreadable file error' in watch mode after a save in vscode](https://github.com/marcosbozzani/node-sass/blob/bug-vscode-watch/lib/render.js).

[File to read not found or unreadable" with -w under Windows](https://github.com/sass/node-sass/issues/1894)

[Compile sass Error: File to read not found or unreadable](https://github.com/sass/node-sass/issues/2022)

["File to read not found or unreadable" using node-sass when saving on VSCode](https://github.com/microsoft/vscode/issues/20491)

[I am not able to run SASS](https://github.com/facebook/create-react-app/issues/2531)

[I am not able to run SASS into my create-react-app](https://github.com/michaelwayman/node-sass-chokidar/issues/14)

[change files throw error status 3](https://github.com/michaelwayman/node-sass-chokidar/issues/22)

[VSCode won't work with filewatchers](https://stackoverflow.com/questions/50395998/vscode-wont-work-with-filewatchers)