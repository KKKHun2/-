# 원티드 프리온보딩 선발과제🙌
원티드 프리온보딩 선발과제 제출용

## 배포링크
https://wanted-pre-onboarding-frontend-hun.vercel.app

## 과제

1. 로그인/회원가입
2. 투두리스트

## 프로젝트 실행방법

- npm install
- npm start

## 사용한 이유
사용한 통신방법은 전에 진행했었던 익숙한 axios를 활용해 사용했습니다.

그리고 기존에 잘 사용하던 styled-components  사용해서 컴퍼넌트나 페이지들 안에서 css를 구성했습니다.

해당 기능들을 구성한 이유는 크게 세가지로 나눌 수 있을 꺼 같습니다.
1. 로그인/회원가입을 합친 이유는 처음에 분리해서 만들려고 했지만,<br/>
 들어가는 구성이 간단해서 간편하게 보여주는 게 좋을 것 같아서 그렇게 만들었습니다.<br/>
 로그인에서는 간단하게 요구사항처럼 이메일에는 @ 만 들어가고 비밀번호도 8자 이상이면 가능하도록 하였고,<br/>
 회원가입에서는 패스워드, 패스워드 확인으로 두 개가 일치해야만 회원가입 가능하도록 구성하였습니다.,<br/>
 로그인 회원가입 둘 모두 평소에는 로그인/회원가입 버튼이 비활성 상태인 아래 코드 처럼 색변경으로 없어진 것 처럼 하고 조건을 만족할때에 버튼이 보이면서 활성화 되도록 하였습니다. 
 
 ```
  &:disabled {
    background-color: #2f2f2f;
    color: #2f2f2f;
    cursor: not-allowed;
  }
  
 ```
 
2. 투두 페이지는 todoForm, todoList 두 개의 컴포넌트로 구성한 페이지인데<br/>
처음에 추가 할때는 화면에도 저장이되서 아래 리스트에 보이고 로컬스토리지에도 저장해서 사이트에 다시 들어와도 남게 만들었습니다<br/>
예전에 투두리스트 과제 때 사용한 거를 가져다 사용했고 props로 내려서 사용했습니다<br/>
확인 버튼을 누르면 밑줄이 생기고 글자가 연해 지게 해서 완료했다는 걸 표시했고<br/>
수정 버튼에서는 아래 코드 처럼 수정 눌렀을때만 취소버튼이 생기도록 했고 기존꺼를 저장하는 방식이라 취소 시 아무런 일이 안 생기게 했습니다.
```

{editTodo &&
        <TodoButton2 type="submit" onClick={handleOnClick} >
        취소
        </TodoButton2>}
        
```
삭제 버튼은 삭제해서 로컬 스토리지에 저장된 todo와 화면에서의 해당 todo도 삭제 처리 되게 했습니다.

3. Router 에서는 localStorage.getItem("token") 로 삼항연산자를 사용해서 토큰이 있는지 없는지 판단해서 페이지 이동이 되도록 했습니다.
 <br/>
  각자의 페이지에 적어주면 중복코드여서 이곳에서 간편하게 관리하게 했습니다.
  
  ```
  const Router = () => {
  const isToken = localStorage.getItem("token");
  const routes = useRoutes([
    {
      path: '/',
      element: isToken ? <Navigate replace to="/todo" /> : <Login />,
    },
    {
      path: '/todo',
      element: isToken ? <Todo /> : <Navigate replace to="/" />,
    },
  ]);
  return routes;
};

```

4. 토큰은 간단하게 로그인 할때 아래 코드로 토큰얻게 했습니다.

```
localStorage.setItem("token", response.data.access_token); 

```
  아쉬운점은 .env로 통신 주소를 따로 적어서 코드내에 주소가 보이는걸 가리는걸 하려고 했으나 잊어버리고 그렇게 못했습니다. </br>
  delete와 put 메소드를 로컬스토리지에 저장하게한 투두리스트 덕에 오류가 좀 생겼었는데 수정 못한 것도 아쉽습니다.</br>
  ui가 깔끔하지 못해서 좀 정리를 못한 것도 아쉽습니다.

## 사용한 라이브러리

- React Router
- Axios
- Styledcomponents
- react-icons

## 기술스택
<div align=center><h1>📚 FE STACKS</h1></div>

<div align=center>
<img src="https://img.shields.io/badge/GitHub-000000?style=for-the-badge&logo=GitHub&logoColor=white">
<img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=Git&logoColor=white">
<img src="https://img.shields.io/badge/Gitmoji-31A8FF?style=for-the-badge&logo=Gitmojii&logoColor=white">
<img src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=React&logoColor=white">
<img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=JavaScript&logoColor=white">
<br />
<img src="https://img.shields.io/badge/styledcomponents-DB7093?style=for-the-badge&logo=styledcomponents&logoColor=white">
<img src="https://img.shields.io/badge/ReactRouter-CA4245?style=for-the-badge&logo=ReactRouter&logoColor=white">
<img src="https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=Vercel&logoColor=white">
<img src="https://img.shields.io/badge/Axios-5A29E4?style=for-the-badge&logo=Axio&logoColor=white">
</div>
