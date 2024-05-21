1.
p5.js의 특징
간단하고 직관적인 문법으로 초보자도 쉽게 학습 가능하며 브라우저로 즉시 결과확인이 가능하여 학습속도가 빠르다
웹기반이기 때문에 특정 프로그램 설치를 요구하지 않는다

인터랙티브 아트는 사용자와 상호작용할 수 있는 예술 작품을 의미한다. 전통적인 예술 작품이 정적이라면, 인터랙티브 아트는 사용자의 입력이나 환경 변화에 따라 실시간으로 변형된다 이러한 특성 때문에 관객은 작품에 직접 참여할 수 있으며, 그 경험이 각기 다르게 나타난다

코드
function setup() {
    createCanvas(800, 600);
    background(255);
}
function draw() {
// 마우스 위치에 원을 그림
if (mouseIsPressed) {
fill(random(255), random(255), random(255)); // 랜덤한 색상으로 원 채우기
        noStroke();
ellipse(mouseX, mouseY, 50, 50); // 마우스 위치에 지름 50의 원 그리기
}
}

2.
통합이 쉬워 웹 개발자들이 기존의 웹 프로젝트에 쉽게 통합할수있다
빠르게 머신러닝 모델을 테스트하고 프로토타이핑을 할 수 있다
다양한 예제와 튜토리얼이 제공되어 학습하기 좋다

3.
three.js의 주요 구성요소로는
Scene Camera Renderer Mesh Geometry Material Light 7개로 구성되어 있다
Scene (장면): 3D 객체들이 배치되는 공간다. 조명, 카메라, 메쉬 등 모든 3D 요소가 포함된다.
Camera (카메라): 장면을 바라보는 시점을 정의한다. 일반적으로 원근 카메라(Perspective Camera)와 직교 카메라(Orthographic Camera)가 사용된다.
Renderer (렌더러): 장면과 카메라를 사용하여 이미지를 생성하고, 이를 HTML <canvas> 요소에 렌더링한다. WebGLRenderer가 가장 많이 사용된다.
Mesh (메쉬): 3D 객체를 정의하는데 사용된다. 기하학(Geometry)과 재질(Material)의 결합으로 이루어진다.
Geometry (기하학): 메쉬의 형태를 정의한다. BoxGeometry, SphereGeometry 등 다양한 형태를 제공한다.
Material (재질): 메쉬의 표면 특성을 정의한다. MeshBasicMaterial, MeshStandardMaterial 등 다양한 재질이 있다
Light (조명): 장면을 비추는 조명이다. PointLight, DirectionalLight, AmbientLight 등 여러 종류의 조명이 있다

1 html작성
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Three.js 3D Scene</title>
<style>
body { margin: 0; }
canvas { display: block; }
</style>
</head>
<body>
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script src="script.js"></script>
</body>
</html>
2 script.js로 작성
// 장면(Scene)을 생성
const scene = new THREE.Scene();

// 카메라(Camera)를 생성 (원근 카메라 사용)
const camera = new THREE.PerspectiveCamera(
75, // 시야각 (field of view)
window.innerWidth / window.innerHeight, // 종횡비 (aspect ratio)
0.1, // near 클리핑 평면
1000 // far 클리핑 평면
);
camera.position.z = 5; // 카메라 위치 설정

// 렌더러(Renderer)를 생성
const renderer = new THREE.WebGLRenderer();
renderer.setSize(window.innerWidth, window.innerHeight); // 렌더러 크기 설정
document.body.appendChild(renderer.domElement); // 렌더러의 캔버스를 HTML에 추가

// 큐브(Cube)를 생성
const geometry = new THREE.BoxGeometry(); // 큐브 기하학
const material = new THREE.MeshBasicMaterial({ color: 0x00ff00 }); // 큐브 재질
const cube = new THREE.Mesh(geometry, material); // 기하학과 재질을 결합하여 메쉬 생성
scene.add(cube); // 장면에 큐브 추가

// 애니메이션 함수 정의
function animate() {
requestAnimationFrame(animate); // 다음 프레임에 애니메이션 함수 호출

// 큐브를 회전
cube.rotation.x += 0.01;
cube.rotation.y += 0.01;

// 장면(Scene)과 카메라(Camera)를 사용하여 렌더링
renderer.render(scene, camera);
}

// 애니메이션 시작
animate();

4
r3f의 특징
react 컴포넌트를 사용하여 개발자가 친숙한 React 방식으로 3D 장면을 구성하고 관리할 수 있게 한다
R3F는 선언적인 코딩 스타일을 지원하여, 복잡한 3D 장면을 직관적이고 간결하게 구성할 수 있습니다. React의 JSX 문법을 사용하여 3D 객체를 정의할 수 있다
React의 상태 관리와 생명주기 메서드를 활용하여 3D 장면의 상태를 제어하고 업데이트할 수 있다
React의 가상 DOM과 조화를 이루어 성능을 최적화합니다. R3F는 변경된 부분만 렌더링하므로, 불필요한 렌더링을 줄일 수 있다
R3F는 Three.js의 대부분의 기능을 지원하며, 필요에 따라 Three.js의 원시 객체를 직접 사용할 수 있다
r3f의 이점
React를 이미 사용하고 있는 개발자에게 친숙한 환경을 제공하여, 3D 그래픽스를 기존 프로젝트에 쉽게 통합할 수 있다
React 컴포넌트의 장점을 살려, 모듈화된 3D 객체와 장면을 작성하고 재사용할 수 있다
선언적이고 컴포넌트 기반의 접근 방식으로, 3D 장면을 더 빠르고 효율적으로 개발할 수 있다
React의 생태계와 도구를 활용하여, 3D 그래픽스 프로젝트의 테스트, 상태 관리, 라우팅 등을 손쉽게 구현할 수 있다
코드의 가독성과 구조화된 방식 덕분에, 유지보수가 쉽고 협업이 용이하다
