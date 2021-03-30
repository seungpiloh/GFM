# GFM Practice
## Extended Syntax
### 1. 테이블(Tables)
#### 1.1 특징
- GFM은 추가적인 리프 블록 유형을 사용할 수 있는 테이블을 활성화합니다.  

- 테이블은 행과 열이 있는 데이터 배열로, 단일 헤더 행, 데이터로부터 헤더를 구분하는 구분자 행, 0개 이상의 데이터 행으로 구성됩니다.

- 각 행은 임의 텍스트를 포함하는 셀로 구성되며, 이 셀에서는 inline이 분석되고 파이프( | )로 구분됩니다. 이때 가독성을 위해 선행 파이프와 후행 파이프가 권장됩니다. 
 
- 파이프와 셀 내용 사이의 공백은 잘리게 되며 테이블에 블록 수준의 요소들을 삽입할 수 없습니다.
 
- 구분 기호 행은 하이픈(-)과 선택적인 선행 또는 후행 콜론(:) 또는 둘 모두에 해당하는 셀로 구성되어 각각 왼쪽, 오른쪽, 또는 가운데 정렬을 나타냅니다. 

#### 1.2 예제
##### 1.2.1
| Markdown |
```
| foo | bar |
| --- | --- |
| baz | bim |
```
| 출력 결과 |
| foo | bar |
| --- | --- |
| baz | bim |

##### 1.2.2
| Markdown |
```
| abc | defghi |
:-: | -----------:
bar | baz
```
| 출력 결과 |
| abc | defghi |
:-: | -----------:
bar | baz

- 한 열의 셀은 길이가 일치할 필요는 없지만, 셀의 길이가 일치하면 더 쉽게 읽을 수 있습니다. 마찬가지로 선행 및 후행 파이프의 사용도 일관되지 않을 수 있습니다.
##### 1.2.3
| Markdown |
```
| f\|oo  |
| ------ |
| b `\|` az |
| b **\|** im |
```
| 출력 결과 |
| f\|oo  |
| ------ |
| b `\|` az |
| b **\|** im |

- 다른 inline 주기를 포함하여 셀 내용에 파이프를 포함 시킵니다.
##### 1.2.4
| Markdown |
```
| abc | def |
| --- | --- |
| bar | baz |
> bar
```
| 출력 결과 |
| abc | def |
| --- | --- |
| bar | baz |
> bar

- 테이블은 첫 번째 빈 줄 또는 다른 블록 수준 구조의 시작 부분에서 파손됩니다.
##### 1.2.5
| Markdown |
```
| abc | def |
| --- | --- |
| bar | baz |
bar

bar
```
| 출력 결과 |
| abc | def |
| --- | --- |
| bar | baz |
bar

bar

##### 1.2.6
| Markdown |
```
| abc | def |
| --- |
| bar |
```
| 출력 결과 |  
| abc | def |
| --- |
| bar |

- 헤더 행은 셀의 개수에 있는 구분자 행과 일치해야 합니다. 그렇지 않으면 테이블이 인식되지 않습니다.   
##### 1.2.7
| Markdown |
```
| abc | def |
| --- | --- |
| bar |
| bar | baz | boo |
```
| 출력 결과 |
| abc | def |
| --- | --- |
| bar |
| bar | baz | boo |

- 표의 나머지 행은 셀의 수에 따라 다를 수 있습니다. 헤더 행에 있는 셀 수 보다 적은 셀의 수가 있다면 빈 셀이 삽입됩니다. 단, 초과는 무시됩니다. 
##### 1.2.8 
| Markdown |
```
| abc | def |
| --- | --- |
```
| 출력 결과 |
| abc | def |
| --- | --- |

- 본문에 행이 없는 경우 HTML출력에 `<tbody>`가 생성되지 않습니다.
### 2. 할일 리스트(Task lists)
#### 2.1 특징
- GFM은 리스트 항목에 대해 추가 처리 단계가 수행되는 할일 리스트를 활성화합니다.

- 할일 리스트 항목은 첫 번째 블록이 할일 리스트 항목 표시로 시작하는 단락이고, 다른 내용 전에 적어도 하나 이상의 공백 문자가 있는 리스트 항목입니다.

- 할일 리스트 항목 표시는 선택적인 공백의 수,  왼쪽 대괄호([), 공백 문자 또는 소문자 또는 대문자 x, 오른쪽 대괄호(])로 구성됩니다.

- 대괄호 사이의 문자가 공백 문자인 경우 확인란은 체크가 취소됩니다. 그렇지 않으면 확인란이 체크됩니다.

- 이 설명은 확인란 요소가 상호작용하는 방식을 정의하지 않습니다. 실제로 구현자는 확인란은 비활성화 또는 불변한 요소로 렌더링하거나 최종 렌더링된 문서에서 활발한 상호작용들(즉. 체크, 체크 해제)를 동적으로 처리할 수 있습니다.

#### 2.2 예제
##### 2.2.1
| Markdown |
```
- [ ] foo
- [x] bar
```
| 출력 결과 |
- [ ] foo
- [x] bar

##### 2.2.2
| Markdown |
```
- [x] foo
  - [ ] bar
  - [x] baz
- [ ] bim
```
| 출력 결과 |
- [x] foo
  - [ ] bar
  - [x] baz
- [ ] bim 
<br>  

- 할일 리스트는 임의로 중첩될 수 있습니다.  

### 3. 취소선(Strikethrough)
#### 3.1 특징
- GFM은 추가적인 강조 유형을 사용할 수 있게 하는 취소선을 활성화합니다.

- 취소선 텍스트는 두 개의 물결표(~)로 묶인 텍스트입니다.

#### 3.2 예제
##### 3.2.1
| Markdown |
```
~~Hi~~ Hello, world!
```
| 출력 결과 |
~~Hi~~ Hello, world!

##### 3.2.2
| Markdown |
```
This ~~has a

new paragraph~~.
```
| 출력 결과 |
This ~~has a

new paragraph~~.

- 기존 강조 구분 기호와 마찬가지로, 새로운 단락은 취소선을 중단합니다.

### 4. 자동링크
#### 4.1 특징
- GFM은 더 많은 조건에서 인식되는 자동 링크를 활성화합니다.

- 자동링크는 더 작은 환경에서 인식될지라도 자동링크의 범위를 지정하기 위해 and 및 to를 사용하지 않고도 구성할 수 있습니다. 이렇게 인식된 모든 자동링크들은 줄의 시작 부분, 공백 뒤 또는 구분 문자 *, _ , ~ , ( 에만 사용할  수  있습니다.

- 확장된 www 자동 링크는 텍스트 www. 를 갖추고 뒤이어 유효한 도메인이 있을 때 인식됩니다. 유효한 도메인은 마침표(.)에 의해 구분된 알파벳-숫자, 밑줄(_) 및 하이픈(-) 부분으로 구성되어 있습니다.  적어도 마침표가 하나 이상 있어야 하며 도메인의 마지막 두 부분에는 밑줄이 없을 수 있습니다.

- 스키마 http는 자동으로 삽입됩니다.

#### 4.2 예제
##### 4.2.1
www.commonmark.org
##### 4.2.2
Visit www.commonmark.org/help for more information.

- 유효한 도메인 이후에는 비 공간이거나 문자가 아닌 것들도 올 수 있습니다.

##### 4.2.3
Visit www.commonmark.org.

Visit www.commonmark.org/a.b.

- 그런 다음 다음과 같이 확장된 자동링크 경로 검증을 적용합니다. 후행 구두점 (특히 ? , ! , . , , , : , * , _ , and , ~)은 링크 내부에 포함될 수 있지만 자동 링크의 일부로 간주되지 않습니다.   

##### 4.2.4
www.google.com/search?q=Markup+(business)

www.google.com/search?q=Markup+(business)))

(www.google.com/search?q=Markup+(business))

(www.google.com/search?q=Markup+(business)

- 자동 링크가 )로 종료되면 전체 자동 링크에서 괄호의 총 개수를 검색합니다. 여는 괄호보다 닫히는 괄호의 수가 더 많은 경우 괄호 안에 자동 링크를 포함하기 위해 자동 링크의 일치하지 않는 후행 괄호 부분은 고려하지 않습니다.

##### 4.2.5
www.google.com/search?q=(business))+ok

- 이 검사는 링크가 닫히는 괄호로 끝날 때만 수행되므로, 자동 링크 내부에 괄호만 있는 경우 특별한 규칙이 적용되지 않습니다.

##### 4.2.6
www.google.com/search?q=commonmark&hl=en

www.google.com/search?q=commonmark&hl;

- 자동 링크가 세미콜론(;)으로 끝나는 경우 엔티티 참조와 유사한지, 이전 텍스트가 하나 이상의 알파벳-숫자 뒤에 오는 경우 인지 확입합니다. 만약 그렇다면 자동 링크에서 제외됩니다.

##### 4.2.7
www.commonmark.org/he<lp

- <는 자동 링크를 즉시 종료합니다.

##### 4.2.8
http://commonmark.org

(Visit https://encrypted.google.com/search?q=Markup+(business))

- 확장된 URL 자동 링크는 확장된 자동 링크 경로 검증에 따라 스키마 중 하나가 http:// 또는 https:// 이고 뒤이어 유효한 도메인이 올 때 0개 이상의 비 공간이거나 문자가 아닌 것이 있으면 인식됩니다.

##### 4.2.9
foo@bar.baz

- 확장된 이메일 자동 링크는 텍스트 노드 내에서 이메일 주소가 인식될 때 인식됩니다. 이메일 주소는 다음 규칙에 따라 인식됩니다. 
    1. 알파벳-숫자 또는 . , - , _ , + 인 하나 이상의 문자입니다.
    2. @기호입니다.
    3. 알파벳-숫자 또는  - , _ , 인 마침표로 구분된 하나 이상의 문자입니다. 적어도 하나의 마침표가  있어야 합니다. 마지막 문자는 - 또는 _ 중 하나일 수 없습니다.

- 스키마 mailto가 생성된 링크에 자동으로 추가됩니다.

##### 4.2.10
hello@mail+xyz.example isn't valid, but hello+xyz@mail.example is.

- +는 @ 앞에 있을 수 있지만, 그 후에 있을 수는 없습니다.

##### 4.2.11
a.b-c_d@a.b

a.b-c_d@a.b.

a.b-c_d@a.b-

a.b-c_d@a.b_

- . , - 및 _는 @의 양쪽에 있을 수 있지만 . 만 이메일 주소 끝에 발생할 수 있습니다. 이 경우 이메일 주소는 주소의 일부로 간주되지 않습니다.

### 5. 허용되지 않는 원시 HTML (Disallowed Raw HTML)
#### 5.1 특징
- GFM은 HTML출력을 렌더링 할 때 다음 HTML 태그들이 필터링되는 태그필터를 활성화합니다.

    - <title>
    - <textarea>
    - <style>
    - <xmp>
    - <iframe>
    - <noembed>
    - <noframes>
    - <script>
    - <plaintext>

- 필터링은 선행 < 를 %lt; 개체로 대체하여 수행합니다. 이러한 태그들은 특히 HTML이 그들 고유의 방식으로 해석되는 방법을 변경할 때 선택되며 (즉. 중첩된 HTML은 다르게 해석됩니다.) , 이것은 일반적으로 다른 렌더링된 Markdown content의 맥락에서 바람직 하지 않습니다.

#### 5.2 예제
##### 5.2.1
<strong> <title> <style> <em>

<blockquote>
  <xmp> is disallowed.  <XMP> is also disallowed.
</blockquote>
   
- 다른 모든 HTML 태그들은 그대로 유지됩니다.
