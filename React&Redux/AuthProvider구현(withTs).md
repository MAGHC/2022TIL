## authProvider 구현

### 1.context api 를 활용한 provider

```tsx

Auth 파일 생성

일단 context 를 정의해준다.


아 그리고 컨텍스트에 뭐가 넣어질 것인지 interface도 미리 만들어둔다 나의 경우

currentUser 라는 현재 로그인 한 객체와 isAuthenticated 를 각각 firebase 로그인 에 user 가 있을시에 정보를 넣어주고 true로 변환시켜놨다.


interface AuthContextType {
  isAuthenticated: Boolean;
  currentUser: {};
}

이렇게 인터페이스를 넣어두면 다음부터 사용할때 자동완성이 되서 좋음



let AuthContext =createContext<AuthContextType>(null!)

아. 참고로 변수명 대문자 시작은 나도 모르겠는데 react-router 공식예제에서 그렇게 해서 따라했다 컨벤션인가 보다


이제 사용할 auth provider 를 컴포넌트 형태로 만들어준다.


export const AuthProvider =({children}):{children:React.ReacNode}=>{




}

이떄 provider 특징상 아래 컴포넌트로 전부 내려줌으로 {children}을 넣어준다


세부 내용은 사람마다 메서드 마다 다르겠지만


export const AuthProvider = ({ children }: { children: React.ReactNode }) => {
  const [currentUser, setCurrentUser] = useState({});
  const [isAuthenticated, setIsAuthenticated] = useState(false);

  auth.onAuthStateChanged((user) => {
    if (user) {
      setCurrentUser(user.providerData[0]);
      setIsAuthenticated(true);
    } else {
      setCurrentUser({});
      setIsAuthenticated(false);
    }
  });

  return <AuthContext.Provider value={{ currentUser, isAuthenticated }}>{children}</AuthContext.Provider>;
};


나는 이렇게 구현했다 value 에는 currentUser, isAuthenticated 가 들어간다.


원래의 예제에는 구조분해 할당해서 value 로 통치는데 나는 좀 꺼내쓰기 용이하게 두개로 뺴놨다.


그리고 보통은 다른곳에 hooks 폴더로

useAuth를 만드는 데 나는 Auth 폴더 안에 하나로 묶여있는 게 맞다고 개인적으로 판단하여


export function useAuth() {
  return useContext(AuthContext);
}

밑에다 하나 만들어놨다.






```

### 2. react-router 에서 redirect 페이지 만들기

```tsx

const AuthValidPage = ({ children }: { children: JSX.Element }) => {
  let location = useLocation();
  let auth = useAuth();
  console.log(auth);

  if (auth.isAuthenticated === false)
    return (
      <>
        {alert("로그인해주세요")}
        <Navigate to="/login" state={{ from: location }} replace />
      </>
    );
  else return children;
};


별거없다 만들고나먼 if 로 false 상태라면 Navigate 컴포넌트로 replace 시킨다. 다만 신기했던거는 alert를 어떻게  띄워주지? 하고 있었는데 저렇게 하니까 됬다.


else return children 을 해주고



 <Route
          path="/chatmain"
          element={
            <>
              <AuthValidPage>
                <ChatMain></ChatMain>
              </AuthValidPage>
            </>
          }
        />


        rotue 는 이렇게 구현되어있다.




```
