# 확장구문

## 1. 표
표는 하나의 헤더 행과 하나의 구분 행, 0개 이상의 데이터 행으로 구성됩니다. 각 행은 파이프(|)로 구분된 임의의 텍스트를 포함하는 셀로 구성됩니다. 읽기의 명확성을 위해 선행 및 후행 파이프도 권장됩니다. 구분 행의 셀에는 빼기기호(-)와 선택적으로 콜론(:)만 들어갑니다. 선행 콜론만 쓰면 왼쪽정렬, 후행 콜론만 쓰면 오른쪽 정렬, 둘 다 쓰면 가운데 정렬이 됩니다.

    | Command | Description |
    | --- | --- |
    | git status | List all new or modified files |
    | git diff | Show file differences that haven't been staged |

>| Command | Description |
>| --- | --- |
>| git status | List all new or modified files |
>| git diff | Show file differences that haven't been staged |

표의 범위는 빈 줄이나 다른 블록 수준 요소의 시작에서 끝이 납니다.

    | abc | def |
    | --- | --- |
    | bar | baz |
    > bar
    
    | abc | def |
    | --- | --- |
    | bar | baz |
    bar
    
    bar

>| abc | def |
>| --- | --- |
>| bar | baz |
>> bar
>
>| abc | def |
>| --- | --- |
>| bar | baz |
>bar
>
>bar

헤더 행과 구분 행은 셀의 수가 같아야 합니다. 그렇지 않으면 표로 인식되지 않습니다.

    | abc | def |
    | --- |
    | bar |

>| abc | def |
>| --- |
>| bar |

헤더 행보다 셀 수가 적으면 빈 셀이 삽입되며, 헤더 행보다 셀 수가 많으면 초과된 부분은 무시됩니다.

    | abc | def |
    | --- | --- |
    | bar |
    | bar | baz | boo |

>| abc | def |
>| --- | --- |
>| bar |
>| bar | baz | boo |

## 2. 작업 목록
작업 목록을 사용하면 확인란이있는 항목 목록을 만들 수 있습니다. 작업 목록을 지원하는 Markdown 응용 프로그램에서는 콘텐츠 옆에 확인란이 표시됩니다. 작업 목록을 만들려면 작업 목록 항목 앞에 대시(-) 및 공백이있는 대괄호([ ])를 추가합니다. 확인란을 체크하려면 대괄호 사이에 x 기호를 추가합니다([x]).

    - [x] Write the press release
    - [ ] Update the website
    - [ ] Contact the media

>- [x] Write the press release
>- [ ] Update the website
>- [ ] Contact the media

작업 목록은 중첩될 수 있습니다.

    - [x] foo
        - [ ] bar
        - [x] baz
    - [ ] bim

>- [x] foo
>   - [ ] bar
>   - [x] baz
>- [ ] bim

## 3. 취소선
단어의 가운데에 수평선을 넣어 취소할 수 있습니다. 단어를 취소하려면 단어 앞뒤에 두 개의 물결 기호(~~)를 사용합니다.

    ~~The world is flat.~~ We now know that the world is round.

>~~The world is flat.~~ We now know that the world is round.

## 4. 자동 링크

www.commonmark.org

Visit www.commonmark.org/help for more information.

Visit www.commonmark.org.

Visit www.commonmark.org/a.b.

www.google.com/search?q=Markup+(business)

www.google.com/search?q=Markup+(business)))

(www.google.com/search?q=Markup+(business))

(www.google.com/search?q=Markup+(business)

www.google.com/search?q=(business))+ok

www.google.com/search?q=commonmark&hl=en

www.google.com/search?q=commonmark&hl;

www.commonmark.org/he<lp

http://commonmark.org

(Visit https://encrypted.google.com/search?q=Markup+(business))

foo@bar.baz
