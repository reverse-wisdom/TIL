> ### CSS Grid 핵심정리(2)
>
> 링크참조: https://studiomeal.com/archives/533

- **minmax 함수**

  - minmax(100px, auto) -> 최소한 100px, 최대는 자동으로 맞춤, 아무리 내용이 적더라도 최소한의 높이는 100px 로 맞춰야하며, 콘텐츠 양이 많으면 100px이 넘어가면 알아서 늘어나도록 처리

  - 사용예시

    ```css
    .grid-container {
        grid-template-colums: repeat(3,1fr);
        grid-template-rows: repeat(3, minmax(100px. auto));
    }
    ```

- **auto-fill 과 auto-fit**

  - auto-fil, auto-fit column의 개수를 미리 정하지 않고 설정된 너비가 허용하는 한 최대한 셀을 채움

  - 사용예시

    - 아이템이 10개면 알아서 한 줄에  5개씩 2 줄로 배치됨
    - 아이템이 4개면 20%할당후 마지막 20%영역만큼 비워짐

    ```html
    .grid-container {
    	grid-templates-columns:repaet(auto-fill, minmax(20%, auto))
    }
    
    ```

    - 비워진걸 채워주는 기능이 바로 **auto-fit**
    - 비워진 곳 없이 알아서 채워줌

    ```html
    .grid-container {
    	grid-templates-columns:repaet(auto-fit, minmax(20%, auto))
    }
    ```

    

    

