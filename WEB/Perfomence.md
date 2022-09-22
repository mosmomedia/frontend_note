## 상호 작용 가능 시점 (TTI)

콘텐츠가 눈에 보이지만 클릭이 되지 않거나 스크롤이 더디게 움직이는 경험이 한번쯤은 있으실텐데요. 이는 브라우저의 상호 작용이 원활하지 않음을 뜻하고, 아직 TTI(Time to Interactive)에 이르지 못한 상태를 말합니다. 이 상태가 길어진다면 여행자의 체감 속도도 비례하여 떨어질 것입니다.

따라서 TTI에 도달하는 시간을 앞당겨야 합니다.

TTI (Time to Interactive): 레이아웃이 안정되고, 주요 웹 글꼴이 보이고, 메인 스레드가 사용자 입력을 처리하기에 충분한 시점

## Lazy loading

https://www.freecodecamp.org/news/how-to-lazy-load-images-in-react/

1. Lazy Loading Saves Data and Bandwidth
   Since images out of the viewport are not downloaded immediately, lazy loading conserves extra bandwidth usage. This is good for performance, especially for mobile users.

2. Lazy Loading Lowers the Cost of a CDN
   Media content services like Cloudinary or Imagekit offer paid plans for media storage. Lazy loading images ensures that only images requested from the CDN are loaded, reducing server costs.

3. Lazy Loading Improves SEO
   Page speed is a critical factor that influences SEO (and makes search engines more likely to recommend your page). Because your page load time is very low, search engines will love your site.
