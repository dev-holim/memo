1. **README 작성**  
- bitbucket 저장소에 README.md 추가  
- 작성 가이드는 첨부문서 참고  
  

2. **commit 메시지 충실하게 작성**  
- 형식 -> 타입(범위): 내용   
- 내용은 너무 길지 않게(50자 이내)  
- 내용에 변경 이유를 작성  
나쁜 예) update code

나쁜 예) bug fix  
좋은 예) fix(api): handle null pointer in user service  
좋은 예) feat: allow user to reset password via email  
  
---  
## ![✅](https://fonts.gstatic.com/s/e/notoemoji/16.0/2705/72.png) 타입(Type) 종류  
| 타입       | 설명 |  
|------------|------|  
| `feat`     | 새로운 기능 추가 |  
| `fix`      | 버그 수정 |  
| `docs`     | 문서 관련 변경 |  
| `style`    | 포맷, 세미콜론 등 코드 변경 없음 |  
| `refactor` | 리팩토링 (기능 변화 없음) |  
| `test`     | 테스트 코드 추가/수정 |  
| `chore`    | 빌드/설정 파일 등 기타 변경 |  
---  
  
**3. 소스코드 저장소 관리 시스템 체계화**  
- 개발자에게 Owner/Maintainer/Developer/Viewer 레벨로 구분된 권한 부여  
   = SW 팀장은 본인이 타 저장소에도 최소 Developer 권한으로 참여 -> Merge/ Commit 히스토리 파악  
   = 각 저장소마다 정/부 개념으로 담당자 지정(정: Owner, 부: Maintainer). 그 외 개발자는 관련도에 따라 Developer 또는 Viewer 로 지정 -> 주 담당자 부재시에도 장애복구/긴급대응 능력을 확보하기 위함  
  
**4. 주요 이벤트 발생 시 코드 리뷰 진행**  
- 주요 신규 기능 개발 후 main 브랜치로의 Merge (pull request 시 진행, bugfix 제외)  
- 신규 서비스 개발 후 리뷰 요청  
- 기타 필요 시