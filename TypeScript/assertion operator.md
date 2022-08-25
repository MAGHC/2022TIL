### assertion operator

!
연산자인데

해당 피연산자가 null, undefined 가 아님을 단언한다.

interface AuthContextType {
isAuthenticated: Boolean;
currentUser: {};
}

let AuthContext = createContext<AuthContextType>(null!);
