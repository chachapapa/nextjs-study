# Routing Fundamentals

The skeleton of every application is routing. This page will introduce you to the fundamental concepts of routing for the web and how to handle routing in Next.js.

> 모든 어플리케이션의 뼈대는 라우팅입니다. 이 페이지에서는 웹을 위한 라우팅의 기본 개념과 Next.js에서 라우팅을 처리하는 방법을 소개합니다.

## Terminology

First, you will see these terms being used throughout the documentation. Here's a quick reference:

> 먼저, 문서 전체에서 사용되는 용어에 대한 설명입니다. 예를 들어:

![Terminology for Component Tree](https://github.com/user-attachments/assets/a768786d-c9d0-4aa4-b6fc-e50383c5aa45)


- **Tree**: A convention for visualizing a hierarchical structure. For example, a component tree with parent and children components, a folder structure, etc.
- **Subtree**: Part of a tree, starting at a new root (first) and ending at the leaves (last).
- **Root**: The first node in a tree or subtree, such as a root layout.
- **leaf**: Nodes in a subtree that have no children, such as the last segment in a URL path.

> - **트리(Tree)**: 계층 구조를 시각화하는 데 사용되는 관례입니다. 예를 들어, 부모와 자식 컴포넌트가 있는 컴포넌트 트리, 폴더 구조 등이 있습니다.
> - **서브트리(Subtree)**: 트리의 일부분으로, 새로운 루트(첫 번째)에서 시작하여 리프(마지막)에서 끝납니다.
> - **루트(Root)**: 트리 또는 서브트리에서 첫 번째 노드로, 루트 레이아웃과 같습니다.
> - **리프(Leaf)**: 자식이 없는 서브트리의 노드로, URL 경로의 마지막 세그먼트와 같습니다.

![Terminology for URL Anatomy](https://github.com/user-attachments/assets/378c9fc3-f17c-4b48-b5dd-b44874896f3a)

- **URL Segment**: Part of the URL path delimited by slashes.
- **URL Path**: Part of the URL that comes after the domain (composed of segments).

> - **URL 세그먼트(URL Segment)**: 슬래시로 구분된 URL 경로의 일부입니다.
> - **URL 경로(URL Path)**: 도메인 뒤에 오는 URL의 일부로, 세그먼트로 구성됩니다.

## [The app Router](https://nextjs.org/docs/app/building-your-application/routing#the-app-router)

In version 13, Next.js introduced a new App Router built on React Server Components, which supports shared layouts, nested routing, loading states, error handling, and more.
> Next.js의 버전 13에서는 공유 레이아웃, 중첩 라우팅, 로딩 상태, 오류 처리 등을 지원하는 React 서버 컴포넌트 기반의 새로운 앱 라우터를 도입했습니다.

The App Router works in a new directory named app. The app directory works alongside the pages directory to allow for incremental adoption. This allows you to opt some routes of your application into the new behavior while keeping other routes in the pages directory for previous behavior. If your application uses the pages directory, please also see the Pages Router documentation.
> 앱 라우터는 app이라는 새 디렉토리에서 작동합니다. app 디렉토리는 페이지 디렉토리와 함께 작동하여 점진적인 채택을 가능하게 합니다. 이를 통해 응용 프로그램의 일부 라우트를 새로운 동작으로 선택적으로 적용할 수 있으며, 다른 라우트는 이전 동작을 위해 페이지 디렉토리에 유지할 수 있습니다. 응용 프로그램이 페이지 디렉토리를 사용하는 경우, Pages Router 문서도 참조하시기 바랍니다.

**Good to know**:

The App Router takes priority over the Pages Router. Routes across directories should not resolve to the same URL path and will cause a build-time error to prevent a conflict.

> **참고사항**:
>
> 앱 라우터는 페이지 라우터보다 우선적으로 작동합니다. 디렉토리 간의 라우트가 동일한 URL 경로로 해석되지 않아야 하며, 충돌을 방지하기 위해 빌드 시 오류가 발생합니다.

![image](https://github.com/user-attachments/assets/def7d1e7-7eb2-438a-a0ca-2a7110087f7f)

By default, components inside app are React Server Components. This is a performance optimization and allows you to easily adopt them, and you can also use Client Components.

> 기본적으로 app 디렉토리 내의 컴포넌트는 React 서버 컴포넌트입니다. 이는 성능 최적화의 일환으로, 쉽게 채택할 수 있도록 해줍니다. 또한 클라이언트 컴포넌트를 사용할 수도 있습니다.

**Recommendation**: 

Check out the [Server](https://nextjs.org/docs/app/building-your-application/rendering/server-components) page if you're new to Server Components.

> **추천사항**:
>
> 서버컴포넌트에 익숙하지 않다면 [서버](https://nextjs.org/docs/app/building-your-application/rendering/server-components) 페이지를 확인해보세요.

## Roles of Folders and Files

Next.js uses a file-system based router where:

- **Folders** are used to define routes. A route is a single path of nested folders, following the file-system hierarchy from the root folder down to a final leaf folder that includes a `page.js` file. See [Defining Routes](https://nextjs.org/docs/app/building-your-application/routing/defining-routes).

- **Files** are used to create UI that is shown for a route segment. See [special files](https://nextjs.org/docs/app/building-your-application/routing#file-conventions).

> Next.js는 파일 시스템 기반의 라우터를 사용하여 다음과 같이 동작합니다:
> 
> - **폴더**는 라우트를 정의하는 데 사용됩니다. 라우트는 루트 폴더에서 시작하여 최종 리프 폴더까지 파일 시스템 계층을 따라 중첩된 폴더의 단일 경로입니다. 최종 리프 폴더에는 `page.js` 파일이 포함됩니다. 자세한 내용은 [라우트 정의](https://nextjs.org/docs/app/building-your-application/routing/defining-routes) 섹션을 참조하세요.
>
> - **파일**은 라우트 세그먼트에 표시되는 UI를 생성하는 데 사용됩니다. 자세한 내용은 [특수 파일](https://nextjs.org/docs/app/building-your-application/routing#file-conventions) 섹션을 참조하세요.

## Route Segments

Each folder in a route represents a route segment. Each route segment is mapped to a corresponding segment in a URL path.

> 각각의 경로 내 폴더는 라우트 세그먼트를 나타냅니다.각 라우트 세그먼트는 URL 내의 일치하는 세그먼트에 매핑됩니다.

![image](https://github.com/user-attachments/assets/08dd57f8-0f01-4089-b73f-4dd1ba5d5971)

## Nested Routes

To create a nested route, you can nest folders inside each other. For example, you can add a new `/dashboard/settings` route by nesting two new folders in the `app` directory.

The `/dashboard/settings` route is composed of three segments:


- `/` (Root segment)

- `dashboard` (Segment)

- `settings` (Leaf segment)

> 중첩 라우트를 생성하기 위해, 폴더내에 또다른 폴더를 중첩시킬 수 있습니다. 예를 들어, `/dashboard/settings` 경로를 만들기 위해 `app` 디렉토리에 두 개의 새로운 폴더를 중첩할 수 있습니다.
>
> `/dashboard/settings` 경로는 세 개의 세그먼트로 구성됩니다:
>
> - `/` (루트 세그먼트)
> - `dashboard` (세그먼트)
> - `setting` (리프 세그먼트)

## File Conventions

Next.js provides a set of special files to create UI with specific behavior in nested routes:

> Next.js는 중첩 라우트에서 특정 작업을 위한 UI생성을 위해 특수 파일 세트를 제공합니다:

|File|Description|
|:-----|:----------|
|`layout`| 세그먼트와 그 자식들을 위한 공유 UI|
|`page`|	경로의 고유 UI를 정의하고, 경로의 공개적인 접근 활성화|
|`loading`|	세그먼트와 그 자식들을 위한 로딩 UI|
|`not-found`|	세그먼트와 그 자식들을 위한 '페이지를 찾을 수 없음' UI|
|`error`|	세그먼트와 그 자식들을 위한 에러 UI|
|`global-error`|	전역 에러 UI|
|`route`|	서버 측 API 엔드포인트|
|`template`|	리렌더링을 위한 레이아웃 UI|
|`default`|	병렬 라우트의 기본 UI|

**Good to know**: 

`.js`, `.jsx`, or `.tsx` file extensions can be used for special files.

> **참고사항**:
>
> `.js`, `.jsx`, 또는 `.tsx` 파일 확장자를 특수 파일에 사용할 수 있습니다.

## Component Hierarchy
The React components defined in special files of a route segment are rendered in a specific hierarchy:

> 라우트 세그먼트의 특수 파일에 정의된 React 컴포넌트들은 특정한 계층 구조를 바탕으로 렌더링됩니다:

- `layout.js`
- `template.js`
- `error.js` (React error boundary)
- `loading.js` (React suspense boundary)
- `not-found.js` (React error boundary)
- `page.js` or nested `layout.js`

![image](https://github.com/user-attachments/assets/13e89b76-c5ba-4a63-ac75-0880b1a76af3)

In a nested route, the components of a segment will be nested inside the components of its parent segment.

> 중첩라우트에서는, 세그먼트의 컴포넌트들이 부모 세그먼트의 컴포넌트 내부에 중첩됩니다.

![image](https://github.com/user-attachments/assets/20ea5d75-f562-4cfe-98d3-3dd9b83843da)

## Colocation
In addition to special files, you have the option to colocate your own files (e.g. components, styles, tests, etc) inside folders in the `app` directory.

This is because while folders define routes, only the contents returned by `page.js` or `route.js` are publicly addressable.

> 특수 파일 외에도, `app` 디렉토리 내의 폴더에 자신의 파일(예: 컴포넌트, 스타일, 테스트 등)을 함께 둘 수 있습니다.
>
> 이는 폴더가 라우트를 정의하지만, `page.js` 또는 `route.js`에서 반환되는 내용만 공개적으로 접근할 수 있기 때문입니다.

![image](https://github.com/user-attachments/assets/01fb5847-c811-4211-9fc0-ca6090e6b0fb)

Learn more about [Project Organization and Colocation](https://nextjs.org/docs/app/building-your-application/routing/colocation).

>  [Project Organization and Colocation](https://nextjs.org/docs/app/building-your-application/routing/colocation) 에 대해 더 학습해 보세요.

## Advanced Routing Patterns
The App Router also provides a set of conventions to help you implement more advanced routing patterns. These include:

- [Parallel Routes](https://nextjs.org/docs/app/building-your-application/routing/parallel-routes): Allow you to simultaneously show two or more pages in the same view that can be navigated independently. You can use them for split views that have their own sub-navigation. E.g. Dashboards.
- [Intercepting Routes](https://nextjs.org/docs/app/building-your-application/routing/intercepting-routes): Allow you to intercept a route and show it in the context of another route. You can use these when keeping the context for the current page is important. E.g. Seeing all tasks while editing one task or expanding a photo in a feed.

These patterns allow you to build richer and more complex UIs, democratizing features that were historically complex for small teams and individual developers to implement.

>App Router는 더 발전된 라우팅 패턴을 구현하는 데 도움이 되는 일련의 규칙도 제공합니다. 이에는 다음과 같은 패턴들이 포함됩니다:
>
> - [병렬 라우트](https://nextjs.org/docs/app/building-your-application/routing/parallel-routes): 하나의 뷰에서 동시에 두 개 이상의 페이지를 표시할 수 있으며, 이들은 독립적으로 탐색할 수 있습니다. 이는 각각 자체 하위 탐색을 가진 분할 뷰(예: 대시보드)에 사용할 수 있습니다.
>
> - [라우트 중간 처리](https://nextjs.org/docs/app/building-your-application/routing/intercepting-routes): 특정 라우트를 가로채고 다른 라우트의 맥락에서 표시할 수 있습니다. 이는 현재 페이지의 컨텍스트를 유지하는 것이 중요할 때 유용합니다. 예를 들어, 한 작업을 편집하는 동안 모든 작업을 볼 수 있는 상황이거나, 피드에서 사진을 확대하는 경우 등에 사용할 수 있습니다.
>
>이러한 패턴들은 보다 풍부하고 복잡한 UI를 구축할 수 있도록 도와주며, 이전에는 작은 팀이나 개발자 개인이 구현하기 어려웠던 기능들을 더 쉽게 구현할 수 있도록 합니다.
