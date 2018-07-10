참고: https://nolboo.kim/blog/2015/08/18/linux-users-groups/

리눅스 사용자 관리에 대해 알아본다.

## basic

사용자를 추가할 하는 방법은 아래와 같다.

```
useradd {username}
```

옵션으로 홈디렉토리, 만료시간, 기본쉘 등을 정의할 수 있지만 사용할 일은 거의 없다.

비밀번호를 변경해야한다.

```
passwd
```

`root` 인 경우 다른 사용자의 비밀번호를 바꿀 수 있다.

```
passwd {username}
```

삭제하는 방법은 아래와 같다.

```
userdel {username}
userdel -r {username}  // remove home directory
```

## sudo

`sudo` 는 `root` 사용자의 권한을 일부 사용할 수 있도록 하는 명령이다. 기본으로 항상 설치되는 것은 아니다.

`sudo` 명령은 sudoers 라는 파일을 참조하여 해당 사용자가 어느 권한까지 `sudo` 를 이용해  빌려 쓸 수 있는지 알아낸다.

`sudoers` 파일 편집은 신중하게 수행되어야 하므로 별도 편집기가 제공된다.

```
visudo
```

이제 각 사용자별로 sudo 접근을 사용할 수 있는지 여부를 명시한다.

```
root    ALL=(ALL:ALL) ALL
cjones  ALL=(ALL:ALL) ALL
kbrown  ALL=(ALL:ALL) ALL
lmartin ALL=(ALL:ALL) ALL
```

## group

`/etc/group` 파일에 기록된 정보로 사용자는 적어도 어느 한 그룹에 속하게 된다. 당연히 여러 개 그룹에 속할 수 있다.

```
$ cat /etc/group
root:x:0:
sys:x:3:
tty:x:5:
mem:x:8:
```

위 파일 내용은 크게 4부분으로 나눌 수 있다.

1. group name - 그룹명을 나타낸다.
1. password - `x` 는 사용하지 않음
1. group id - 숫자로 표현된 id
1. group list - 해당 그룹에 속한 사용자 목록. 콤마로 구분된 username 이 들어간다.


### 그룹 추가/삭제

아래 명령은 새 그룹을 만든다.

```
newgrp {groupname}
```

파일은 파일을 만든 사용자와 그 사용자의 디폴트 그룹에 의해 소유된다.

```
chown {username}:{groupname} {filename}
```


