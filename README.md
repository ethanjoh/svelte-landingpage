# Svelte + Vite

이 템플릿은 Vite 환경에서 Svelte 개발을 시작하는 데 도움을 주기 위해 제작되었습니다.

## 권장 IDE 설정

[VS Code](https://code.visualstudio.com/) + [Svelte](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode).

## 공식 Svelte 프레임워크가 필요하신가요?

Vite를 기반으로 하는 [SvelteKit](https://github.com/sveltejs/kit#readme)을 확인해 보세요. 서버리스 우선 접근 방식으로 어디에나 배포할 수 있으며 다양한 플랫폼에 맞게 조정 가능합니다. TypeScript, SCSS, Less를 기본적으로 지원하며, mdsvex, GraphQL, PostCSS, Tailwind CSS 등의 지원을 쉽게 추가할 수 있습니다.

## 기술적 고려사항

**SvelteKit 대신 이 템플릿을 사용하는 이유는 무엇인가요?**

- SvelteKit은 자체 라우팅 솔루션을 제공하는데, 이는 일부 사용자에게 선호되지 않을 수 있습니다.
- SvelteKit은 기본적으로 Vite 앱이라기보다는 Vite를 내부적으로 사용하는 프레임워크에 가깝습니다.

이 템플릿은 HMR과 intellisense 측면에서 개발자 경험을 고려하면서 Vite + Svelte로 시작하기 위해 가능한 한 최소한의 내용만 포함하고 있습니다. 다른 `create-vite` 템플릿과 동일한 수준의 기능을 보여주며, Vite + Svelte 프로젝트에 처음 입문하는 초보자에게 좋은 출발점입니다.

나중에 SvelteKit이 제공하는 확장된 기능과 확장성이 필요할 경우, 마이그레이션하기 쉽도록 템플릿이 SvelteKit과 유사하게 구조화되어 있습니다.

**`.vscode/extensions.json`을 포함한 이유는 무엇인가요?**

다른 템플릿들은 보통 README를 통해 간접적으로 확장을 권장하지만, 이 파일을 사용하면 사용자가 프로젝트를 열 때 VS Code가 권장 확장을 설치하라는 프롬프트를 표시할 수 있습니다.

**JS 템플릿에서 `checkJs`를 활성화한 이유는 무엇인가요?**

런타임에 변수 타입을 변경하는 대부분의 경우는 의도적이라기보다는 실수일 가능성이 높습니다. 따라서 기본적으로 고급 타입 검사 기능을 제공합니다. 만약 JavaScript의 동적 타입 특성을 활용하고 싶다면, 구성을 매우 간단하게 변경할 수 있습니다.

**HMR이 로컬 컴포넌트 상태를 유지하지 않는 이유는 무엇인가요?**

HMR 상태 유지는 여러 가지 까다로운 문제를 동반합니다! 예상치 못한 동작을 하는 경우가 많아 `svelte-hmr`과 `@sveltejs/vite-plugin-svelte` 모두에서 기본적으로 비활성화되어 있습니다. 자세한 내용은 [여기](https://github.com/sveltejs/svelte-hmr/tree/master/packages/svelte-hmr#preservation-of-local-state)에서 읽어볼 수 있습니다.

컴포넌트 내에서 유지해야 할 중요한 상태가 있다면, HMR에 의해 교체되지 않는 외부 스토어를 만드는 것을 고려해 보세요.

```js
// store.js
// 매우 단순한 외부 스토어 예시
import { writable } from 'svelte/store'
export default writable(0)
```
