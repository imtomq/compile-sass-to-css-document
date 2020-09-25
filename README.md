# Compile Sass to Css

## Install Sass

```bash
npm install node-sass --save
```

or

```bash
npm install --save-dev node-sass
```

- Ở đây chúng ta muốn cài đặt 1 package có tên là **node-sass**, hỗ trợ compile code Sass sang Css. Ta sẽ sử dụng ***npm install node-sass --save***.

- Ở đây mình muốn để node-sass ở dev dependencies vì nó cũng chỉ là công cụ hỗ trợ compile code chứ không phải là 1 phần của project khi chạy thực tế.

``` js
"devDependencies": {
    "node-sass": "^4.14.1"
  }
```

