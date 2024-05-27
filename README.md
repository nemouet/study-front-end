## I. Câu hỏi chung.
1. Document Object Model (DOM) là gì?
- DOM là một giao diện lập trình thể hiện cho web document có cấu trúc như HTML và XML dưới dạng cây đối tượng (tree of objects). Nó định nghĩa cách truy cập, thao tác và sửa đổi các thành phần của documents bằng script language như Javascript.

2. Cách thức Vue có thể manipulate DOM?
- Vue có thể manipulate DOM thông qua directive và reactive data binding.
  1. Virtual DOM: DOM ảo là một bản sao cấu trúc của DOM thực tế. Các thay đổi không được thực hiện đối với DOM thực, thay vào đó, một bản sao của DOM được tạo dưới dạng cấu trúc dữ liệu JavaScript . Khi nào có bất kỳ thay đổi nào, chúng sẽ được thực hiện đối với cấu trúc dữ liệu JavaScript. Cấu trúc sau được so sánh với cấu trúc dữ liệu ban đầu. Những thay đổi cuối cùng sau đó được cập nhật vào DOM thực, người dùng sẽ thấy thay đổi này.
  2. Directives: Vue cung cấp một số directive để manipulate DOM. Một số directive phổ biến bao gồm:
   - v-bind: Bind data từ Vue instance tới các thuộc tính của DOM element, ví dụ: v-bind:class, v-bind:style, v-bind:href...
   - v-on: Gắn sự kiện tới DOM element, ví dụ: v-on:click, v-on:keyup...
   - v-if và v-show: Dùng để điều khiển việc hiển thị và ẩn các phần tử trong DOM.
   - v-for: Dùng để lặp qua một mảng và render các phần tử trong DOM.

  3. Reactive data binding: Vue sử dụng reactive data binding để theo dõi sự thay đổi của các biến trong Vue instance và tự động cập nhật DOM tương ứng. Khi giá trị của biến thay đổi, Vue sẽ tự động update các phần tử liên quan trong DOM mà không cần phải manipulate DOM trực tiếp.

  4. Custom directives: Ngoài các directive tích hợp sẵn, Vue cũng cho phép tạo ra các directive tùy chỉnh để manipulate DOM theo cách riêng. Bằng cách sử dụng custom directives, người dùng có thể thực hiện các thao tác manipulate DOM phức tạp hơn mà không cần phải viết mã JavaScript trực tiếp trong template.

## II. Tóm tắt về project structure và cách thức routing của Nuxt2 
1. Tóm tắt về project structure
- Project gồm các thư mục sau:
    - Components directory: Chứa các components. project này chứa file `Skills.vue`
    - Pages directory: chứa các view của ứng dụng, mỗi một file tương đương 1 routes của ứng dụng. Project này chứa 2 file `About.vue` và `index.vue` tương ứng với trang index và trang about.
    - Plugins directory: chứa các plugin js
    - Static directory: chứa các file static được ánh xạ trực tiếp đến server
    - Nuxt.config.js file: file cấu hình cho dự án Nuxtjs (vd như head có gì, title có gì ... các Plugins nào được chạy trước khi render ra trang...)
    - Package.json File:  chứa các dependencies và scripts cho ứng dụng của bạn.

2. Cách thức routing của Nuxt2
- Routing trong Nuxt2 được quản lý tự động thông qua cấu trúc thư mục và các tệp Vue trong thưc mục `pages`. Ví dụ:
  - `pages/index.vue`: sẽ tương ứng với đường dẫn `/`.
  - `pages/about.vue`: sẽ tương ứng với đường dẫn `/about`.

- Nuxt.js cũng hỗ trợ việc tạo các route lồng nhau bằng cách sử dụng route con của vue-router.

- Ví dụ:
  - Đường dẫn file:
    ```
    pages/
    --| users/
    -----| _id.vue
    -----| index.vue
    --| users.vue
    ```
  - Nó sẽ tự động tạo ra Router:
    ```
    router: {
      routes: [
        {
          path: '/users',
          component: 'pages/users.vue',
          children: [
            {
              path: '',
              component: 'pages/users/index.vue',
              name: 'users'
            },
            {
              path: ':id',
              component: 'pages/users/_id.vue',
              name: 'users-id'
            }
          ]
        }
      ]
    }
    ```

## 3. Câu lệnh để chạy ở môi trường dev và build.
- Câu lệnh ở môi trường dev: `$npm run dev`
- Để build, ta dùng lệnh: `npm run build`
- Sau khi app được build thành công, sử dụng lệnh này để chạy: `npm run start`

