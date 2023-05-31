# BLOG

Link : https://blog-harry.vercel.app/

<img width="1280" alt="스크린샷 2023-05-31 오후 5 17 21" src="https://github.com/sksskdf/BLOG-toyproject/assets/78300703/400e9289-5bf0-4e12-87c5-00064a0ebf09">
<img width="1280" alt="스크린샷 2023-05-31 오후 5 17 31" src="https://github.com/sksskdf/BLOG-toyproject/assets/78300703/a5711661-12f0-4e6c-bf7b-9107bb239612">
<img width="1280" alt="스크린샷 2023-05-31 오후 5 17 34" src="https://github.com/sksskdf/BLOG-toyproject/assets/78300703/88b1025b-ea26-477b-b15e-5fd7a62cf4a3">

-------

### 사용 기술 스택
NextJS
    
------
  
### 기능
#### 블로그 포스트 불러오기
파일시스템의 /posts 경로에 있는 md파일들을 /lib/posts.js 파일에서 읽어 객체로 파싱한 뒤 블로그포스트와 관련된 정보들을 불러오는 함수들을 export 합니다.

#### 메인화면
블로그 주인과 관련된 정보와 export한 /lib/posts.js 파일의 함수를 이용하여 포스트 정보들을 불러온 뒤 
        
        <ul className={utilStyles.list}>
          {allPostsData.map(({ id, date, title }) => (
            <li className={utilStyles.listItem} key={id}>
              <Link href={`/posts/${id}`}>{title}</Link>
              <br />
              <small className={utilStyles.lightText}>
                <Date dateString={date} />
              </small>
            </li>
          ))}
        </ul>
      
위 코드에서 보는 것 처럼 map함수를 이용해서 li를 만듭니다.
li는 해당 포스트 상세보기로 이동하는 Link를 포함합니다.

#### 포스트 상세보기
Next.js 에선 파일시스템의 /pages를 루트로 한 디렉토리 패스가 라우팅 주소와 매칭됩니다.
이를 이용해 /pages/posts/[id].js 파일에서 포스트 상세보기 화면을 구현합니다. (파일내부에서 파일제목인 [id]를 통해 매개변수화된 라우팅주소를 인자로 받습니다.)
해당 id를 통해 포스트정보를 불러온 뒤 

    <Layout>
      <Head>
        <title>{postData.title}</title>
      </Head>
      <article>
        <h1 className={utilStyles.headingXl}>{postData.title}</h1>
        <div className={utilStyles.lightText}>
          <Date dateString={postData.date} />
        </div>
        <br />
        <div dangerouslySetInnerHTML={{ __html: postData.contentHtml }} />
      </article>
    </Layout>

위 코드와 같이 포스트 정보를 출력합니다.

### Next.js 를 사용해 본 소감
