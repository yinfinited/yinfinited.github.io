


참고: https://nolboo.kim/blog/2015/08/18/linux-users-groups/

리눅스 사용하면서 가장 골치 아픈 권한에 대해 정리한다.

## Permission

권한은 3가지 심볼로 정해지는데, 디렉토리에 대한 것과 파일에 대한 것이 의미가 다르다.

|      | file | directory      |
| ---- | ---- | -------------- |
| r    | 읽기 | 파일 목록 보기 |
| w    | 쓰기 | 파일 추가 삭제 |
| x    | 실행 | 디렉토리 열기  |

권한은 보통 아래와 같이 표시된다.

```
rwxr-xr-x
```

위치에 따라 의미는 아래와 같다.

```
{owner}{group}{all}
```

따라서 위에 표시한 것은 아래 의미가 된다.

- `rwx` for owner
- `r-x` for group
- `r-x` for all

변경하는 방법은 `chmod` 를 이용하는 것이다.

```
chmod {permission} {filename}
```

권한 값을 주는 방법은 숫자로 주는 방법이 있고 문자로 주는 방법이 있다.

```
r = 4
w = 2
x = 1
```

따라서 아래와 같다.

```
rwx = 7
rw- = 6
r-x = 5
r-- = 4
-wx = 3
-w- = 2
--x = 1
```

위 숫자를 owner, group, all 에 대해서 주면 된다.

하위디렉토리 모두를 변경할 때는 `chomd -R` 을 사용한다.

```
chmod -R 777 {dir}
```

