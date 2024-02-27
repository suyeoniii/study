## Write File (touch, echo, cat, vi/vim, nano)

### touch

```sh
touch filename.txt
```

- 빈 파일을 생성함
- 같은 이름의 파일이 있으면, 파일의 timestamp를 업데이트
- 파일 내용은 수정하지 않음

### echo

```sh
echo "Hello World!" > mytext.txt
```

- echo는 터미널에 출력할 때 사용
- `>`를 사용하면 파일에 내용을 넣을 수 있음

### cat

```sh
cat > newfile.txt
This is a new file
Ctrl+D
```

- 파일의 내용을 concatenate 하거나, 터미널에 표시할 때 사용
- 파일을 저장할 수도 있음

### vi/vim

```sh
vi newfile.txt
```

- 파일 생성에 효과적인 텍스트 에디터
- vi 또는 vim으로 사용가능
- 파일 작성 완료 후 ESC + :wq 로 저장

### nano

```sh
nano newfile.txt
```

- vi 에디터보다 덜 복잡한 에디터
- 일반적인 텍스트 파일처럼 수정가능함
- (ctrl + x) + y + enter

#### 참고자료

[link](https://medium.com/@akshaykotawar86/difference-between-o-d2697a1f48f4#id_token=eyJhbGciOiJSUzI1NiIsImtpZCI6IjU1YzE4OGE4MzU0NmZjMTg4ZTUxNTc2YmE3MjgzNmUwNjAwZThiNzMiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJodHRwczovL2FjY291bnRzLmdvb2dsZS5jb20iLCJhenAiOiIyMTYyOTYwMzU4MzQtazFrNnFlMDYwczJ0cDJhMmphbTRsamRjbXMwMHN0dGcuYXBwcy5nb29nbGV1c2VyY29udGVudC5jb20iLCJhdWQiOiIyMTYyOTYwMzU4MzQtazFrNnFlMDYwczJ0cDJhMmphbTRsamRjbXMwMHN0dGcuYXBwcy5nb29nbGV1c2VyY29udGVudC5jb20iLCJzdWIiOiIxMTQ1NDU0OTQwOTAxMjUzODkzNzUiLCJlbWFpbCI6InNzeTQyMzBAZ21haWwuY29tIiwiZW1haWxfdmVyaWZpZWQiOnRydWUsIm5iZiI6MTcwODk1MzM1OCwibmFtZSI6IlN1eWVvbiBTb24iLCJwaWN0dXJlIjoiaHR0cHM6Ly9saDMuZ29vZ2xldXNlcmNvbnRlbnQuY29tL2EvQUNnOG9jSTJILXYwNjhhNlhsck9sNXlUY09PVnBQaTZEUk8tdGVBZ3N5WVFXNjJvSnZVPXM5Ni1jIiwiZ2l2ZW5fbmFtZSI6IlN1eWVvbiIsImZhbWlseV9uYW1lIjoiU29uIiwibG9jYWxlIjoia28iLCJpYXQiOjE3MDg5NTM2NTgsImV4cCI6MTcwODk1NzI1OCwianRpIjoiN2JjMTNlODhiZjZhNWYzYzgwNWQyNjFjMzRmN2YwOWU5OGM0NGQ2MyJ9.OO1IeRUSXP-Ayp11UrhJfV2NMcQUxTVxiNEllDJePukT9JmHwCDuMkc3z8hpLc-CgdfXckddN-0bWx4xuLSZfL0VyjeiF9XYEPgZFXSaQa4VoVhJGZl8EabDCJaYoZjA3A-66B2IRNrL_pubmwUBPHDmjDAYFjHMEFvrJBMBaEw7cBk_RBC-_L43VOWf1bvfHoRScUtHn5PfkSVJtRyQ8C9aKh3VIXOfrqtCaonSAzhnjVSm0-IvSgXT4rcvyEB74y0I2A80sDEqymy4BzI0rKTkCgfO5ABZMi1FUXJXP_3FcYsDqJa3D5le2ShJOLVo2a2tLXiu9G_PHDY-EHwr4g)
