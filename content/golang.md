title: Golang cơ bản (Giới thiệu và cài đặt)
slug: golang 
category: Programing
Date: 2019-03-15

![Image](images/golang/golang.png)


# Tổng quan 
- Golang, còn được gọi là Go, là một ngôn ngữ lập trình biên dịch hướng hệ thống (systems-oriented) mã nguồn mở (open source) sử dụng cú pháp cấp cao tương tự như ngôn ngữ kịch bản được thiết kế và phát triển bởi Google vào năm 2007 để giúp các nhà phát triển của Google xây dựng các hệ thống cho lượng người dùng cực lớn. Nó được kỳ vọng sẽ giúp ngành công nghiệp phần mềm khai thác nền tảng đa lõi của bộ vi xử lý và hoạt động đa nhiệm tốt hơn. 

- Go có trang chủ tại địa chỉ [golang](https://golang.org/) 

## Ý nghĩa tên gọi
- Go được xuất phát từ tên công ty Google. Hơn nữa, Go trong tiếng Anh có nghĩa là đi, tiến lên, mang một ý nghĩa tiến đến tầm cao mới.

# Cài đặt
## Cài đặt Go 
- Golang hỗ trợ cả ba nền tảng Mac, Windows, Linux. Trong bài viết này mình sẽ hướng dẫn các bạn cài đặt Golang trên nền tảng linux (Ubuntu 18.04)

- Thông thường, trước khi cài đặt một phần mềm trên Ubuntu thì bước đầu tiên cần làm đó là cập nhật các gói package đang được cài đặt trên hệ thống. Mở chương trình cửa sổ dòng lệnh terminal trên Ubuntu và chạy câu lệnh dưới đây:
```
$ sudo apt-get update
$ sudo apt-get -y upgrade
```
- Sau khi kết thúc việc cập nhật bạn truy cập vào [link](https://golang.org/dl/) này để chọn version tương ứng với phiên bản hệ điều hành, ví dụ OS của mình là linux, với kiến trúc AMD 64 bit, mình chọn được version và tiến hành tải về  [link](https://dl.google.com/go/go1.12.1.linux-amd64.tar.gz) và giải nén, bạn có thể tải về và giải nén trực tiếp hoặc thông qua dòng lệnh như sau:
```
$ wget https://dl.google.com/go/go1.12.1.linux-amd64.tar.gz
$ sudo tar -xzvf go1.12.linux-amd64.tar.gz
```
- Sau khi giải nén xong bạn có thể di chuyển nó về thư mục **/usr/local**
```
$ sudo mv go /usr/local
```

## Thiết lập đường dẫn 
- Trong bước này, mình sẽ thiết lập một số đường dẫn mà Go cần. Các đường dẫn trong bước này đều liên quan đến vị trí cài đặt Go của mình trong **/usr/local**, nếu bạn để tệp ở vị trí khác, hãy sửa đổi các lệnh để khớp với vị trí mới của bạn.

- Go có các biến môi trường như sau:
```
- GOROOT: Nơi mà các packages Go sẽ được cài đặt (trỏ về thư mục /usr/local/go lúc nãy mình vừa move, hoặc 1 thư mục bất kì mà bạn vừa move đến).
- GOPATH: Nơi mà các thư viện được kéo về, nó là workspace (không gian làm việc) của bạn.
```
- Bạn có thể thiết lập các biến môi trường này bằng cách sửa lại file .profile trong thư mục root ubuntu như sau:
```
$ sudo nano .profile
```
- Ở cuối tập tin, thêm dòng này:
```
export GOPATH=~/go
export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin
```
- Lưu lại và đóng tệp, chạy lệnh **source .profile** để các thay đổi trên file có tác dụng mà không phải restart terminal.
 
## Kiểm tra cài đặt Go
- Bây giờ Go đã được cài đặt và các đường dẫn đã được thiết lập cho máy của bạn, bạn có thể kiểm tra để đảm bảo rằng Go hoạt động như mong đợi:
```
$ go version
go version go1.12 linux/amd64
```
- Bạn có thể gõ một số lệnh khác, **go env** để check các biến môi trường của Go.

- Tạo một thư mục mới cho workspace Go của bạn:
```
$ mkdir go
$ cd go
$ mkdir src pkg bin
```

## Viết chương trình đầu tiên
- Tạo folder chứa code chương trình Go đầu tiên của bạn bằng cách:
```
$ cd /go/src
$ mkdir -p learn_go 
$ cd learn_go
$ mkdir hello
$ cd hello
$ gedit hello.go
```
- Viết chương trình đầu tiên của bạn gửi lời chào tới thế giới:
```
package main
import "fmt"
func main() {
    fmt.Printf("hello, world\n")
}
```
## Chạy một chương trình Go:
- Sử dụng lệnh **go run** bạn sẽ thấy output là **hello, world**
```
$ cd /go/src/learn_go/hello
$ ls
$ hello.go
$ go run hello.go
hello, world
```
- Sử dụng lệnh **go install**, khi bạn gõ lệnh **go install hello**, go tool sẽ tìm đến một package tên **hello** trong workspace go của bạn, sau đó tạo ra một file chứa mã nhị phân tên hello (hello.exe trên windows) tại thư mục **/bin** trong workspace. Cấu trúc thư mục sau khi chạy lệnh **go install hello** sẽ như dưới đây:
```
.
├── bin
│   └── hello
├── pkg
└── src
    └── learn_go
        └── hello
            └── hello.go
```
- Mở terminal và gõ ```$ hello``` bạn sẽ thấy output là **hello, world**.

# Kết luận
- Vậy là mình đã giới thiệu cho các bạn một ngôn ngữ mới thú vị, mong rằng bài viết này sẽ giúp ích cho những bạn mới bắt đầu làm quen với ngôn ngữ lập trình Go bớt đi những bỡ ngỡ từ đó viết được những chương trình lớn hơn cho riêng mình sau này. Cảm ơn các bạn đã quan tâm.

# Tài liệu tham khảo
- [Go Setup on Linux](https://www.youtube.com/watch?v=R-cA6J3IniI)
- [wikipedia](https://vi.wikipedia.org/wiki/Go_(ng%C3%B4n_ng%E1%BB%AF_l%E1%BA%ADp_tr%C3%ACnh))











