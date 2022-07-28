### useTab

Tab 의 내용 전환 / 함수라고 생각하면된다.

훅들을 만들 고 쓰는과정에서 신기한 건 다른게 아니고

구조분해할당같은것들을 이렇게 유연하게 쓴다고?

혹은 내머리가 이렇게 정적인 사고방식을 가졌구나 하는 깨달음 을준다 아무튼

먼저 content 를 만들어준다

배열안에 객체로. 그래야 접근도 편하고 배열 메서드들쓰지

const tabcontent =[{
tabId:1,
content:내용1

},{
tabId:2
content:내용2

}]

## 버튼 누를때마다 핸들링 / currentItem => alltab의 컨텐츠 배열

const useInput =(initialValue, allTab)=>{
const [currentidx, setCurrentIdx]=useState(initialValue)
return {currentItem:allTab[currentidx], changeCur:setCurrentIdx}
}

{tabcontent.map((item,idx)=>{
<button onclick={()=>{changeCur(idx)}}></button>
})}

<h1>{currentItem.content}</h1>

이런식으로 map으로 버튼만 뿌리고 컨텐츠가 유동적으로 바뀌게 할 수 있다.

신기
