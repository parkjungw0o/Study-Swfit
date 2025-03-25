# Access Token & Refresh Token
### 로그인 요청
1. 사용자 아이디, 비밀번호를 서버로 전송 
2. 사용자 인증에 성공하면 Access Token과 Refresh Token을 발급
3. 인증 실패 시 에러 메시지를 반환

### Access Token 
- 클라인트가 인증된 사용자임를 나타냄
- 사용 기간이 짧음
- API 요청 시 Authorization 헤더에 추가되어 사용

```swift
 //almofire
 let headers: HTTPHeaders = [
            "Authorization": "Bearer \(accessToken)"
         ]
```
### Refresh Token 
- Access Token이 만료되었을 때 새로운 Access Token을 받기 위한 토큰
- 사용 기간이 더 길며 (7일 ~ 30일), 서버에 저장되기도 함
- ⚠️ Refresh Token은 민감하므로 재발급 요청 외의 목적으로 사용되지 않음
```swift
func refreshAccessToken(completion: @escaping (Bool) -> Void) {
    guard let refreshToken = UserSessionManager.shared.getRefreshToken() else {
        completion(false) // Refresh Token이 없으면 실패
        return
    }
    
    let url = "https://gsm/user/retoken"
    let headers: HTTPHeaders = [
        "Authorization": "Bearer \(refreshToken)"
    ]
    
    AF.request(url, method: .post, headers: headers)
        .responseDecodable(of: LoginResponse.self) { response in
            switch response.result {
            
            //로그인에 성공하는 경우
            case .success(let loginResponse):
                let responseDto = loginResponse.responseDto
                // 새로운 Access Token 저장
                UserSessionManager.shared.saveAccessToken(responseDto.accessToken)
                completion(true)
            //로그인에 실패하는 경우
            case .failure:
                completion(false) // 실패 처리
            }
        }
}
```