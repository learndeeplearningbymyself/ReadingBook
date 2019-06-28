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