# Welcome to PHPEnum - Dạo này bạn quẩy enum ra sao?

Bạn đã bao giờ phải xử lý enum trong PHP và cảm thấy mệt mỏi với sự lộn xộn và phiền toái chưa? Đừng lo lắng nữa vì
PHPEnum đã sẵn sàng giúp bạn thổi bay những lo lắng!

Tôi dự định sẽ thay thế enum bằng class như các package khác nhưng tôi cho rằng performance không tốt bằng enum native
nên package này đã ra đời. LOL =)))

### Làm thế nào để cài đặt?

Cài đặt PHPEnum cực kỳ đơn giản, chỉ cần sử dụng Composer:

```bash
composer require dnt/php-enum
```

Tại file enum của bạn, hãy use trait `DNT\Enum\EnumUtilities` và... well mọi thứ đã sẵn sàng

```php

use DNT\Enum\EnumUtilities;

enum Status: int {
    // Thêm trait này
    use EnumUtilities;
    
    case SUSPEND = 0;
    case ACTIVE = 1;
    // ...
}
```

### Cách sử dụng

#### toArray

Phương thức này trả về một mảng với key là name enum và value là value enum. Hơi rối nhỉ? Cùng xem mẫu dưới đây

```php
Status::toArray();

// Kết quả:
[
    'SUSPEND' => 0,
    'ACTIVE' => 1
];
```

#### toJson

Phương thức toJson trả về 1 json_encode của phương thức toArray. Bạn cũng có thể truyền thêm các flag vào nếu như không
muốn sử dụng các flag mặc định

```php
Status::toJson();

// Kết quả:
'{
    "SUSPEND": 0,
    "ACTIVE": 1
}';
```

#### getValue

Phương thức cho phép lấy giá trị của enum với input có thể là string(enum name), enum. Nếu không tìm thấy enum null sẽ
được trả về

```php
Status::getValue('SUSPEND');
// Hoặc
Status::getValue(Status::SUSPEND);
// Kết quả: 0
```

```php
Status::getValue('NOT_EXISTS');
// Kết quả: null
```

*Lưu ý: Tham số thứ hai cho biết nếu null thì có throw exception hay không. Mặc định là false*

#### Like a function

Chúng ta cũng có thể lấy 1 instance enum theo cách gọi hàm =))). Tên hàm được chuyển về dạng UPPER_CASE.

```php
Status::suspend();
Status::active();
```

Dễ dàng chứ? Hãy để PHPEnum giúp bạn giải quyết mọi thách thức với enum trong PHP một cách ngầu hết sức!

### Conventions

#### Quy tắc đặt tên case

- Viết hoa tất cả chữ cái
- Các chữ phân cách bởi dấu `_`

VD: USER_ACTIVE, USER_SUSPEND, ...

#### Quy tắc đặt tên hàm

Các tên hàm được đặt theo qui tắc camelCase

- Viết thường chữ đầu
- Các chữ phân cách nhau bằng chữ in hoa

VD: userActive, userSuspend

### Đóng góp

Nếu bạn cảm thấy rằng PHPEnum có thể trở nên ngầu hơn nữa, hãy đóng góp các ý tưởng của bạn. Chúng tôi luôn chào đón.