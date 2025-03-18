<aside>
✅ 
저희 웹 사이트는 다양한 상품 리뷰를 한 곳에서 모아서 제공하는 플랫폼입니다. 많은 사람들이 상품을 구매하기 전에 다른 사람들의 경험과 의견을 참고하고 싶어하지만, 이를 위해서는 여러 웹 사이트를 돌아다니며 정보를 수집해야 합니다. 이러한 불편함을 해결하기 위해 저희는 한 번에 다양한 상품 리뷰를 확인할 수 있는 편리한 웹 사이트를 개발했습니다.

</aside>

### 1주차

2주차에 2~3명으로 이루워진 조 구성

캡스톤 3월 21일 주제발표.

---

주제.

웹, 앱, 게임 

→ 앱 - 나이별 축의금 및 조의금 평균 금액 (빅데이터)

→ 웹 - OOO 추천 사이트 

→ 웹,앱 - 세대별 브랜드 선호 순위 (빅데이터)

→ 앱 - 평균 기름값 및 반경 몇km 이내 제일 저렴한 주유소 알려주기

- 온라인 쇼핑몰에서 상품을 구매하기 전에, 다른 사용자들의 리뷰를 확인하는 경우가 많지만 
다양한 리뷰를 확인을 하는 것을 어려워서 생각하게 됨.

→ 앱 - 초단기예측 앱 ( 비올지 안올지 알려주는 앱 )

---

## 쇼핑몰 리뷰 분석 앱 및 웹사이트

- 사용자들이 입력한 리뷰를 자연어 처리 기술을 활용하여 분석하여, 상품에 대한 종합적인 평가를 제공하는 앱

- [ ]  데이터 수집 모듈 - 작업중

<aside>
💡 사용자가 입력한 쇼핑몰 리뷰 데이터를 수집하고, 데이터베이스에 저장하는 모듈
이를위해 웹 크롤링 기술을 활용하여 쇼핑몰 리뷰 데이터를 자동으로 수집.

</aside>

- [ ]  자연어 처리 모듈 - 대기

<aside>
💡

수집한 데이터를 자연어 처리 기술을 활용하여 분석하는 분석 모듈이 필요함
자연어 처리 라이브러리, API등을 활용하여 처리할 수 있음
자연어 처리 모듈은 감성 분석 키워드 추출 등 다양한 분석이 가능함.분석 결과 제공 모듈

</aside>

<aside>
💡 자연어 처리 결과를 시각적으로 제공해주는 모듈이 필요함.
웹 혹은 앱을 개발하여 사용자에게 분석 결과를 제공할 수 있어야함.

</aside>

- [ ]  기타 기능 모듈

<aside>
💡 검색 기능, 필터링 기능, 사용자 리뷰 작성 기능 등 다양한 기타 모듈의 탑재를 고려 중

</aside>

쇼핑몰 리뷰 데이터를 입력하면 데이터 수집 모듈이 이를 수집하여 데이터베이스에 저장함.

자연어 처리 모듈이 저장된 데이터를 분석하여 감성 분석 결과와 키워드 추출 결과를 생성.

분석 결과를 시각적으로 사용자에게 제공.

---

1. 비슷한 앱이나 웹이 있는지.
있으면 참고해서 좀 더 새롭게 갈수있는 방향성을 확인해보기.
2. 같은 이름을 가진 상품이 있을경우 여러가지를 보여주기
3. 리뷰에서 비속어 및 여러가지 리뷰가 있을때 필터링이 되도록 db 쿼리 짜기

---

웹 크롤링은 구글 

[참고사이트](https://m.blog.naver.com/21ahn/221329219163) 

만약 웹 크롤링 작업을 하려면 node.js 를 사용하여 웹 크롤링 하는것이 좋아보임.

가급적 node.js를 사용하여 서버에서 크롤링 후 db에 넣은다음 뿌리는걸 생각해야 할 것 같음.

---

### 3월 27일 발표

- [x]  이름
- [x]  개발목적 (사유)
- [x]  어떤식으로 개발
- [x]  단계별로 작업진행도

---

```jsx
const axios = require('axios');
const cheerio = require('cheerio');

const url = 'https://example.com';

axios.get(url)
  .then(response => {
    const $ = cheerio.load(response.data);
    
    // 원하는 데이터를 추출하는 코드 작성
    const title = $('title').text();
    
    console.log(title);
  })
  .catch(error => {
    console.log(error);
  });
```

위 코드를 사용하여 정보를 가져오는데에는 성공하였으나, 

원하는 정보를 가져오지 못했기 때문에 해당 부분을 가져오는 코드로 보완 해야함.

---

```jsx
const puppeteer = require('puppeteer');

(async () => {
  const browser = await puppeteer.launch();
  const page = await browser.newPage();

  await page.goto('https://smartstore.naver.com/gksmf0227/products/5482492529?NaPm=ct%3Dlg4r76p4%7Cci%3D51996703ed42a56e4ac36f173c838d117aea6b73%7Ctr%3Dslcc%7Csn%3D3185338%7Chk%3D4b840611adbecee671b3cda04db34505f8c519fe');
  
  const selector = '#REVIEW > div > div._180GG7_7yx > div.cv6id6JEkg > ul > li:nth-child(1) > div > div > div > div._1XNnRviOK8 > div > div._1YShY6EQ56 > div._19SE1Dnqkf > div > span._3QDEeS6NLn';
  
  await page.waitForSelector(selector);

  const data = await page.$eval(selector, element => element.textContent);
  
  console.log(data);

  await browser.close();
})();
```

위 코드를 사용하여 리뷰 하나를 긁어오는데에 성공함. 
다음 순서는 이제 그 사이트에 있는 모든 리뷰 긁어오기

밑에는 코드 실행 결과▼

<aside>
💡 주문하고 주말지나고 바로 도착했어요. 오자마자 꺼내 먹었는데 맛은 완전 맛있었는데 살짝 딱딱한(?)감이 있어서 하루정도 상온 보관해 먹으면 완전 맛있을꺼 같았어요~~후숙된거보단 훨씬 좋아 굿입니다!
각자 하나씩 통으로 들고 뚝딱 맛있게 먹었답니다. 크기도 여러가지라 더 좋아요~^^

작년에 이어 3번째 주문했는데 역시 후회없습니다. 시장보다 더 싸고 강추강추합니당~^^

</aside>

---

```jsx
const puppeteer = require('puppeteer');

(async () => {
  const browser = await puppeteer.launch();
  const page = await browser.newPage();

  //url
  await page.goto('https://smartstore.naver.com/75st_melon/products/4868037144?NaPm=ct%3Dlgah2rts%7Cci%3Dde5714f6edbc985b8b402d48e5c9814a4418acf1%7Ctr%3Dslcc%7Csn%3D1149995%7Chk%3De90682363a3288adde9b1d8138ad09c51808909c')  
  var count = 1;

  //CSS 셀렉터
  const reviewSelector = '#REVIEW > div > div._180GG7_7yx > div.cv6id6JEkg > ul > li';
  const pageSelector = '#REVIEW > div > div._180GG7_7yx > div.cv6id6JEkg > div > div > a.fAUKm1ewwo._2Ar8-aEUTq';

  //로딩중...
  await page.waitForSelector(reviewSelector);
  const clickButton = await page.waitForSelector(pageSelector,el => el.getAttribute('aria-hidden'));

  //최초 항목별 카운트
  const reviewCount = await page.$$eval(reviewSelector, elements => elements.length);

  //데이터 파싱
  while(clickButton)
  {
    await page.waitForSelector(pageSelector);
    try{
      await page.click(pageSelector);
    }catch
    {
      break;
    }
    await page.waitForSelector(reviewSelector);
    for (let i = 1; i <= 6; i++) {
      try{
      const reviewItemSelector = `${reviewSelector}:nth-child(${i}) > div > div > div > div._1XNnRviOK8 > div > div._1YShY6EQ56 > div._19SE1Dnqkf > div > span._3QDEeS6NLn`;
      await page.waitForTimeout(25)
      const data = await page.$eval(reviewItemSelector, element => element.textContent.trim());
      await page.waitForTimeout(25)
      console.log(count+ ". " + data);
      count=count+1;
      }
      catch
      {
        break;
      }
    }
  }

  await browser.close();
})();
```

위 코드로 네이버 스마트스토어의 한 상품의 모든 리뷰를  긁어오는데에 성공함

---

---

웹페이지 솔루션 그누보드 사용할지 워드프레스 사용할지 고민중.

버추얼 호스트를 사용해서 도메인 연결할 예정. ( 알아두면 좋음 ) 

---


WBS + 구현도로 메인은 어떤지, 관리자페이지는 어떻게 되는지,
즉. 사용자가 어떤식으로 사용할 예정인지. 설명 혹은 부가적인 이미지를 추가하여 발표를 해야한다. 라고 조언을 해주심.

---

apache 명령어 

```bash
setenforce 0
service httpd start
```

웹서버 구축 완료 네트워크 설정만 하면 됨. 
현재는 내부 인터넷에서만 사용가능 함.

---

```jsx
const puppeteer = require('puppeteer');
const sql = require('mysql');
const fs = require('fs');

const sqlReviews = sql.createConnection({
  port : "????",
  host : "????",
  user : "????",
  password : "????",
  database : "????",
  charset: '????'
})

sqlReviews.connect((err)=>{
  if(err) throw err;
})

const columnsIn = "INSERT INTO smartstore (Name, Date, Rate, Content) VALUES ?";

const reviews = [];

(async () => {
  const browser = await puppeteer.launch({headless:true});
  const page = await browser.newPage();
  //url
  await page.goto('https://smartstore.naver.com/sutomarket/products/6711646317?n_media=11068&n_rank=3&n_ad_group=grp-a001-02-000000023041568&n_ad=nad-a001-02-000000221671263&n_campaign_type=2&n_mall_id=newbuan15&n_mall_pid=6711646317&n_ad_group_type=2&NaPm=ct%3Dlie1gwoo%7Cci%3D0yG0002VolzyGl8hh1ma%7Ctr%3Dpla%7Chk%3D928f8d392b58509aa968262d4b9cc1d2f9a97de3')  

  //스크롤 다 내리기
  let lastHeight = await page.evaluate("document.body.scrollHeight");
  while (true) {
    await page.evaluate("window.scrollTo(0, document.body.scrollHeight)");
    await page.waitForTimeout(2000); 
    let newHeight = await page.evaluate("document.body.scrollHeight");
    if (newHeight === lastHeight) {
      break;
    }
    lastHeight = newHeight;
  }
  
  //사진 로딩 건너뛰기
  await page.setRequestInterception(true);
  page.on('request', (req) => {
    if(req.resourceType() == 'image')
    {
      req.abort();
    }
    else
    {
      req.continue();
    }
  });

  //CSS 셀렉터
  const reviewSelector = '#REVIEW > div > div._180GG7_7yx > div.cv6id6JEkg > ul > li'; //리뷰
  const pageSelector = '#REVIEW > div > div._180GG7_7yx > div.cv6id6JEkg > div > div > a.fAUKm1ewwo._2Ar8-aEUTq'; // 리뷰의 다음 버튼을 누르기 위한 버튼
  const areaSelector = '#_productFloatingTab > div > div._27jmWaPaKy._1dDHKD1iiX > ul > li';

  //로딩중...
  await page.click(`${areaSelector}:nth-child(${2}) > a > span`);
  await page.waitForSelector(reviewSelector);
  const clickButton = await page.waitForSelector(pageSelector,el => el.getAttribute('aria-hidden'));
  

  //최초 항목별 카운트
  const reviewCount = await page.$$eval(reviewSelector, elements => elements.length);

  //데이터 파싱
  while(clickButton)
  {
    await page.waitForSelector(pageSelector);
    try{
      await page.click(pageSelector);
    }catch
    {
      break;
    }
    await page.waitForSelector(reviewSelector);
    for (let i = 1; i <= reviewCount; i++) {
      try{
      //각 데이터의 대한 주소
      const [contentItemSelector, rateItemSelector, nameItemSelector, dateItemSelector] = await Promise.all([
        `${reviewSelector}:nth-child(${i}) > div > div > div > div._1XNnRviOK8 > div > div._1YShY6EQ56 > div._19SE1Dnqkf > div > span._3QDEeS6NLn`,
        `${reviewSelector}:nth-child(${i}) > div > div._30o7PGmsIy > div > div._1XNnRviOK8 > div > div._1YShY6EQ56 > div._1rZLm75kLm > div._37TlmH3OaI > div._2V6vMO_iLm > em._15NU42F3kT`,
        `${reviewSelector}:nth-child(${i}) > div > div > div > div._1XNnRviOK8 > div > div._1YShY6EQ56 > div._1rZLm75kLm > div._37TlmH3OaI > div._2FmJXrTVEX > strong`,
        `${reviewSelector}:nth-child(${i}) > div > div > div > div._1XNnRviOK8 > div > div._1YShY6EQ56 > div._1rZLm75kLm > div._37TlmH3OaI > div._2FmJXrTVEX > span`
      ])
      await page.waitForTimeout(10)
      const [namedata, contentdata, ratedata, datedata] = await Promise.all([
      page.$eval(nameItemSelector, element => element.textContent.trim()),
      page.$eval(contentItemSelector, element => element.textContent.trim()),
      page.$eval(rateItemSelector, element => element.textContent.trim()),
      page.$eval(dateItemSelector, element => element.textContent.trim())
      ])
      await page.waitForTimeout(10)
      const data = [namedata,datedata,ratedata,contentdata];
      await page.waitForTimeout(10)
      reviews.push(data);
      }
      catch
      {
        break;
      }
    }
  }
  //파일명
  var file = 'smartstore.json'
 // 파일생성
  fs.open(file,'w',function(err,fd){
    if(err) throw err;
  })
  //파일쓰기
  fs.writeFileSync(file, JSON.stringify(reviews));

//데이터베이스 컬럼 입력
  sqlReviews.query(columnsIn,[reviews],(err)=>{
        if(err) throw err;
        sqlReviews.query("SELECT * FROM smartstore",(err,results,fields) =>{
          console.log("err : ",err);
          console.log("results : ", results);
          console.log("fields : ", fields);
        });
      });

  await browser.close();
})();
```

### [node.js request 관련모듈 링크](https://mainia.tistory.com/5724)

https://opentutorials.org/course/3332/21032

---

## 사용한 개발 도구

리눅스(CentOS7), MySql, Node.js, php. html&css, js
