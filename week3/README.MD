# 필수과제

1. ListView 최소 1개 이상 활용해보기
2. Switch(Checkbox, RadioButton 등등)가 리스트 아래로 드래그 되었을때 풀리는 현상 해결해보기
3. CRUD (생성, 읽기, 수정, 삭제) 구현해오기
4. RecyclerView의 뷰홀더에 대해서 한번 더 알아보기
5. RecyclerView 최소 1개 이상 활용해보기
6. status바 색상 변경

# 챌린지 과제

1. RecyclerView 커스텀 해보기
    1. Drag and Drop
    2. LongClickListener
    3. Filter
    4. Swipe
    
    등등 여러가지가 있는데 본인의 과제 기획에 맞는 기능을 골라서 구현해보시면 됩니다
    
2. Header, Footer 구현해보기
3. 리사이클러뷰 layout manager 조사해보기

# 구현

![크림2.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f2130da7-ed8d-40bd-ab02-5f7e8ff2ba49/크림2.jpg)

![크림3.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e88b389a-c7aa-4b71-a258-addba2af5971/크림3.jpg)

- status bar 색상 검정색
- 상단 광고바 → Recycleviwe 로 구현(가로)
- 상품 아이콘 → Recycleviwe 로 구현(가로)

![크림4.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/46621b10-986d-41e5-ab9d-b5ebe6aa8b29/크림4.jpg)

- 리스트뷰로 구현

![크림1.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6530e6e4-e082-4eed-9114-02294ccb21b1/크림1.jpg)

- “전체” 텍스트뷰 클릭시 구매내역을 볼수있는 액티비티로 이동

![크림5.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/81e64f54-b3a1-4a9f-864c-863824c71924/크림5.jpg)

![크림6.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4dba5d45-8391-49c7-946b-eafe098ea299/크림6.jpg)

- 구매목록 Recycleview 로 구현
- 뷰 클릭시 삭제되면서 모델명과 구매내역에서 삭제되었습니다 라는 메시지가 뜸
- 스와이프 기능을 통해 삭제 버튼을 만들고싶었지만 구현하지못함

## Switch(Checkbox, RadioButton 등등)가 리스트 아래로 드래그 되었을때 풀리는 현상

→ 이러한 이유가 생기는 이유는 자원을 아끼기 위한 리스트뷰의 재사용 문제 때문이다  

예를들어 리스트뷰에 100개의 아이템이 수직으로 있고, 한 화면에 10개가 나온다면 리스트뷰는 한번에 100개             를 다 로딩시켜놓는게 아니라 몇개정도만 로딩시켜놓고, 스크롤시 이전것들을 삭제하고 그 다음 부분을 로딩 시키는 방식을 가지고있기 때문이다.

# VIewHolder 를 사용하는 이유

listView 사용당시에는 ViewHolder라는 개념이 없었고 그냥 뷰를 inflate해서 사용했다. 이 경우 문제가 있었는데 "레이아웃의 각 요소를 가져오려면 일일히 findViewById를 해줘야했다."

view의 세부정보를 담고 있는 Viewholder라는 개념을 도입해서 매번 findviewbyid를 해주지 않아도 세부 view를 가져올 수 있게 하였다.

[https://jinsangjin.tistory.com/24](https://jinsangjin.tistory.com/24)
