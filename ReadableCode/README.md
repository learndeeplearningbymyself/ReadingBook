## Readable Code

Dịch tóm tắt từ sách [Readable code - bản tiếng Nhật](https://www.amazon.co.jp/%E3%83%AA%E3%83%BC%E3%83%80%E3%83%96%E3%83%AB%E3%82%B3%E3%83%BC%E3%83%89-%E2%80%95%E3%82%88%E3%82%8A%E8%89%AF%E3%81%84%E3%82%B3%E3%83%BC%E3%83%89%E3%82%92%E6%9B%B8%E3%81%8F%E3%81%9F%E3%82%81%E3%81%AE%E3%82%B7%E3%83%B3%E3%83%97%E3%83%AB%E3%81%A7%E5%AE%9F%E8%B7%B5%E7%9A%84%E3%81%AA%E3%83%86%E3%82%AF%E3%83%8B%E3%83%83%E3%82%AF-Theory-practice-Boswell/dp/4873115655/ref=sr_1_1?adgrpid=52747835709&gclid=CjwKCAjwr8zoBRA0EiwANmvpYCH2NZYfDkMnd-j8zdh50wzDEnLTtAavPnsRYb6wsturOpgWvw0EwxoCN0EQAvD_BwE&hvadid=338541255723&hvdev=c&hvlocphy=1009309&hvnetw=g&hvpos=1t1&hvqmt=e&hvrand=6448826365599410260&hvtargid=aud-762433167318%3Akwd-334307148361&hydadcr=16038_11170847&jp-ad-ap=0&keywords=%E3%83%AA%E3%83%BC%E3%83%80%E3%83%96%E3%83%AB%E3%82%B3%E3%83%BC%E3%83%89&qid=1561602682&s=gateway&sr=8-1)

### Chương 1: Code dễ hiểu

> Key: Viết code phải sao cho dễ hiểu

### 1.1. Thế nào là **code tốt**

Ta xét 2 ví dụ sau:

VD1:
```C++
return exponent >= 0 ? mantissa * (1 << exponent) : mantissa / (1 << -exponent)
```

VD2:
```C++
if (exponent >= 0) {
    return mantissa * (1 << exponent);
} else {
    return mantissa / (1 << -exponent);
}
```

Code ở ví dụ 1 khá là đơn giản, nhưng code ở ví dụ 2 lại đem đến cảm giác **yên tâm** (có thể hiểu theo nghĩa là **dễ đọc, dễ hiểu**) hơn cho người đọc. Giữa **đơn giản** và **yên tâm** yếu tố nào là quan trọng hơn?

### 1.2. Định lí cơ bản về việc code dễ đọc

> Key: Code sao cho người khác chỉ mất một khoảng thời gian ngắn cũng có thể đọc hiểu

Cần tính toán khoảng thời gian mà người khác sẽ mất khi đọc code của mình, chúng ta cần cố gắng giảm thiểu tối đa khoảng thời gian này

**Hiểu code** ở đây được hiểu theo nghĩa là **có khả năng** thay đổi được code, tìm được bug.

`Để người khác đọc hiểu code` - cụm từ **người khác** ở đây có thể hiểu theo nghĩa là **chính bản thân mình** sau 6 tháng không đọc code. Có thể sẽ có những **modules** sẽ được sử dụng cho các project khác, nên việc viết code để **người khác** hiểu là vô cùng quan trọng.

### 1.3. Liệu ngắn có hẳn là tốt ?

Có thể thấy rõ ràng thời gian để đọc một class có 2000 dòng code là ngắn hơn so với thời gian đọc một class có 5000 dòng code.

Nhưng như ở [ví dụ ở phần 1.1](#11thế-nào-là-code-tốt) code ngắn đôi khi tốn thời gian để hiểu hơn là code dài.

Việc thêm comment có thể khiến code dài hơn, nhưng lại dễ hiểu hơn nhiều

Ví dụ:
```C++
//"hash = (65599 * hash) + c" - high speed version
hash = (hash << 6) + (hash << 16) - hash + c;
```

Việc viết code để tiết kiệm thời gian đọc hiểu quan trọng hơn việc viết code ngắn.

### 1.4. [Thời gian đọc hiểu code] là một sự mâu thuẫn?

[Chúng ta có thể thấy còn có những yếu tố khác cũng quan trọng như: code có hiệu năng cao hay không ?, test có dễ hay không ?]

Thực tế thì việc viết code dễ hiểu không hề cạnh tranh với các yếu tố trên. Việc viết code dễ hiểu cũng luôn gắn liền với thiết kế tốt và test dễ dàng.

> Khi đọc code lần đầu tiên, thay vì nghĩ ngay đến việc refactor code hãy tự hỏi rằng liệu code này có dễ hiểu hay không.

### 1.5. Phần khó khăn

Phần khó khăn nhất có lẽ là tưởng tượng khi người khác đọc code của mình, họ sẽ nghĩ như thế nào.

Thế nhưng nếu làm được điều này, chúng ta hoàn toàn có thể trở thành những lập trình viên **trình cao** hơn.

### Chương 2: Đặt tên biến bao hàm thông tin

Khi đặt tên cho hàm, biến, class chúng ta sẽ áp dụng cùng một nguyên tắc đó là:

> Tên cũng là một cách comment ngắn gọn

Đặt tên biến cần ngắn nhưng vẫn phải đảm bảo truyền đạt nhiều thông tin nhất có thể

> Key: Tên nên bao hàm thông tin trong đó

### 2.1. Sử dụng từ ngữ tường minh khi đặt tên

Tránh sử dụng những từ ngữ trống rỗng khi đặt tên. Ví dụ như [get] là 1 từ hoàn toàn tối nghĩa

```ruby
def GetPage(url):
    ...
```
Bản thân từ **get** cũng không truyền tải bất kì ý nghĩa gì. Phương thức này sẽ lấy page từ đâu về ? (local cache, database, internet?). Nếu lấy từ internet thì nên là **FetchPage()** hoặc **DownloadPage()** thì sẽ rõ nghĩa hơn.

Tiếp theo là ví dụ của class **BinaryTree**

```java
class BinaryTree {
    int Size();
};
```
Phương thức **Size()** này sẽ trả về kết quả gì ? Chiều cao của cây ? Số lượng node ? Lượng bộ nhớ mà cây sử dụng ?. Nếu đặt tên theo đúng như những mục đích trên thì tên phương thức sẽ lần lượt là **Height()**, **NumNodes()**, **MemoryBytes()**

Một ví dụ khác đó là class **Thread**

```java
class Thread {
    void Stop();
};
```
Cái tên **Stop()** không hẳn đã là tồi nhưng nếu để phù hợp hơn với hành động - mục đích của phương thức thì những trường hợp sau đây nên được cân nhắc. Ví dụ: nếu là task nặng thì đặt là **Kill()**, nếu dừng nhưng sau đó có thể khởi chạy **(Resume)** trở lại thì nên đặt là **Pause()**

Tìm kiếm những từ ngữ **đa dạng** hơn
```
send = deliver, dispatch
find = search, extract
start = launch, begin
make = create, build
```
**Chú ý** tới việc trùng tên với từ khoá của ngô ngữ lập trình đang sử dụng

> Key: Không sử dụng cách nói vòng vo khi đặt tên mà nên đặt tên một cách tường minh, rõ ràng

### 2.2. Tránh sử dụng những tên chung chung như tmp, retval

Tránh chọn những tên trống rỗng như **tmp**, **retval**, **foo**, mà thay vào đó hãy chọn những tên biểu thị đúng mục đích và đặc tính của giá trị mà biến đó sẽ nhận.

Ví dụ:
```javascript
var euclidean_norm = function(v) {
    var retval = 0.0;
    for (var i = 0; i < v.length; i += 1) {
        retval += v[i] * v[i];
    }
    return Math.sqrt(retval);
}
```
Một cái tên tốt có nghĩa là biến hoặc hàm phải biểu thị rõ mục tiêu và giá trị của nó.　Trong ví dụ trên biến **retval** có thể thay bằng **sum_squares**. Điều này giúp cho việc thể hiện mục tiêu dễ dàng hơn cũng như hữu ích khi tìm bug.

Tuy nhiên cũng có những trường hợp những tên tưởng chừng như sáo rỗng này lại có ý nghĩa. Chúng ta cùng xem ví dụ sau

```java
if (right < left) {
    tmp = right;
    right = left;
    left = tmp;
}
```

Đây là ví dụ kinh điển về đoạn code đảo giá trị của 2 số. Đặt tên biến là **tmp** sẽ cho thấy rằng đây là biến chỉ mang ý nghĩa là lưu trữ thông tin tạm thời, có khoảng thời gian tồn tại khá ngắn, ngoài ra nó không có ý nghĩa nào khác, đồng nghĩa với việc nó sẽ không được truyền vào hàm khác hay được ghi đè gía trị ở một vị trí nào khác trong chương trình.

Dưới đây cũng là một ví dụ khá hay về việc sử dụng biến **tmp**

```java
tmp_file = tempFile.NamedTemporaryFile()
SaveData(tmp_file)
```

Nếu thay vì là **tmp_file** mà là **tmp** thì sẽ không có sự rõ ràng khi người đọc sẽ không biết **tmp** là gì (file hay tên file, ...)

> Advise: Nên sử dụng biến tmp một cách thận trọng cho mục đích lưu trữ ngắn hạn và tồn tại trong khoảng thời gian ngắn

**Loop iterator**

- Những tên biến như **i, j, k, iter** tuy là những tên tối nghĩa nhưng thường được sử dụng để làm **index** hoặc **loop iterator**, nếu sử dụng với mục đích khác có thể gây hiểu nhầm.

- Tuy nhiên có những cái tên có ý nghĩa hơn là **i, j, k, iter**
Ta xét ví dụ sau
```c++
for (int i = 0; i < clubs.size(); i++) {
    for (int j = 0; j < clubs[i].members.size(); j++) {
        for (int k = 0; k < users.size(); k++) {
            if (clubs[i].members[k] == users[j]) {
                cout << "user[" << j << "] is in club[" << i << "]  << endl;
            }
        }
    }
}
```

Thoạt nhìn, đoạn code trên không hề có lỗi nhưng nếu để ý kĩ thì index của **members** và **users** là ngược nhau, đúng ra phải là

```c++
if (clubs[i].members[j] == users[k])
```

Trong trường hợp có nhiều iterators, ta có thể thêm tiếp đầu ngữ cho các biến, như ở ví dụ trên thay vì là **i**, **j**, **k** ta sẽ đặt tên như sau **ci**, **mi**, **ui**. Khi đó việc phát hiện lỗi cũng sẽ dễ hơn rất nhiều

```c++
if (clubs[ci].members[ui] == users[mi]) # Bug, tiếp đầu ngữ của iterator sai
```

> Advise: Khi sử dụng những tên biến tối nghĩa như tmp, it, retval cần cân nhắc lí do sử dụng thật kĩ lưỡng

Hãy từ bỏ thói quen **sử dụng những tên vô nghĩa như foo khi không nghĩ ra tên thích hợp để đặt cho biến, hàm, class**. Thay vào đó, sử dụng 1 chút thời gian để nghĩ tên thích hợp, nếu biến điều đó thành thói quen thì khả năng đặt tên sẽ tăng lên đáng kể.

### 2.3. Sử dụng những tên mang tính cụ thể thay vì mang tính trừu tượng

Ta xét ví dụ với phương thức **ServerCanStart()**, phương thức này có nhiệm vụ xác nhận xem liệu server có thể lắng nghe ở 1 cổng TCP/IP hay không, nếu nhiệm vụ của phương thức là như vậy thì cái tên **ServerCanStart** là khá trừu tượng, thiếu tính cụ thể, thay vào đó ta có thể đặt tên là **CanListenOnPort**

### 2.4. Thêm thông tin vào tên

Như đã nói ở phần trước, đặt tên tốt cũng là một cách comment ngắn gọn. Vì thế, nếu có thông tin nào buộc phải thông báo cho người đọc code thì phải dùng từ ngữ để truyền đạt thông tin đó thông qua tên biến, hàm, ...

Xét ví dụ:
```java
String id; // VD: aft3h454hj54
```

Nếu ID format là quan trọng thì nên đặt tên là **hex_id**

**Đơn vị của giá trị**

Với các biến liên quan đến **thời gian**, **bộ nhớ** thì nên thêm đơn vị cho tên biến (**_ms**, **_byte**)

Xét ví dụ

```javascript
var start = (new Date()).getTime();

var elapsed = (new Date()).getTime() - start;

document.writeln("Read time: " + elapsed + " sec");
```

Đoạn code trên nhìn qua có vẻ không vấn đề gì nhưng thực chất hàm **getTime** sẽ trả về đơn vị là **ms**. Nên để dễ hiểu và rõ ràng hơn, đoạn code trên nên sửa như sau

```javascript
var start_ms = (new Date()).getTime();

var elapsed_ms = (new Date()).getTime() - start_s;

document.writeln("Read time: " + elapsed_ms * 1000 + " sec");
```

**Thêm những thuộc tính quan trọng khác**

Ngoài việc thêm thông tin về đơn vị vào tên biến, còn có các thông tin quan trọng khác như là **chú ý**, **nguy hiểm**, ...

Ví dụ về vấn đề an toàn thông tin. Đa phần nguyên nhân là do chương trình nhận các dữ liệu thiếu đi tính an toàn. Vì thế với các dữ liệu kiểu này, các tên biến như **untrustedUrl**, **unsafeMessageBody** sẽ là thích hợp. Nếu như sau khi xử lí bằng các hàm tăng tính an toàn cho dữ liệu thì các tên như **trustedUrl** hoặc **safeMessageBody** là khá phù hợp

Bảng dưới đây sẽ biểu thị việc thêm thông tin vào tên biến là quan trọng như thế nào

| Trạng thái | Tên biến thông thường | Tên biến phù hợp |
| ---------- | --------------------- | ---------------- |
| password đang ở dạng plain text, nên trước khi xử lí phải tiến hành mã hoá | password | plaintext_password |
| Trước khi hiển thị comment của người dùng càn tiến hành escaped | comment | unescaped_comment |
| Chuyển mã kí tự của html thành mà UTF-8 | html | html_utf8 |
| URL Encode dữ liệu nhập vào | data | data_urlenc |

Tóm lại hãy thêm các thuộc tính vào những chỗ thể hiện ý nghĩa quan trọng của biến

### 2.5. Quyết định độ dài của tên

Một trong những quy ước ngầm đó chính là tên của biến không nên quá dài. Việc quyết định độ dài của tên hoàn toàn phụ thuộc vào mục đích sử dụng của biến

Dưới đây là một vài quy tắc đơn giản sẽ hỗ trợ chúng ta trong việc quyết định độ dài của tên biến

### Các tên ngắn sẽ thích hợp hơn với scope ngắn

```java
if (debug) {
    map<string,int> m;
    LookUpNamesNumbers(&m);
    Print(m);
}
```

Ở ví dụ trên, tên biến m có thể không mang quá nhiều ý nghĩa nhưng với một scope nhỏ như trên (trong phạm vi 1 câu lệnh **if**) thì việc đặt tên như vậy cũng không hẳn đã gây khó khăn cho người đọc.

Nhưng với scope lớn hơn, hoặc là **global variable** thì đặt tên như vậy sẽ không bao hàm đủ thông tin cần thiết.

### Sử dụng một cái tên dài hơn - Không còn bất kì vấn đề nào nữa

Có rất nhiều lí do để tránh đặt một cái tên dài, một trong số đó là **khó để iết**, nhưng các **text editor** hiện đại đều có chức năng **word completion** để có thể hoàn thiện từ một cách tự động

### Các từ viết tắt

Thông thường các từ viết tắt sẽ được sử dụng trong các project (VD: thay vì **BackEndManager** thì sẽ là **BEManager**). Việc này thường có hại hơn là có lợi, đặc biệt với những người mới tham gia vào project (khó hiểu, mang tính chất mã hoá quá mạnh)

Tuy nhiên với các từ viết tắt phổ biến như **str - string** **eval - evaluation**, thì việc đọc hiểu cũng sẽ không quá khó khăn

### Loại bỏ các từ thừa

Có những trường hợp loại bỏ đi những từ thừa trong tên biến mà vẫn không làm mất mát đi thông tin trong đó. Ta có thể lấy ví dụ như sau

**ConvertToString** -> **ToString**
**DoServeLoop** -> **ServeLoop**

### 2.6. Truyền tải thông tin thông qua format tên

Chúng ta có thể sử dụng các kí hiệu như _, /, chữ in hoa để truyền tải thông tin cho tên biến. VD như ở open source project (C++) của google sẽ có 1 vài quy ước đặt tên biến, class, hàm như sau.

Ví dụ ở đoạn code
```c++
static const int kMaxOpenFiles = 100;

class LogReader {
    public:
        void OpenFile(string local_file);

    private:
        int offset_;
        DISALLOW_COPY_AND_ASSIGN(LogReader);
}
```

Ta có thể rút ra được một vài quy tắc như sau
- Tên class - **CamelCase**
- Tên thuộc tính class - **lower_separated**
- Tên hằng số không phải là **CONSTANT_NAME** mà là **kConstantName**, tên viết hoa hoàn toàn sẽ được dùng cho **MACRO_NAME**
- Tên biến của class sẽ là **lower_** để phân biệt với **local variables**

### Các quy ước khác về format tên

- Với **jQuery**
  - Các biến là jquery object sẽ có **$** trong chữ cái đầu tiên của tên

- Với **javascript** thông thường (quy tắc được đề cập ở cuốn [JavaScript: The Good Parts](https://www.amazon.co.jp/JavaScript-Parts-%E2%80%95%E3%80%8C%E8%89%AF%E3%81%84%E3%83%91%E3%83%BC%E3%83%84%E3%80%8D%E3%81%AB%E3%82%88%E3%82%8B%E3%83%99%E3%82%B9%E3%83%88%E3%83%97%E3%83%A9%E3%82%AF%E3%83%86%E3%82%A3%E3%82%B9-Douglas-Crockford/dp/4873113911/ref=sr_1_1?adgrpid=54840574273&gclid=Cj0KCQjwu-HoBRD5ARIsAPIPenflLpz28vyfIEH_lGKkiuodgmbR4eAhvjoRIYezeeegZSIAndkjABQaAvIgEALw_wcB&hvadid=338525771739&hvdev=c&hvlocphy=1009309&hvnetw=g&hvpos=1t1&hvqmt=e&hvrand=17154409248115044252&hvtargid=aud-762433167318%3Akwd-298464948360&hydadcr=27521_11564932&jp-ad-ap=0&keywords=javascript+the+good+parts&qid=1561958770&s=gateway&sr=8-1))
  - Với **constuctor** thì tên hàm sẽ viết hoa **toàn bộ** chứ cái đầu tiên
  - Với **hàm thông thường** thì sẽ là **viết thường chữ cái thứ nhất**

- Với HTML, CSS: tên của id, class sẽ như sau
  - **id** sẽ sử dụng **lower_separate**
  - **class** sẽ sử dụng **hyphen-separate**

```html
<div class="main-content" id="middle_column"></div>
```

Điều quan trọng hơn cả là đảm bảo **tính nhất quán** trong project

### 2.7. Tổng kết

Dưới đây sẽ là các gợi ý khi lựa chọn tên cho biến, hàm

- **Chọn những từ rõ nghĩa** - Thay vì **Get** thì tuỳ vào trường hợp có thể sử dụng **Fetch** hoặc **Download** để thay thế

- **Tránh những tên vô nghĩa như tmp, retval** - Nhưng việc lựa chọn những tên như trên lại hoàn toàn có thể nếu có lí do hợp lí

- **Sử dụng những tên có tính cụ thể cao, qua đó có thể truyền tải được thông tin chi tiết nhất có thể** - **CanListenOnPort** sẽ có tính cụ thể cao hơn **ServerCanStart**

- **Thêm những thông tin quan trọng vào tên biến** - Với biến có đơn vị là **ms** thì thêm **_ms** ở **hậu tố**, với các biến sau này cần escape thì thêm **raw_** vào tiền tố

- **Với các biến có scope lớn thì dùng những tên dài** - Với những biến được gọi ở nhiều scope thì nên sử dụng thêm **1-2 kí tự** để đánh dấu. Với những scopes **chỉ có vài dòng** thì nên dùng tên ngắn

- Chữ in hoa, _ cũng bao hàm ý nghĩa - Thêm dấu **_** vào **thuộc tính của class** để phân biệt với **biến local**

### Chương 3: Tên gọi tránh sự hiểu nhầm

> Key -  Luôn tự hỏi xem "Liệu cái tên này có gây ra sự hiểu nhầm về ý nghĩa hay không ?"

### 3.1. Ví dụ: filter()

Cùng xem xét đoạn code dưới đây (tương tác với dữ liệu lấy ra từ database)

```java
results = Database.all_objects.filter("year <= 2011");
```

Biến `results` sẽ bao hàm những kết quả nào (trong 2 kết quả dưới đây)?
- [year <= 2011] object
- [year > 2011] object (ngược lại với kết quả bên trên)

Điều dẫn đến sự khó hiểu ở trên là do cái tên **filter** có ý nghĩa mơ hồ. Không rõ ràng giữa việc **chọn lựa (select)** và **loại trừ** nên nó gây ra sự hiểu nhầm về mặt ý nghĩa như trên.

Nếu là **chọn lựa** thì nên là **select** còn nếu là loại trừ thì nên là **exclude**

### 3.2. Ví dụ Clip(text, length)

Cùng xét đoạn code cắt paragraph như sau:

```python
# Cắt đoạn cuối của text và thêm (...) vào đó
def Clip(text, length):
    # body
```

Với cái tên **Clip()**, có thể hiểu theo 2 nghĩa
- Xoá đi **length** kí tự từ phía cuối
- loại bỏ đi tối đa **length** kí tự

Để tránh nghi vấn cho người đọc nên chuyển tên hàm thành **Truncate(text, length)**

Ngoài ra còn tên tham số **length**, nên đặt là **max_length** thì sẽ rõ ràng hơn về ý nghĩa. Trong chương trước, cũng đã có sự đề cập đến đơn vị trong tên biến. Vì trong trường hợp này, **length** biểu thị số lượng chữ cái nên cái tên **max_chars** sẽ thích hợp hơn

### 3.3. Sử dụng min, max khi biến bao hàm giá trị giới hạn

Xét đoạn code kiểm tra điều kiện số lượng đồ trong shopping cart không vượt quá 10

```python
CART_TOO_BIG_LIMIT = 10

if shopping_cart.num_items() >= CART_TOO_BIG_LIMIT:
    Error("かーとにある商品数が多すぎる。)
```

Đoạn code trên mắc 1 lỗi cổ điển đó là lỗi **off-by-one**  (đây là lỗi liên quan tới điều kiện giới hạn). Ta có thể sửa **>=** thành **>**

Nhưng bản chất của vấn đề lại nằm ở cái tên khá mơ hồ / tối nghĩa **CART_TOO_BIG_LIMIT**. Cái tên này không nói rõ là **bao hàm giá trị biên** hay **không bao hàm giá trị biên**

> Advise: Cần làm rõ việc có bao hàm giá trị biên hay không thông qua việc thêm các tiếp đầu ngữ là max_ hoặc min_ vào tên biến

Vì thế nên ta sẽ sửa tên biến từ **CART_TOO_BIG_LIMIT** thành **MAX_ITEMS_IN_CART**

### 3.4. Sử dụng first, last khi chỉ định phạm vi giá trị

Cùng xét một ví dụ khác về **<** và **<=**

```python
print integer_range(start=2, stop=4)
```

**start** là một cái tên ổn, nhưng **stop** thì lại mơ hồ. Liệu **stop=4** có **bao hàm 4** hay **không bao hàm 4** 
Nếu bao hàm giá trị cuối cùng thì nên đặt tên là **first** và **last**

```python
set.PrintKeys(first="Bart", last="Maggie")
```

Ngoài cách gọi tên như trên, chúng ta hoàn toàn có thể sử dụng tên **min** và **max**

### 3.5. Sử dụng begin và end theo ý nghĩa bao hàm / không bao hàm


Trong lập trình **begin** sẽ được hiểu theo nghĩa là bao hàm giá trị, còn **end** sẽ là không bao hàm giá trị

Cách viết

```c++
PrintEventsInRange("OCT 16 12:00am", "OCT 17 12:00am")
```

đơn giản hơn nhiều so với

```c++
PrintEventsInRange("OCT 16 12:00am", "OCT 16 11:59:59.9999am")
```

### 3.6. Tên của biến Bool

Khi đặt tên cho biến bool hoặc hàm trả về giá trị bool thì nên đặt sao cho tên mang ý nghĩa **true**, **false**

Dưới đây là một ví dụ cho việc đặt tên không tốt

```c
bool read_password = true;
```

Bản thân từ **read** cũng mang nghĩa là **đọc**. Nên có thể hiểu theo 2 nghĩa sau đây

- Sẽ đọc password
- Đã đọc password (thể quá khứ của **read** cũng là **read**)

Ở đây, thay vì read có thể sử dụng **need_password**, **user_is_authenticated**

Với các biến bool, thì nên thêm tiếp đầu ngữ **is**, **has**, **can**, **should**
Tránh dùng những tên phủ định như **disable_ssl** mà nên sử dụng **use_ssl**

### 3.7. Phù hợp với kì vọng của người dùng

Kể cả khi dùng với một ý nghĩa khác nhưng do **định kiến** hoặc **thói quen suy nghĩ** của người dùng mà việc đặt tên cũng có thể dẫn đến sự hiểu nhầm. Những tình huống đó, ta nên **chấp nhận định kiến của người dùng** và đặt một cái tên không gây hiểu nhầm

### Ví dụ: get*()

Rất nhiều lập trình viên thường có thói quen đặt tên cho phương thức bắt đầu bằng **get** cho các phương thức **chỉ lấy về giá trị của thuộc tính**

Dưới đây là một ví dụ

```java
public class StatisticsCollector {
    public void addSample(double x) {
        // body
    }

    public double getMean() {
        // body
    }
}
```

`**getMean** ở đây là phương thức duyệt qua toàn bộ dữ liệu đã có, sau đó tính giá trị trung bình của chúng. Với lượng dữ liệu lớn thì việc tính toán như trên là rất tốn kém, những lập trình viên không nghĩ đến hiệu năng và chi phí tính toàn thì sẽ gọi hàm **getMean**

Cân nhắc về chi phí tính toán trước, ta nên đổi tên phương thức trên thành **computeMean** (cũng nên thay đổi code để giảm chi phí tính toán)

### Ví dụ: list::size()

Xét đoạn code C++ dưới đây với 1 bug khá khó để tìm thấy, đó là nguyên nhân khiến cho tốc độ của server giảm đi rõ rệt.

```c++
void ShrinkList(list<Node>& list, int max_size) {
    while (list.size() > max_size) {
        FreeNode(list.back());
        list.pop_back();
    }
}
```

Nguyên nhân gây ra bug là do **list.size()** có thời gian tính toán là **O(n)**, do không tính trước số lượng các nodes của list nên hàm **ShrinkList** trên sẽ có thời gian tính toán là **O(n2)**

Đoạn code này hoàn toàn đúng về mặt logic, chạy pass toàn bộ unit test nhưng nếu truyền vào hàm **ShrinkList** một list gồm **1 triệu nodes** thì thời gian tính toán của hàm sẽ lên đến **1 tiếng**

Vấn đề nằm ở chỗ, **list.size** tốn khá nhiều thời gian để thực thi. C++ hay các ngôn ngữ khác đều có các containers, bản thân mỗi container đều có 1 method là **size()** với thời gian thực thi nhất định

### 3.8. Ví dụ: xem xét giữa nhiều cái tên

Cùng xét ví dụ, thực thi các experiments (thử nghiệm) để test traffic cho một trang web. Dưới đây là file setting cho việc test

```json
experiment_id: 100
description: "change font size to 14pt"
traffic_fraction: 5%
```

Do test nhiều lần nên phải copy/ paste các thuộc tính ở các files setting còn lại
Nhưng để tránh việc nhiều thuộc tính / giá trị ở các file trùng nhau (file quá dài, tốn công copy / paste) chúng ta muốn ở các experiments khác cũng có thể sử dụng được các giá trị của file setting đã tồn tại (gọi là **inherit prototype pattern**). Nếu thế có thể viết như dưới đây

```json
experiment_id: 101
the_other_experiment_id_want_to_reuse: 100
[Chỉ overwrite các thông tin cần thiết]
```

Điều cần xem xét ở đây là tên **the_other_experiment_id_want_to_reuse**. Có thể kể ra 4 cái tên phù hợp
1. template
2. reuse
3. copy
4. inherit

Khi cân nhắc giữa nhiều cái tên, cần suy xét khả năng gây hiểu lầm của từng tên một

Đầu tiên là tên **template**. Đây là một cái tên khá mơ hồ, sẽ có 2 khả năng hiểu ở đây một là **Đây là template** và hai là **Sử dụng template này**. Ngoài ra đây là một từ có tính trừu tượng khá cao, dẫn đến sự hiểu nhầm rằng thử nghiệm với template này không phải là thử nghiệm thật mà là thử nghiệm mang tính trừu tượng.

Thứ hai là từ **reuse**. Đây không hẳn là một cái tên tệ, nhưng vẫn có thể gây ra sự hiểu nhầm ở chỗ **Thử nghiệm này có thể tái sử dụng ~lần**, nên đổi thành **reuse_id**. Thế nhưng có khả năng bị hiểu nhầm là **id tái sử dụng của thử nghiệm này là ~**

Tiếp theo là **copy**. Đây là một cái tên khá tốt, nhưng có thể gây hiểu nhầm ở chỗ
```json
copy: 100
```
Có thể hiểu theo 2 hướng **copy 100 lần** hoặc **đây là lần copy thứ 100**. Để thể hiện đúng mục tiêu là **tham chiếu đến các thử nghiệm khác** ta sẽ đặt tên là **copy_experiment**

Cuối cùng là**inherit**. Đây là cái tên rất quen thuộc với các lập trình viên (nó mang ý nghĩa là kế thừa). Khi chúng ta kế thừa 1 class thì toàn bộ methods, properties của class đó sẽ thuộc về class con. Thế nhưng để có sự rõ ràng thì nên đổi thành **inherit_from** hoặc **inherit_from_experiment_id**

Từ những tìm kiếm và cân nhắc trên chúng ta thấy có 2 cái tên phù hợp nhất đó là **copy_experiment** và **inherit_from_experiment_id** vì hai cái tên này khó gây ra sự hiểu nhầm và cũng rõ ràng nhất

### 3.9. Tổng kết

- Tên phù hợp nhất là cái tên không gây ra sự hiểu nhầm nào. Khi người khác đọc code của mình, họ sẽ hiểu được ngay ý đồ của mình
- Trước khi đặt tên nên có một cái nhìn đa chiều về cái tên đó, tưởng tượng xem liệu nó có gây hiểu nhầm hay không
- Với giá trị cực đại / tiểu thì tên nên có **max_**, **min_**
- Với các khoảng thì có thể là **first**, **last** - bao hàm giá trị cuối, **begin**, **end** - không bao hàm gía trị cuối
- Với giá trị bool thì nên có các tiếp đầu ngữ nhủ **is**, **has**, ...
- Cũng nên chú ý đến kì vọng của người dùng, ví dụ với hàm **get**, **size** thì nên đáp ứng kì vọng của người dùng về thời gian tính toán nhanh nhất có thể

### Chương 4: Vẻ đẹp

Một cuốn tạp chí bao hàm khá nhiều thông tin trong đó. Vậy nên việc thiết kế layout cho nó là vô cùng quan trọng. Layout ở đây có thể kể đến như: độ dài văn bản, chiều rộng, thứ tự, ...

Chương này sẽ trình bày về cách viết code sao cho dễ đọc. Bao gồm những chú ý về: khoảng trắng, cách bố trí các đoạn code, thứ tự của chúng

Cụ thể là:
- Sử dụng layout một cách nhất quán, cũng như sử dụng các patterns đã quen thuộc theo cách đọc của người dùng
- Khiến cho các đoạn code giống nhau về ý nghĩa nhìn giống nhau
- Tập hợp các đoạn code liên quan lại thành một khối

### 4.1. Tại sao code đẹp lại quan trọng

Cùng xem xét đoạn code sau

```c++
class StatsKeeper {
public:
    void Add(double d);
  private: int count;
   public:
        double Averange();
private: double minimum;
list<double>
    past_items
        ;double maximum;
};
```
Rõ ràng để hiểu được đoạn code trên sẽ mất khá nhiều thời gian, còn đoạn code đẹp hơn dưới đây thì như thế nào

```c++
class StatsKeeper {
    public:
        void Add(double d);
        double Averange();

    private:
        list<double> past_items;
        int count;

        double minimum;
        double maximum;
};
```

Rõ ràng là dễ đọc hơn rất nhiều. Phần lớn thời gian lập trình là để đọc code, nếu như có thể đọc code một cách trôi chảy thì ta cũng có thể nói đó là **code đẹp**

### 4.2. Tính nhất quán trong việc bố trí vị trí các dòng code

Ta xét class **TcpConnectionSimulator** viết bằng Java, dùng để đánh giá mức độ hoạt động của chương trình khi kết nối vào mạng tốc độ cao. Constructor của **TcpConnectionSimulator** class có 4 tham số
1. Tốc độ kết nối (Kbps)
2. Thời gian trễ trung bình (ms)
3. Thời gian trễ (ms)
4. Tỉ lệ mất gói tin (%)

Xét đoạn code dưới đây
```java
public class PerformanceTester {
    public static final TcpConnectionSimulator wifi = new TcpConnectionSimulator(
        500, /* Kbps */
        80, /* ms */
        200, /* jitter */
        1 /* packet loss % */);

    public static final TcpConnectionSimulator t3_fiber =
        new TcpConnectionSimulator(
            45000, /* Kbps */
            10, /* ms */
            0, /* jitter */
            0 /* packet loss % */);

    public static final TcpConnectionSimulator cell = new TcpConnectionSimulator(
        100, /* Kbps */
        400, /* ms */
        250, /* jitter */
        5 /* packet loss % */);
}
```

Do convention code (80 kí tự tối đa 1 dòng) nên ở biến **t3_fiber** có sự khác biệt so với các biến còn lại (điều này vi phạm quy tắc - **các phần có ý nghĩa giống nhau phải tương tự nhau**). Ta sẽ sửa lại như sau

```java
public class PerformanceTester {
    public static final TcpConnectionSimulator wifi =
        new TcpConnectionSimulator(
            500, /* Kbps */
            80, /* ms */
            200, /* jitter */
            1 /* packet loss % */);

    public static final TcpConnectionSimulator t3_fiber =
        new TcpConnectionSimulator(
            45000, /* Kbps */
            10, /* ms */
            0, /* jitter */
            0 /* packet loss % */);

    public static final TcpConnectionSimulator cell =
        new TcpConnectionSimulator(
            100, /* Kbps */
            400, /* ms */
            250, /* jitter */
            5 /* packet loss % */);
```

Đoạn code trên có tính thống nhất và khá dễ nhìn nhưng lại quá dài và comments lặp lại 3 lần. Nên có thể viết ngắn hơn như sau

```java
public class PerformanceTester {
    // TcpConnectionSimulator(throughput, latency, jitter, packet_loss)
    //                           [Kbps]     [ms]    [ms]    [percent]

    public static final TcpConnectionSimulator wifi =
        new TcpConnectionSimulator(500, 80, 200, 1);

    
    public static final TcpConnectionSimulator t3_fiber =
        new TcpConnectionSimulator(45000, 10, 0, 0);

    
    public static final TcpConnectionSimulator cell =
        new TcpConnectionSimulator(100, 400, 250, 5);
}
```

Ở đoạn code trên, ta đã di chuyển comment lên đầu, đồng thời toàn bộ các tham số đều được xếp theo thứ tự thành một hàng duy nhất. Dễ nhìn hơn rất nhiều

### 4.3. Sử dụng căn lề cho method

Xét đoạn code dưới đây kiểm tra chức năng của hàm **ExpandFullName** như sau

```c++
// [Doug Adams] - là 1 dạng partial_name, hàm sẽ có chức năng biến đổi nó thành [Mr. Douglas Adams]
// Nếu không thực hiện được thì đưa ra error

string ExpandFullName(DatabaseConnection dc, string partial_name, string* error);

DatabaseConnection database_connection;
string error;

assert(ExpandFullName(database_connection, "Doug Adams", &error) == "Mr. Douglas Adams");
assert(error == "");

assert(ExpandFullName(database_connection, "Jake Brown", &error) == "Mr. Jacob Brown III");
assert(error == "");

assert(ExpandFullName(database_connection, "No Such Guy", &error) == "");
assert(error == "no match found");

assert(ExpandFullName(database_connection, "John", &error) == "");
assert(error == "more than one result");
```

Thoạt nhìn qua đoạn code phía trên khá khó coi, chưa kể còn dài và có nhiều chỗ lặp lại, thiếu đi 1 pattern nhất quán. Để cải thiện đoạn code trên mà vẫn giữ nguyên ý nghĩa của nó, ta cần sử dụng **helper parameter**

```c++
CheckFullName("Doug Adams", "Mr. Douglas Adams", "");
CheckFullName(" Jake Brown ", "Mr. Jake Brown III", "");
CheckFullName("No Such Guy", "", "no match found");
CheckFullName("John", "", "more than one result");
```

Ta có thể thấy 4 test case với các tham số khác nhau. Mọi công việc xử lí đều được đưa vào hàm **CheckFullName**


```c++
void CheckFullName(string partial_name,
                   string expected,
                   string expected_error) {
    // database_connection giờ là thuộc tính của class
    string error;
    string full_name = ExpandFullName(database_connection, partial_name, &error);
    assert(error == expected_error);
    assert(full_name == expected_full_name);
}
```

Nhờ việc thay đổi code như trên, ngoài việc giải quyết được vấn đề về code đẹp, ta còn giải quyết được một vài vấn đề như sau
- Code đã ngắn đi, đơn giản hơn do ta đã xoá đi 1 lượng đáng kể code thừa
- Những phần quan trọng của test case là **tên** và **error** đã dễ nhìn hơn, trước đây chúng được bao bởi **database_connection** và **error** nên khá khó **nuốt trôi**
- Việc thêm test cũng đơn giản hơn nhiều

Qua đây ta rút ra được bài học

> Cải thiện "bề ngoài code" không chỉ giúp code dễ đọc hơn mà còn cải thiện được cấu trúc của code

### 4.4. Căn lề dọc

Việc căn lề dọc cũng khiến code trở nên dễ đọc hơn. Trong phần trước, ta có thể căn dọc các tham số của các **test cases** bằng những khoảng trắng như sau

```c++
CheckFullName("Doug Adams"  , "Mr. Douglas Adams" , "");
CheckFullName(" Jake Brown ", "Mr. Jake Brown III", "");
CheckFullName("No Such Guy" , ""                  , "no match found");
CheckFullName("John"        , ""                  , "more than one result");
```

Ví dụ dưới đây sẽ định nghĩa nhiều biến

```javascript
details  = request.POST.get('details');
location = request.POST.get('location');
phone    = equest.POST.get('phone');
email    = request.POST.get('email');
url      = request.POST.get('url');
```

Có thể nhận ra dễ dàng ở dòng thứ 3 **request** bị viết nhầm thành **equest**, nhờ có việc căn lề mà ta có thể dễ dàng tìm ra lỗi.

#### Liệu có nên căn lề ?

Ta có thể thấy việc căn lề giúp đảm bảo tính thị giác qua đó giúp **những đoạn code có vai trò giống nhau sẽ giống nhau**

Nhưng có những lập trình viên không thích việc căn lề. Họ có lí do như sau

> Chỉ thay đổi 1 dòng mà các dòng khác cũng phải thay đổi theo để đảm bảo quy tắc thì rất phí thời gian

### 4.5. Sắp xếp một cách nhất quán và có nghĩa

Việc sắp xếp thứ tự code thực ra không ảnh hưởng quá nhiều đến độ chính xác của code. Ở ví dụ dưới đây, khi thay đổi thứ tự 5 dòng định nghĩa thì cũng không sao cả

```javascript
details  = request.POST.get('details');
location = request.POST.get('location');
phone    = request.POST.get('phone');
email    = request.POST.get('email');
url      = request.POST.get('url');
```

Tuy nhiên không nên sắp xếp ngẫu nhiên mà nên sắp xếp theo một ý nghĩa nào đó. Ví dụ như
- Sắp xếp theo đúng thứ tự các trường <input> của form HTML
- Sắp xếp theo mức độ quan trọng giảm dần
- Sắp xếp theo thứ tự alphabet

Dù chọn thứ tự nào đi nữa thì trong 1 series code thì thứ tự này nên được bảo toàn, nếu thay đổi thì sẽ gây ra sự khó hiểu

```ruby
if details:  rec.details  = details
if phone:    rec.phone    = phone   # tại sao phone lại ở đây thay vì location
if email:    rec.email    = email
if url:      rec.url      = url
if location: rec.location = location # tại sao location lại bị cho xuống đây
```

### 4.6. Viết các định nghĩa thành block

Não người là một khối thống nhất. Nên để nắm bắt được cấu trúc của code nhanh hơn ta nên tổ chức code theo **đơn vị** như thế này

Xét đoạn code C++ viết cho front end phía server như sau

```c++
class FrontEndServer {
    public:
        FrontEndServer();
        void ViewProfile(HttpRequest* request);
        void OpenDatabase(string location, string user);
        void SaveProfile(HttpRequest* request);
        string ExtractQueryParam(HttpRequest* request, string param);
        void ReplyOk(HttpRequest* request, string html);
        void FindFriends(HttpRequest* request);
        void ReplyNotFound(HttpRequest* request, string error);
        void CloseDatabase(string location);
        ~FrontEndServer();
}
```

Đoạn code trên không hẳn là tồi nhưng việc viết tất cả methods vào một block duy nhất như vậy sẽ khiến người đọc khó nắm bắt cấu trúc các methods hơn. Thay vào đó ta sẽ chia các methods theo các nhóm dựa theo logic của methods. Ví dụ như sau

```c++
class FrontEndServer {
    public:
        FrontEndServer();
        ~FrontEndServer();

        // Handler
        void ViewProfile(HttpRequest* request);
        void SaveProfile(HttpRequest* request);
        void FindFriends(HttpRequest* request);
        
        // Request and Reply Utility
        string ExtractQueryParam(HttpRequest* request, string param);
        void ReplyOk(HttpRequest* request, string html);
        void ReplyNotFound(HttpRequest* request, string error);
        
        // Database helper
        void OpenDatabase(string location, string user);
        void CloseDatabase(string location);
}
```

Code đã trở nên dễ đọc hơn rất nhiều. Thoạt qua ta có thể nắm rõ cấu trúc chung của code. Sau đó muốn biết chi tiết hơn thì cũng có thể đọc với một thời gian ngắn

### 4.7. Chia code thành các đoạn

Liên tưởng một chút đến chuyện viết văn. Việc chia đoạn văn có thể tóm gọn như sau

- Những phần có tư tưởng giống nhau sẽ được nhóm lại với nhau
- Chia đoạn để cải thiện tính thị giác, giúp người đọc không bị loạn và đọc dễ hơn
- Có thể di chuyển, chuyển đổi các đoạn văn cho nhau để phù hợp với nội dung

Viết code cũng vậy, cũng cần chia đoạn. Ví dụ như đoạn code dưới đây, sẽ chẳng có ai muốn đọc nó cả

```python
# import user email and after that collation to system 's user
# Finally, display users whose are not friends
def suggest_new_friends(user, email_password):
    friends = user.friends()
    friend_emails = set(f.email for f in friends)
    contacts = import_contacts(user.email, email_password)
    contact_emails = set(c.email for c in contacts)
    non_friend_emails = contact_emails - friend_emails
    suggested_friends = User.objects.select(email__in=non_friend_emails)
    display['user'] = user
    display['friends'] = friends
    display['suggested_friends'] = suggested_friends
    return render("suggested_friends", display)
```

Nhìn qua sẽ thấy rất khó hiểu, nhưng nếu chia đoạn cho code thì sẽ tốt hơn

```python
def suggest_new_friends(user, email_password):
    # get mail of user's friends
    friends = user.friends()
    friend_emails = set(f.email for f in friends)
    
    # import all email addresses from user's mail account
    contacts = import_contacts(user.email, email_password)
    contact_emails = set(c.email for c in contacts)

    # find users whose not friend
    non_friend_emails = contact_emails - friend_emails
    suggested_friends = User.objects.select(email__in=non_friend_emails)
    
    # display it on page
    display['user'] = user
    display['friends'] = friends
    display['suggested_friends'] = suggested_friends
    
    return render("suggested_friends", display)
```

Việc chia đoạn và thêm comment cho từng đoạn giúp code dễ nhìn hơn rất nhiều. Tương tự như viết văn, ta cũng có khá nhiều cách để chia đoạn code

### 4.8. Tính nhất quán và sở thích cá nhân

Cuối cùng chúng ta sẽ đề cập đến những trường hợp viết code theo sở thích cá nhân. Ví dụ như việc đặt dấu { ở đâu khi định nghĩa class

```java
class Logger {
    // body
}

class Logger
{
    // body
}
```

Việc lựa chọn style code nào là tuỳ vào lập trình viên, nhưng điều quan trọng ở đây là tính nhất quán trong style code, tránh tình trạng mỗi chỗ một kiểu.

> Key - Style thống nhất quan trọng hơn style chính xác

### 4.9. Tổng kết

Ai cũng thích nhìn code đẹp cả. Việc viết code có cấu trúc, ý nghĩa, thống nhất sẽ giúp việc đọc code dễ và nhanh hơn. Dưới đây là một vài tổng kết

- Với các blocks thực hiện cùng một nhiệm vụ thì nên viết chúng sao cho chúng có sự tương đồng
- Việc căn lề code cũng sẽ giúp nắm bắt cấu trúc code dễ dàng hơn
- Nếu đã sắp xếp theo thứ tự A - B - C thì nên giữ thứ tự này ở những chỗ khác. Nên chọn những thứ tự có ý nghĩa và tuân thủ theo thứ tự đó ở mọi chỗ
- Sử dụng những dòng trống để phân chia đoạn code lớn thành các đoạn code nhỏ theo ý nghĩa logic

## Chương 5: Biết được khi nào nên comment code

Chúng ta vẫn thường nghĩ, comment là để giải thích cách vận hành của code. Nhưng đó chỉ là một phần mục đích của việc comment

> Key - Mục tiêu của comment là để truyền tải ý đồ của người viết code tới người đọc code

Khi viết code, trong đầu chúng ta có rất nhiều ý tưởng và thông tin, thế nhưng những gì người đọc code thấy được chỉ là những dòng code trước mắt mà thôi. 

Chương này sẽ đưa ra các ví dụ về việc khi nào nên đưa ra các thông tin, ý tưởng có trong đầu. Thay vì đề cập đến những khái niệm về comment hay được nói tới thì phần này sẽ trình bày về những phần như sau

- Biết được khi nào **không nên** comment code
- Truyền tải được suy nghĩ của mình thông qua code
- Đứng trên phương diện của người đọc để biết được code của mình cần những gì

### 5.1. Không nên comment code

Việc đọc comment đôi khi cũng sẽ ảnh hưởng đến thời gian đọc code. Có những comment vô nghĩa nhưng cũng có những comment có ý nghĩa, vậy sự khác biệt giữa chúng là gì. Ta cùng xem xét ví dụ sau

```c++
// Define class Account
class Account {
    public:
        // constructor
        Account();

        // setting new value for profit
        void SetProfit(double profit);

        // return profit from this Account
        double GetProfit();
};
```

> Key - Không viết comment cho những đoạn code có thể đọc hiểu ngay lập tức

