# Compile SASS to CSS

## Install SASS

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

## Add compile SASS to CSS command in Package.js file

Trong phần **Scripts**, chúng ta thêm lệnh compile SASS sang CSS:

``` js
"scripts": {
    "scss:compile": "node-sass --watch src/assets/scss/ -o src/assets/css/ ",
    ...
  }
```

### Hãy tìm hiểu từng chi tiết một trong dòng code này.
- ***node-sass***: Là gói gói node-sass.
- ***--watch***: Một cờ hiệu không bắt buộc có nghĩa là **"giám sát tất cả các tập tin .scss trong thư mục scss/ và biên dịch lại chúng mỗi khi có sự thay đổi."**
- ***-w***: sẽ giúp npm theo dõi, cứ mỗi khi file main.scss thay đổi (sau khi save bằng tổ hợp Ctrl +S ) thì sẽ tự động compile sang css.
- ***src/assets/scss/***: Đường dẫn và tên thư mục mà chúng ta đặt tất cả các tập tin .scss của chúng ta.
- ***-o src/assets/css/***: Đường dẫn và thư mục đầu ra cho CSS đã được biên dịch của chúng ta.
