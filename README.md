# 확장구문

## 0. 목차
1. 표
2. 작업 목록
3. 취소선
4. 자동 링크
5. 허용되지 않는 HTML

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
대괄호를 사용하지 않았더라도 자동으로 URL을 링크로 변환합니다. 자동 링크는 줄의 시작, 공백 후, 또는 *, _, ~, ( 와 같은 구분 문자 다음에 와야 인식됩니다.

`http://`, `https://`, `www.` 다음에 유효한 도메인이 붙으면 이 또한 자동 링크로 인식됩니다. 유효한 도메인은 마침표(.)로 부분이 나뉘며, 영숫자, 밑줄 문자(_), 빼기 기호(-)들로 구성됩니다. 최소한 하나의 마침표가 있어야 하며, 마지막 두 부분에는 밑줄 문자가 없어야 합니다.

    www.commonmark.org

>www.commonmark.org

유효한 도메인 뒤에 0개 이상의, 공백이 아니면서 <가 아닌 문자가 올 수 있습니다.

    Visit www.commonmark.org/help for more information.

>Visit www.commonmark.org/help for more information.

후행 구두점(특히 ?, !, ., ,, ;, *, _, -, ~)은 자동 링크에 포함되지 않습니다.

    Visit www.commonmark.org/a.b.

>Visit www.commonmark.org/a.b.

자동 링크가 )로 끝났면, 자동 링크에 괄호가 몇 개 있는지 확인을 하여, 닫힌 괄호가 열린 괄호보다 많으면 마지막 닫힌 괄호는 자동 링크에 포함하지 않습니다.
    
    www.google.com/search?q=Markup+(business)
    
    www.google.com/search?q=Markup+(business)))
    
    (www.google.com/search?q=Markup+(business))
    
    (www.google.com/search?q=Markup+(business)

>www.google.com/search?q=Markup+(business)
>
>www.google.com/search?q=Markup+(business)))
>
>(www.google.com/search?q=Markup+(business))
>
>(www.google.com/search?q=Markup+(business)

세미콜론(;)이 자동링크 끝에 오고, 선행하는 텍스트가 &와 1개 이상의 영숫자이면, 이는 자동 링크에서 제외됩니다.

    www.google.com/search?q=commonmark&hl;

>www.google.com/search?q=commonmark&hl;

<가 오면 바로 링크가 끝납니다.

    www.commonmark.org/he<lp

>www.commonmark.org/he<lp

### 확장된 이메일 자동 링크
이메일도 자동으로 링크로 인식됩니다. 이메일은 형식을 만족해야 합니다.

- 하나 이상의 문자. 영숫자 또는 ., -, _, + 이어야함
- @ 기호 하나
- 마침표(.)로 나뉘어진 하나 이상의 문자. 영숫자 또는 -, _이어야함. 마침표는 하나 이상 있어야함. 마지막 문자는 -나 _가 아니어야 함.

	foo@bar.baz
	
	hello@mail+xyz.example isn't valid, but hello+xyz@mail.example is.

>foo@bar.baz
>
>hello@mail+xyz.example isn't valid, but hello+xyz@mail.example is.

-, _, . 중에서 .만 이메일 뒤에 올 수 있습니다. 이 .은 이메일에 포함되지 않습니다.

    a.b-c_d@a.b
    
    a.b-c_d@a.b.
    
    a.b-c_d@a.b-
    
    a.b-c_d@a.b_

>a.b-c_d@a.b
>
>a.b-c_d@a.b.
>
>a.b-c_d@a.b-
>
>a.b-c_d@a.b_

## 5. 허용되지 않는 HTML
HTML 출력을 할 때 다음 HTML 태그들은 필터링 됩니다.

- <title>
- <textarea>
- <style>
- <xmp>
- <iframe>
- <noembed>
- <noframes>
- <script>
- <plaintext>
 
필터링은 `<`을 `&lt;`로 대체하면서 이루어집니다.

    <strong> <title> <style> <em>
    
    <blockquote>
        <xmp> is disallowed.  <XMP> is also disallowed.
    </blockquote>

><strong> <title> <style> <em>
>
><blockquote>
>   <xmp> is disallowed.  <XMP> is also disallowed.
></blockquote>
