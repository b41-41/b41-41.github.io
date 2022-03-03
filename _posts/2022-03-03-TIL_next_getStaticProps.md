---
layout: post
title: "Next.js - getStaticProps 정적 페이지 생성"
categories: TIL Next.js
---

# 정적 페이지 만들기

- Next.js 프레임워크에서는 3가지 렌더링 방식이 있다.
  1. 정적 생성
  2. SSR
  3. CSR
- 일반적으로 Next.js에서 데이터를 가져오는 메서드 없이 컴포넌트를 만들면 정적 페이지가 생성된다.
- 하지만 데이터를 가져와야 하는 경우 `getStaticProps`, `getStaticPaths`를 사용해야 한다.
- 나의 경우 코드 리펙터링을 할 때 데이터를 가져와야 했으므로 `getStaticProps`나 `getStaticPaths` 둘 중에서 하나를 사용해야 했는데 `getStaticProps`를 사용했다.

# `getStaticProps`와 `getStaticPaths`

## `getStaticProps`

- 빌드 시 값이 고정되어 빌드 이후에는 수정이 불가능하다.

## `getStaticPaths`

- 동적 라우팅과 getStaticProps를 동시에 원할 때 사용한다.

# `getStaticProps` 사용하기

- 리펙터링을 하는 부분 안에서 따로 라우팅을 다시 사용하는 일이 없어서 `getStaticProps`를 사용했다.
- 먼저 기존에는 API 값을 아래와 같이 가져왔었다.

```TypeScript
import { get } from 'apis/requestAPIs/contacts';
const Contacts = () => {

   const [contactType, setContactType] = useState<ContactType[]>([]);
   const [qaPurchase, setQaPurchase] = useState<QaItems[]>([]);
   const [qaSale, setQaSale] = useState<QaItems[]>([]);

     useEffect(() => {
     get
       .ContactType()
       .then(res => setContactType(res.qaTypes))
       .catch(e => console.error(e));
     get
       .QaPurchase()
       .then(res => setQaPurchase(res.qas))
       .catch(e => console.error(e));
     get
       .QaSale()
       .then(res => setQaSale(res.qas))
       .catch(e => console.error(e));
   }, []);

}

export default Contacts
```

- `getStaticProps`를 사용하기 위해서 공식 문서에 있는 것처럼 최하단에 다음과 같이 추가한다.

```TypeScript
export async function getStaticProps() {

    const contactType = await get.ContactType();
    const qaPurchase = await get.QaPurchase();
    const qaSale = await get.QaSale();

    return {
        props: {
            contactType: contactType.qaTypes,
            qaPurchase: qaPurchase.qas,
            qaSale: qaSale.qas,
        }
    }
}
```

- `getStaticProps`에서 props로 반환을 했을 때 그 값들을 바로 컴포넌트에서 불러올 수 있다.

```TypeScript
const Contacts = ({ contactType, qaPurchase, qaSale }: ContactsAPIType) => {
}
```

- 이렇게 불러와서 사용하면 된다.
- 정적 페이지 처리는 Next.js가 알아서 해준다.

## Reference

https://nextjs.org/docs/basic-features/data-fetching/get-static-props

https://velog.io/@devstone/Next.js-100-활용하기-feat.-initialProps-webpack-storybook
