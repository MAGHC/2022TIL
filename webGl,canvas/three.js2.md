### 광원

amient light = > 주변광

directional light = > 방향광 ⇒ 좋은예:햇빛

spot light : 스포트라이트

```js

빛을 주기위해선 mesh 재질을 바꿔야됨
const ambientLigth = new THREE.AmbientLight(0x404040);
scene.add(ambientLigth);
const directionalLight = new THREE.DirectionalLight(0xffffff, 0.5);
scene.add(directionalLight);
const gui = new dat.GUI();

const dlLgihtHelper = new THREE.DirectionalLightHelper(directionalLight, 0.8); // 두번쨰 인수 헬퍼 크기
scene.add(dlLgihtHelper);
```

### 그림자 설정

```js
renderer.shadowMap.enabled = true;

그리고 수동으로 설정해줘야됨

plane 과 sphere

directionalLight.castShadow = true


plane.receiveShadow = true;

sphere.castShadow = true;



그림자 헬퍼

const dlLightshadowHelper = new THREE.CameraHelper(
  directionalLight.shadow.camera
);

scene.add(dlLightshadowHelper);


그림자가 짤리는 이유


directionalLight.shadow.camera.bottom = -12;

하면 늘어남


//스포트 라이트로 변경

const spotlight = new THREE.SpotLight(0xffffff);
scene.add(spotlight);
spotlight.position.set(-100, 100, 0);
spotlight.castShadow = true;

const slHelpoer = new THREE.SpotLightHelper(spotlight);
scene.add(slHelpoer);


그림자가 픽셀화 됨


이유? 각각의 세그먼트가 4방향인데 이것들이 제각각이라

이각도를 줄이면됨

spotlight.angle = 0.2;


// dat gui 로 spotlight 핸들

const option = {
  변경: "#ffea00",
  와이어프레임: false,
  speed: 0.01,
  angle: 0.2,
  panumbra: 0,// 점진적으로 흐림 효과
  intensity: 1 //빛 세기
};

function animate() {
  Box.rotation.x += 0.01;
  Box.rotation.y += 0.01;
  step += option.speed;
  spotlight.angle = option.angle;
  spotlight.penumbra = option.panumbra;
  spotlight.intensity = option.intensity;
  slHelpoer.update(); // 중요  변경될떄마다 헬퍼도 업데이트  아니여도 적용은 되는데 헬퍼는 적용안됨
  sphere.position.y = 10 * Math.abs(Math.sin(step));
  renderer.render(scene, camera);
}
renderer.setAnimationLoop(animate);





```

### 포그 효과

```js
scene.fog = new THREE.Fog(0xffffff, 0, 200);

스크롤에 따른 fog 효과  스크린이 해당 수치만큼 멀어질수록 안보이고 가까이 가야보임

0, 300 이면 300까지 정상점차 안보이다가 그이상은 안봉미

방법이 하나 더있는데

scene.fog = new THREE.FogExp2(0xffffff, 0.01); 이건 카메라로부터의 거리 (둘중 하나 쓸거면 하나는 주석처리해야됨

```

### 배경 설정

```js
renderer.setClearColor(0x5c7e96); // 컬러

이미지 임포트해주고난다음에

const textLoader = new THREE.TextureLoader(); 로더
scene.background = textLoader.load(universe); // 이미지 넣어줌

다만 이건 평면

입체적인 배경을 만들고싶다면 다면 로더를 불러와야됨

const cubeTextLoader = new THREE.CubeTextureLoader(); 로더
scene.background = cubeTextLoader.load([universe, universe2, universe, universe, universe2, universe]);

이건 다면 각 6개



텍스쳐 입히기


const earthGeo = new THREE.SphereGeometry(4, 20, 20);
const earthMa = new THREE.MeshStandardMaterial({ map: textLoader.load(earthImg) }); // 이렇게 넣어줌

const earth = new THREE.Mesh(earthGeo, earthMa);

```

### 리사이징 대응 시키기

윈도우 애드이벤트리스너 resize 해가지고 카메라 업데이트시키고 render setsize 하면됨

```js
window.addEventListener("resize", () => {
  camera.aspect = window.innerWidth / window.innerHeight;
  camera.updateMatrix();
  renderer.setSize(window.innerWidth, window.innerHeight);
});
```

### 번들러

이건 좀 three랑 상관없이 빼야되나 싶기도한데.

아무튼 로컬에서 cors 오류가있음으로 parcel 번들러를 통해 로컬에서 실험했음 다른 방법이 공식 문서에 있었는데 그걸로 하진않았아서.

parcel 파일 하면 알아서 번들링하여 생성됨 로컬에서 할때.
