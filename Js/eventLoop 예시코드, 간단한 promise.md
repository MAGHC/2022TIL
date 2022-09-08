### 이벤트 루프 예시 코드

```js

console.log('start')

setTimeout(()=> console.log('0초 타이머'),0)
Promise.resolve('resolve promise 1').then(res=>console.log(res))

console.log('end')

이상태에서 콘솔에 등록되는 순서는??

일단 스타트엔드가 당연히 먼저 찍힐것이고

그다음에 셋타임아웃도 프로미스도 똑같이 바로 실행이되지만

이벤트루프의 원리를 알고있어야 해당 순서를 알 수 있다.

마이크로 테스크 큐에 프로미스가 들어있고 마이크로테스크 큐에 있는게 다 실행이되어야 다음으로 한바퀴 돌기떄문에

resolve promise 1 이 그다음 찍히고 setTimeout이 찎힌다


//start end resolve promise 1 0초 타이머  순서

console.log('start')

setTimeout(()=> console.log('0초 타이머'),0)
Promise.resolve('resolve promise 1').then(res=>console.log(res))

Promise.resolve('resolve promise 2').then(res=>console.log(res))

console.log('end')


이렇게 프로미스를 하나 더 늘리고 두번쨰가 엄청 오래걸린다고 가정



Promise.resolve('resolve promise 2').then(res=>{
for(let i =0 ; i<1000000; i++){}console.log(res})

이렇게 하면 더 잘 확인가능

좀더 명확하게 0초 타이머가 뒤에 실행되는게 보임



```

### geoloaction 을 통한 간단한 프로미스 작성을 통한 정리

```js
(resolve) => then;
(reject) => err;



const lotteryPromise = new Promise(function(resolve,reject),{
if(Math.random()>=0.5){
resolve('you win')
}else{
reject('you lose')
}
})

lotteryPromise .then(res=>console.log(res))//resolve
.cath(err=>console.err(err))//reject

와 같다.


navigator.geolocation.getCurrentPosition(position=>console.log(position),err=>console.error(err))


이걸 프로미스로 핸들해보자


const getPosition=()=>{
return new Promise(function(resolve,reject){})}


안에 넣어주기
const getPosition=()=>{
return new Promise(function(resolve,reject){navigator.geolocation.getCurrentPosition(position=>resolve(position),err=>reject(err))})}

사실 이건

const getPosition=()=>{
return new Promise(function(resolve,reject){navigator.geolocation.getCurrentPosition(resove, reject)})}
와같음



getPosition().then(pos=>console.log(pos)).catch(err=>console.err(err))

끝


```
