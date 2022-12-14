## 프로젝트 소개

- 주간 페어 프로그래밍 5 - 영화 리뷰 커뮤니티 CRUD & AUTH & 1:N & Async
- 프로젝트 기간
  - 2022.10.27 - 2022.10.28
- 사용 기술
  - 언어: HTML, CSS, JavaScript, Python
  - 라이브러리: django-bootstrap5, django-extensions, django-imagekit, django-widget-tweaks
  - 프레임워크: Django, Axios



## 스크린샷

![pair5](Assets/README.assets/pair5.gif)



## 프로젝트 목적

페어 프로그래밍을 통한 영화 리뷰 커뮤니티 서비스를 개발합니다. 아래 조건을 만족해야 합니다.

- **CRUD** 구현
- **Staticfiles** 활용 정적 파일(이미지, CSS, JS) 다루기
- Django **Auth** 활용 회원 관리 구현
- Media 활용 동적 파일 다루기
- 모델 간 1 : N / M : N 관계 매핑



## 프로젝트 설명

- 회원 관리
  - `signup`
    - 회원가입을 진행한다.
    - 회원가입이 끝나면, 회원 목록 페이지(accounts:index)로 돌아간다.
  - `login`
    - 로그인을 진행한다.
    - 로그인이 끝나면, 회원 목록 페이지로 돌아간다.
  - `logout`
    - 로그아웃을 진행한다.
    - 로그아웃이 끝나면, 회원 목록 페이지로 돌아간다.
  - `detail`
    - 회원 정보를 보여준다.
    - 회원 정보를 수정하는 기능을 제공한다.
      - 회원 정보 페이지의 유저와, 현재 로그인 한 유저가 같을 시에만 해당 기능을 이용할 수 있다.
    - 회원 정보 페이지의 유저와, 현재 로그인 한 유저가 다를 시, 팔로우 버튼이 나타난다.
  - `update`
    - 회원 정보를 수정한다.
    - 회원 정보 페이지의 유저와, 현재 로그인 한 유저가 같을 시에만 수정할 수 있다.
  - `follow`
    - 로그인한 유저는 해당 유저를 팔로우 할 수 있다.
    - 자기 자신은 팔로우 할 수 없다.
    - 이미 팔로우 한 유저는 기본적으로 언팔로우 버튼이 보여진다.
    - 팔로우, 언팔로우 버튼은 비동기적으로 표시가 바뀐다.



- 영화 리뷰 관리
  - `index`
    - 사람들이 작성한 리뷰 목록을 보여준다.
  - `create`
    - 영화 리뷰를 작성한다. 이때, 선택적으로 사진을 함께 올릴 수 있다.
    - 로그인 한 유저의 정보를 자동으로 DB에 함께 저장한다.
    - 로그인 한 유저만 글을 작성할 수 있다.
  - `detail`
    - 영화 리뷰의 제목 + 내용 + 작성자 이름 + 마지막 수정 시간을 보여준다.
    - 사진이 있으면 사진도 보여준다.
    - 해당 글을 작성한 유저만 글을 수정 및 삭제할 수 있다.
    - 댓글을 입력하는 창과, 댓글 목록도 함께 보여준다.
      - 글을 입력하거나 삭제하면, 비동기적으로 댓글과 댓글의 수가 변경되어 보여진다.
    - 글에 좋아요를 누를 수 있다.
      - 비동기적으로 버튼의 이미지와 총 좋아요 수를 변경하여 보여준다.
  - `update`
    - 영화 리뷰 정보 페이지에서 수정을 진행할 수 있다.
    - 해당 글을 작성한 유저만 글을 수정할 수 있다.
  - `delete`
    - 영화 리뷰 정보 페이지에서 삭제를 진행할 수 있다.
    - 해당 글을 작성한 유저만 글을 삭제할 수 있다.
  - `like`
    - 로그인한 유저는 리뷰에 좋아요를 남길 수 있다.
    - 해당 리뷰의 좋아요 개수를 함께 출력한다.
    - 비동기적으로 좋아요 개수와 이미지가 변화한다.



- 댓글 관리
  - `create_comment`
    - 댓글을 작성한다.
    - 로그인 한 유저의 정보와, 댓글이 작성된 게시글의 정보를 자동으로 DB에 함께 저장한다.
    - 로그인 한 유저만 댓글을 작성할 수 있다.
    - 비동기적으로 생성된다.
  - `delete_comment`
    - 댓글을 삭제한다.
    - 로그인 한 유저만 댓글을 삭제할 수 있다.
    - 비동기적으로 삭제된다.



## 역할 (개발 내용)

- 박태호: 게시글 기본 CRUD, 좋아요 비동기
- 조수람: 페이지 디자인, 팔로우 비동기, 헤로쿠 배포
- 최보영: 유저 기본 Auth, 댓글 비동기, 페이지 디자인



## 배운 점

- 댓글 삭제 비동기를 하는 방법
- 비동기적으로 버튼을 생성하는 방법 (attribute)
- 헤로쿠 배포 중 에러를 해결하는 방법



## 문제 해결

### 문제 상황

- 댓글 삭제 기능을 비동기적으로 구현하기 위해, 댓글을 선택하여 삭제 버튼을 누르면 display를 none으로 하여 숨기려고 하였다.
- 모든 댓글의 태그 id가 동일하였고, display를 none으로 하면 개발자 도구로 다시 댓글을 보이게 할 수 있다는 문제가 발생하였다.



### 해결

- forEach를 통해 모든 댓글의 삭제 버튼(이 있는 폼)에 대하여 eventListener를 등록해주고, 버튼이 눌리면 해당 댓글을 .delete()로 삭제해준다.
