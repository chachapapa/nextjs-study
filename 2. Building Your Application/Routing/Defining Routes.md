# Defining Routes

💡이 페이지를 읽기 전에 [Routing Fundamentals](https://github.com/chachapapa/nextjs-study/blob/main/2.%20Building%20Your%20Application/Routing/Routing-Fundamentals.md) 페이지를 먼저 학습하는 것을 추천합니다.

This page will guide you through how to define and organize routes in your Next.js application.

> 이 페이지에서는 Next.js 어플리케이션에서 라우트를 정의하고 관리하는 방법에 대해 설명하겠습니다.

## Creating Routes

Next.js uses a file-system based router where folders are used to define routes.

Each folder represents a route segment that maps to a URL segment. To create a nested route, you can nest folders inside each other.

> Next.js 는 폴더를 라우트를 정의하기 위해 사용하는 파일시스템 기반 라우터를 사용합니다.
>
> 각각의 폴더는 URL 세그먼트에 매핑되는 라우트 세그먼트를 나타냅니다. 중첩 라우트를 사용하기 위해서는, 폴더 내부에 또다른 폴더를 생성해야합니다.

![image](https://github.com/user-attachments/assets/af2da7f2-c182-49ab-b6eb-8752a93ac478)

A special `page.js` file is used to make route segments publicly accessible.

> 특수 파일인 `page.js`는 라우트 세그먼트를 공개적으로 접근할 수 있게 만드는 파일입니다.

![image](https://github.com/user-attachments/assets/3d82a208-895d-48e9-8163-232c326f5574)

In this example, the `/dashboard/analytics` URL path is not publicly accessible because it does not have a corresponding `page.js` file. This folder could be used to store components, stylesheets, images, or other colocated files.

> 위 예시에서는, `/dashboard/analytics` URL 경로가 내부에 `page.js` 파일이 없기 때문에 접근이 불가능합니다. 이 폴더는 컴포넌트, 스타일시트, 이미지 등의 파일을 저장하는데에 사용될 수 있습니다.

 💡**Good to know**: `.js`, `.jsx`, or `.tsx` file extensions can be used for special files.

> 💡**참고사항**: `.js`, `.jsx`, 또는 `.tsx` 확장자가 특수 파일에 사용될 수 있습니다.

## Creating UI

Special file conventions are used to create UI for each route segment. The most common are pages to show UI unique to a route, and layouts to show UI that is shared across multiple routes.

For example, to create your first page, add a `page.js` file inside the `app` directory and export a React component:

> 각각의 라우트 세그먼트의 UI를 제작하기 위해 특수 파일 컨벤션이 사용됩니다. 가장 흔히 사용되는 파일로는 라우트에 일치하는 고유의 UI를 위한 pages, 복수의 라우트에서 공유되는 UI를 위한 layouts 가 있습니다.
>
> 예를 들어, 첫번째 페이지를 생성하기 위해서는, `app` 디렉토리 내에 `page.js`파일을 추가하고 리액트 컴포넌트를 export 해야합니다.

```tsx
export default function Page() {
  return <h1>Hello, Next.js!</h1>
}
```


