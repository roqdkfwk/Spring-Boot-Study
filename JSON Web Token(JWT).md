# JSON Web Token(JWT)

- JWT 토큰 생성 메소드
    
    ```java
    .builder() : JWT를 만들 수 있는 빌더 인스턴스로 만든다.
    
    .header() : 빌더 헤더 객체로 만든다.
    
    .add("key" : "value") : key와 value 형태로 추가한다.
    
    .add(map) : map 객체의 형태로 추가한다.
    
    .setIssuedAt(new Date(currentTime)) : 현재 시각을 기준으로 토큰 발급 시간을 설정한다.
    
    .setExpiration(new Date(currentTime + 1000))
     : 현재 시각을 기준으로 1초 후로 토큰의 만료 시간을 설정한다
     
    .signWith(SignatureAlgorithm.HS256, jwtKey.getBytes(StandardCharsets.UTF_8))
     : HS256 알고리즘을 사용하여 토큰에 서명한다.
    ```