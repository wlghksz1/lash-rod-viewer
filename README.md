# 롯드 3D 뷰어

속눈썹 롯드 STEP 파일을 웹 브라우저에서 바로 열어 보는 뷰어입니다. 설치가 필요 없고, 파일은 보는 사람의 PC 안에서만 처리됩니다(서버로 올라가지 않음).

## 사용법 (받는 분용)

1. 뷰어 링크를 엽니다. (크롬 또는 엣지 최신 버전 권장)
2. 받은 STEP 파일(.stp / .step)을 화면에 끌어다 놓거나 **파일 열기** 버튼으로 엽니다.
3. 오른쪽에 **전체 치수**(가로·세로·높이)가 표시됩니다.
4. **바닥면** 버튼으로 아래에서 올려다본 시점으로 바꾼 뒤, **바닥면 클릭해 단면 위치 선택** 버튼을 누르고 롯드 바닥면 위의 한 지점을 클릭합니다.
5. 그 지점에서 바닥면에 수직인 단면이 표시됩니다. 슬라이더로 단면 위치를 길이 방향으로 옮길 수 있습니다.
6. **치수 확인** 버튼을 누르면 단면의 **본체 폭·높이**가 3D 화면과 2D 단면 그림에 표시됩니다. (날개 부분은 제외)

## 정밀도

- STEP 원본 곡면을 편차 0.01 mm로 표시합니다. 확대해도 곡면이 각지지 않습니다.
- 단면 치수는 정밀 CAD 계산값과 0.02 mm 이내로 일치합니다.
- 단위는 mm 입니다.

## 파일 구성

```
viewer/
  index.html              뷰어 본체 (HTML + JavaScript 한 파일)
  lib/occt-import-js.js   STEP 읽기 엔진 (OpenCascade WebAssembly)
  lib/occt-import-js.wasm
  lib/three.module.js     3D 렌더링 (Three.js r170)
  lib/OrbitControls.js    마우스 회전·확대 조작
```

## 직접 실행 (개발용)

브라우저 보안 때문에 파일을 더블클릭해서 여는 방식(file://)으로는 동작하지 않습니다. 간단한 웹 서버로 띄우세요.

```bash
cd viewer
python -m http.server 8765
```

그다음 `http://localhost:8765/` 를 엽니다. `?file=경로` 를 붙이면 서버에 있는 STEP을 바로 엽니다.

## GitHub Pages 배포

1. 이 폴더(`viewer`)를 GitHub 공개 저장소에 올립니다.
2. 저장소 Settings → Pages → Source: `Deploy from a branch`, Branch: `main`, 폴더: `/ (root)` 로 저장합니다.
3. 몇 분 뒤 `https://<계정>.github.io/<저장소>/` 로 접속할 수 있습니다.

## 라이선스

- occt-import-js: MIT (lib/ 폴더의 license 파일 참고)
- Three.js: MIT
