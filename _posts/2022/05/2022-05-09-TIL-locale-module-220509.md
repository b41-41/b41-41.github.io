---
layout: post
title: "react-intl, next-i18next, next-compose-plugins"
categories: TIL Next Locale
---

## 웹 사이트, 프로그램 다중언어 지원하기

### 들어가기

- 다중언어를 지원하는 프로젝트를 진행하기 위해서 방법을 생각하고 있었다.
- 전역 상태로 locale 값을 받고 locale에 따라 서로 다른 상수를 출력하려고 생각을 하고 있었다.
- 그런데 컴퓨터나 스마트폰의 언어에 따라서 자동으로 locale를 변경하도록 구현하는 부분이 시간이 오래 걸릴 것 같았다.
- 그래서 라이브러리를 찾아 보았다.

### 다중언어 로케일 라이브러리

- [React-intl](https://www.npmjs.com/package/react-intl)
- [next-i18next](https://github.com/isaachinman/next-i18next)

- 위 두가지가 좀 유명한 것 같다.
- react-intl이 유명한데 숫자, 날짜, 포맷팅까지 로케일을 지원해서 편리한 것 같다.
- next-i18next는 Next.js의 SSR의 경우에도 로케일을 잡아주어 Next.js와 함께 쓸 때 좋은 것 같았다.
- 따라서 next-i18next 라이브러리를 사용하기로 했다.

### next-i18next

#### 설치

1. `yarn add next-i18next`로 설치
2. public - locales - 원하는 언어 (en) - common.json
   - 원하는 언어 폴더 만들고 그 아래 원하는 메뉴를 JSON파일로 만든다.
3. 프로젝트 세팅

   1. next-i18next.config.js

   ```
       module.exports = {
   i18n: {
       defaultLocale: 'en',
       locales: ['en', 'ko'],
   },
   };
   ```

   2. next.config.js

   ```
   const { i18n } = require('./next-i18next.config');

   module.exports = {
   i18n,
   };
   ```

   - 이렇게 하면 되는데 기존에 사용하는 모듈이 이미 있어서 `next-compose-plugins`을 사용해서 두 모듈을 하나로 합쳐줬다.
   - 아래처럼

   ```
   const withPlugins = require('next-compose-plugins');

   const withBundleAnalyzer = require('@next/bundle-analyzer')({
       enabled: process.env.ANALYZE === 'true',
   });

   const { i18n } = require('./next-i18next.config');

   module.exports = withPlugins([withBundleAnalyzer], { i18n });
   ```

   - withPlugins([])의 배열 안이 아니라 2번째 인자로 `i18n`을 넣어야한다.
   - 나는 이것 때문에 1시간을 헤맸다.

4. `_app` 파일에 appWithTranslation 추가


    ```
    import { appWithTranslation } from 'next-i18next';

    const MyApp = ({ Component, pageProps }) => <Component {...pageProps} />;

    export default appWithTranslation(MyApp);
    ```

4. serverSideTranslations 추가


    ```
    import { serverSideTranslations } from 'next-i18next/serverSideTranslations';

    export async function getStaticProps({ locale }) {
    return {
        props: {
        ...(await serverSideTranslations(locale, ['common', 'footer'])),
        // Will be passed to the page component as props
        },
    };
    }
    ```
    - [`getStaticProps`](https://b41-41.github.io/posts/TIL_next_getStaticProps/)라고 정적 페이지에 비동기 데이터를 받을 때 사용하는 것인데 대충 page의 `index.ts` 파일에 적용하면 내 프로젝트의 경우 Layout만 삽입되어 있기 때문에 전체 적용되고, 그래서 거기에 집어 넣음.

5. 사용하기 (`useTranslation`)


    ```
    import { useTranslation } from 'next-i18next';

    export const Footer = () => {
    const { t } = useTranslation('footer');

    return (
        <footer>
        <p>{t('description')}</p>
        </footer>
    );
    };
    ```
    - t를 사용함 괄호 안에 string으로 해당 값을 넣어주면 로케일에 맞게 출력 됨.

## Reference

- [https://www.npmjs.com/package/react-intl](https://www.npmjs.com/package/react-intl)
- [https://myeongjae.kim/blog/2020/04/12/react-internationalization-libraries-comparison](https://myeongjae.kim/blog/2020/04/12/react-internationalization-libraries-comparison)
- [https://github.com/isaachinman/next-i18next](https://github.com/isaachinman/next-i18next)
