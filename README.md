<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8" />
</head>
<body>

<h1>Linux 명령어 및 개념 정리</h1>

<hr />

<h2>1. tail</h2>
<p><strong>기능</strong>: 파일의 마지막 부분을 출력</p>
<p><strong>예시</strong>:</p>
<pre><code>tail -100 filename.log  # 파일의 마지막 100줄 출력</code></pre>

<hr />

<h2>2. grep</h2>
<p><strong>기능</strong>: 텍스트에서 특정 문자열(또는 정규표현식)을 포함한 줄을 찾음</p>
<p><strong>옵션</strong>:</p>
<ul>
  <li><code>-E</code>: 확장 정규표현식 사용</li>
</ul>
<p><strong>예시</strong>:</p>
<pre><code>grep "pattern" file.txt
grep -E "^\[[0-9]{4}-[0-9]{2}-[0-9]{2}" file.txt
</code></pre>

<hr />

<h2>3. 명령어 실행 결과를 변수에 저장하는 법</h2>
<p><strong>백틱(<code>`</code>) 또는 <code>$()</code> 사용</strong></p>
<p><strong>예시</strong>:</p>
<pre><code>now=$(date +"%Y-%m-%d %H:%M:%S")
last_line=`tail -100 file.log | grep "pattern" | tail -1`
</code></pre>

<hr />

<h2>4. 조건문 사용법</h2>
<p><code>-f</code> : 파일 존재 여부 확인 (일반 파일)</p>
<p><code>-d</code> : 디렉토리 존재 여부 확인</p>
<p><strong>예시</strong>:</p>
<pre><code>if [ -f "/path/to/file" ]; then
  echo "파일 있음"
else
  echo "파일 없음"
fi

if [ -d "/path/to/dir" ]; then
  echo "디렉토리 있음"
else
  echo "디렉토리 없음"
fi
</code></pre>

<hr />

<h2>5. chmod</h2>
<p><strong>기능</strong>: 파일이나 스크립트 실행 권한 변경</p>
<p><strong>예시</strong>:</p>
<pre><code>chmod +x script.sh  # 실행 권한 추가
</code></pre>

<hr />

<h2>6. cd</h2>
<p><strong>기능</strong>: 디렉토리 이동</p>
<p><strong>예시</strong>:</p>
<pre><code>cd ..               # 상위(부모) 디렉토리로 이동
cd /path/to/dir     # 절대 경로로 이동
</code></pre>

<hr />

<h2>7. 세미콜론(<code>;</code>), 파이프(<code>|</code>), 백그라운드 실행(<code>&</code>)</h2>
<ul>
  <li><code>;</code> : 여러 명령어를 순차 실행</li>
  <li><code>|</code> : 앞 명령어의 결과를 뒤 명령어의 입력으로 사용 (파이프라인)</li>
  <li><code>&</code> : 명령어를 백그라운드에서 실행</li>
</ul>

<hr />

<h2>8. shebang (<code>#!/bin/bash</code>)</h2>
<p><strong>스크립트 첫 줄에 작성</strong></p>
<p>어떤 셸로 실행할지 지정하는 역할</p>

<hr />

<h2>9. 변수 선언과 사용</h2>
<p>변수 선언:</p>
<pre><code>VAR="값"
</code></pre>
<p>변수 사용:</p>
<pre><code>echo $VAR
</code></pre>

<hr />

<h2>10. echo</h2>
<p><strong>기능</strong>: 문자열 출력</p>
<p><strong>예시</strong>:</p>
<pre><code>echo "Hello World"
</code></pre>

<hr />

<h2>11. 날짜 출력 (date 명령어)</h2>
<p><strong>예시</strong>:</p>
<pre><code>date +"%Y-%m-%d %H:%M:%S"
</code></pre>

<hr />

<h2>12. 권한 관련 오류</h2>
<p><strong>문제</strong>: <code>Permission denied</code> 에러 발생 시</p>
<p><strong>해결법</strong>:</p>
<pre><code>chmod +x filename  # 실행 권한 추가
</code></pre>

<hr />

<h2>13. 리눅스 쉘 명령어 예시</h2>
<p>특정 로그에서 날짜가 포함된 마지막 줄 찾기 예제</p>
<pre><code>last_line=$(tail -100 /path/to/logfile.log | grep -E "^\[[0-9]{4}-[0-9]{2}-[0-9]{2}" | tail -1)
</code></pre>
<p>시간 부분만 추출해서 사용하기</p>
<pre><code>time_only=${last_line:12:8}  # 문자열에서 13번째부터 8글자 추출
</code></pre>

<hr />

<h2>14. 정규표현식 간단 설명</h2>
<ul>
  <li><code>^[0-9][0-9]:</code>  
    줄 맨 앞에 숫자 두 개와 콜론이 있는 패턴 (예: <code>12:</code>)
  </li>
  <li><code>^\[[0-9]{4}-[0-9]{2}-[0-9]{2}</code>  
    줄 맨 앞에 대괄호와 <code>YYYY-MM-DD</code> 날짜 형식이 있는 패턴 (예: <code>[2025-08-05</code>)
  </li>
</ul>


</body>
</html>
