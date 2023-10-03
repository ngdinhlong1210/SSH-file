# Cách thêm nhiều tài khoản git trên cùng một máy

## Bước 1: Tạo key rsa từ github

- Đầu tiên, ta vào github cần generate key. Vào **setting > SSH & GPG keys > generate key >**

Ta generate key theo document tại [đây](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

```
    ssh-keygen -t rsa -C "your_email@example.com"
```


Sau khi dán đoạn code trên vào terminal, ta tiếp tục cài đặt path và password cho ssh

## Bước 2: Add key public RSA 

- Ta mở file **(RSA).pub** và copy và thêm vào SSH Keys trên github

## Bước 3: thêm file config vào folder .ssh

- Sau khi thêm key public trên github, ta thêm 1 file config trong folder **.ssh**

```
Host github_dev
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_dev 
Host github_ptit
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa_GS
```

- Giải thích:
    -  **IdentityFile** là file ssh định nghĩa public key-kết hợp với ssh key đã add trên github để clone private project về
    - **Host** là Tên ssh github định danh khi clone về

## Bước 4: Clone project

- Sau khi đã làm xong các bước ở trên, ta chỉ việc clone một project về thông qua ssh

```
    git@github.com:ngdinhlong1210/Ghi-chep-ckhoan.git
```

- Ở đây ta chú ý, vì để định danh ssh user khi clone về ta sẽ sửa **github.com** thành tên Host đã được định nghĩa ở trên

```
    git@github_dev:ngdinhlong1210/Ghi-chep-ckhoan.git
```
