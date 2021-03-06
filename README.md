# AI_Class
ICT 충청 이노베이션 사업에서 주관하는 충남대학교 AI 고급 과정 수업을 듣고 정리하는 저장소입니다. <br/>
README 파일에선 확률과 통계에 대한 기본 개념을 정리합니다.

## 확률
- 실생활의 확률은 전제가 명확하지 않기 때문에 데이터를 쌓은 후 분석할 수밖에 없다. 이를 **통계적 확률**이라고 한다.

### 1. 경우의 수
: 확률은 경우의 수의 비율. 경우의 수를 셀 때 '빠짐'과 '중복'을 주의해야 한다.
- 합의 법칙
: 사건 A, B가 동시에 일어나지 않고, 각각 a, b라는 경우의 수를 갖는다면, A 또는 B가 일어날 경우의 수는 a + b 임.
- 곱의 법칙
: 사건 A의 경우의 수가 a, 사건 B의 경우의 수가 b일 때, A에 이어서 B가 일어날 경우의 수는 a * b 임.
- 경우의 수에선 '또는'인가 '동시에' 인가를 주의해야 함! 

### 2. 순열
:순열은 어떤 순서를 매겨 중복없이 나열하는 것.
- 공식: nPr = n! / (n-r)!

    ex) 참가자가 6명인 마라톤 대회에서 1위, 2위, 3위가 나올 경우의 수
    
- 중복순열
: n개 중 순서는 있지만 중복을 허락해 r개 뽑는 것.    

- 중복집합 순열
: n개 중 서로 같은 것(서로 같은 것을 모은 집합)이 p, q, .... r개 있을 때 n개를 나열. = n! / p! q! ... r!


### 3. 조합
: 여러 개 중 특정 개수를 선택한 경우(순서x)
- 공식: nCr = nPr / r!

- 중복조합
: n개 중 순서는 없지만 중복을 허락하여 r개 뽑는 것.
: nHr = n+r-1Cr
   
### 순열과 조합 정리
: A, B, C 세 글자 중 2 개를 선택하는 경우

                                순서를 생각하는 경우(순열)               순서를 생각하지 않는 경우(조합)
                                
                                
         중복 허용하지 않음             A - B                               A - B
                                     \ C                                  \ C

                                    B - A                               B - C
                                      \ C                               
                                                                        :3C2 = 3
                                    C - A
                                      \ B

                                   : 3P2 = 6
        
        
        
        중복 허용                     / A                                  / A
                                  A - B                                A - B
                                    \ C                                  \ C   
                                    
                                    / A
                                  B - B                                B - B
                                    \ C                                  \ C
                                    
                                    / A                                C - C
                                  C - B   
                                    \ C                                :3H2 = 6
                                    
                                  :3^2 = 9
                                  
## 기초 통계                          

## 고급 통계
