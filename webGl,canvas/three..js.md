### three.js

3d 모델링을 할 수 있게끔 해주는 webgl을 사용한 외부 라이브러리

이번에 기업과제를 통해 안그래도 webGl에 갈증이 있었는데 하게되었다.

주로 공식문서와 직접 쳐보고 예제나 다른 코드를 보고 구현 한 것들 위주로 실제 쳐본 코드로 정리하겠다

요번에 하다가 직면한 문제도 있는데 원래 codesandbox.io 에서 진행하다가

이거 레파지토리에다가 올려볼까하고

레파지토리에서 작업하는데 로컬인데도 cors 오류가 떴다 해결방법은 찾았는데 그걸로 해결이 안됬다 이제 코드 에러보다 이런 불러오는 에러 같은게

더짜증나고 찾기힘들다. 아무튼

모던도 한바퀴본지 좀 되고 이런저런 코드 계속 보고 치고 강의도 계속 보고 하다보니까

이제 공식문서보면서 이해못할 뭔가는 없어보인다

그리고 원래 게임이나 텍스쳐 그래픽을 좋아했음으로 지오메트리나 mesh 에 대해서 대략적인개념을 알고있는것도 약간의 도움은된듯하다.

```js
import * as dat from "dat.gui";
import * as THREE from "three";
import { OrbitControls } from "three/examples/jsm/controls/OrbitControls";

//dat 는 option을 만들어서 컨트롤 할 수 있는 컨트롤러
//orbitControls 는 알아서 마우스 액션과 스크롤을 하면 볼수있게해주는 컨트롤러 인데 이걸 어떻게 구현하지 했는데 이거 있다는걸 알고 좀 허무
//THREE 가 이제 주로 써먹을 THREE .js

const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight);
document.body.appendChild(renderer.domElement);

// 새롭게 그릴 렌더의 사이즈를 설정하고 body 에 추가 해준다.  참고로 바디 마진이 0 아니면 떠있다 reset css 나 하여간 이제 그런거 안적어도 알잖아

const camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 1, 500);
camera.position.set(0, 1, 10); // 카메라를 설정해준다 포지션은 각각 x,y,z 로 따로 set을 사용하여 한번에 설정하거나 따로 설정할수있다.
camera.lookAt(0, 0, 0);
const orbit = new OrbitControls(camera, renderer.domElement); // orbit 컨트롤러 설정
orbit.update(); // 카메라 포지션이 설정되고 항상 함께 orbit 도 같이 업데이트 되야된다 * 중요

const scene = new THREE.Scene(); // 씬을 추가한다

const helper = new THREE.AxesHelper(40); // 헬퍼중 x,y,z 축 을 보여주는 헬퍼
scene.add(helper); // scene.add() 하면 씬에 추가

/*
여긴 라인관련된거 라서 일단 생략 
const material = new THREE.LineBasicMaterial({ color: 0x0000ff });

const points = [];
points.push(new THREE.Vector3(-10, 0, 0));
points.push(new THREE.Vector3(0, 10, 0));
points.push(new THREE.Vector3(10, 0, 0));

const geometry = new THREE.BufferGeometry().setFromPoints(points);

const line = new THREE.Line(geometry, material);
*/

const Boxgeo = new THREE.BoxGeometry();
const Boxmat = new THREE.MeshBasicMaterial({ color: 0xffff00 });
const Box = new THREE.Mesh(Boxgeo, Boxmat);

// 하나의 오브젝트를 만들고싶다면 그 오브젝트의 지오메트리 형태와 마테리얼재료가 있어야되며 그 오브젝트는 그두가지를 합친걸로 구성된다

scene.add(Box);

const planeGeo = new THREE.PlaneGeometry(30, 30, 10); // 벽면 생성
const planeMa = new THREE.MeshBasicMaterial({
  color: 0xffffff,
  side: THREE.DoubleSide, // 양면 속성
});
const plane = new THREE.Mesh(planeGeo, planeMa);

plane.rotation.x = -0.5 * Math.PI; // 바닥에 붙이기 포지션 변경

const gridHelper = new THREE.GridHelper(30); // 그리드 헬퍼  인수는 크기

const sphereGeo = new THREE.SphereGeometry(1);
const sphereMat = new THREE.MeshBasicMaterial({
  color: 0xfffff,
  wireframe: false,
});
const sphere = new THREE.Mesh(sphereGeo, sphereMat); // 여기까지 구 형태 정의 와이어 프레임 은 말그대로 와이어로 표시 (안에 투명)

sphere.position.set(-10, 0, 0); // 카메라 와 마찬가지로 x,y,z

const gui = new dat.GUI(); // dat gui 설정

const option = {
  변경: "#ffea00",
  와이어프레임: false,
  speed: 0.01,
}; //다트 옵션 설정
gui.addColor(option, "변경").onChange((e) => {
  sphere.material.color.set(e);
});

//옵션에 따라 온체인지
gui.add(option, "와이어프레임").onChange((e) => {
  sphere.material.wireframe = e;
});

gui.add(option, "speed", 0, 0.1);

//혹은 최댓값 최소값 설정  하면 알아서 화면에서 dat.gui 에 떠서 컨트롤할수있게된다.

scene.add(gridHelper);
scene.add(sphere);
scene.add(plane);

let step = 0; // 애니메이션 설정을 위한 스탭 단계

function animate() {
  Box.rotation.x += 0.01; // 1프레임 당 0.01  (60frame)
  Box.rotation.y += 0.01;
  step += option.speed;
  sphere.position.y = 10 * Math.abs(Math.sin(step)); // 스피드 넣어서 위아래로 움직이게끔 구현
  renderer.render(scene, camera);
}
renderer.setAnimationLoop(animate); // 애니메이션 반복

// scene.add(line);
```
