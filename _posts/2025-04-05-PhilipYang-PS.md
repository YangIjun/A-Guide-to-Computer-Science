---
layout: post
author: Philip Yang
tags: [ProblemSolving, ACSL Intermediate]
---

[Intermediate 2011-2012 Round 1](c:\Users\yangi\Downloads\ACSL Coding 2011-2012 Round 1 Intermediate (1).pdf)

#PROBLEM:
For most of this past summer, there was still a lockout and the potential for not 
having a 2012 National Football League (NFL) season. Two of the sticking points 
between owners and players were the high price for first round draftpicks and the 
extension of the season to 18 games. The following statistics are available for the 
top 5 first-round draftpicks in 2008:
1. 5 years, 57.5 million
2. 6 years, 56.5 million
3. 6 years, 72 million
4. 6 years, 60 million
5. 5 years, 51 million

If you were at the negotiating table, you would need to find statistical information 
out about these figures. 
INPUT: 
There will be 5 lines of input representing the top 5 picks in an NFL draft. Data 
may be input by using spaces, commas, or on separate lines. Each line will include 
an integer giving the length of the contract in years and a real number giving the 
value of the entire contract in millions. Only the significant digits will be included 
(i.e. 57.5 for 57.5 million). 
OUTPUT:
For the 5 lines of input, find the following: 
#1 The number of annual salaries that are more than 10 million 
#2 The average annual salary 
#3 The lowest salary per game in a 16-game season 
#4 The highest salary per game in an 18-game season 
#5 The difference between the average salary per game in a 16-game season 
versus an 18-game season. 
All outputs should be rounded to the nearest dollar if necessary and commas are 
not needed.

---
```python
# 필요한 변수 만들어 놓기
moreThan10 = 0
annualSalary = []
sixteenSalary = []
eighteenSalary = []
difference = 0


# 반복문, 5번 입력을 받기 위해 5번 반복
for i in range(5):
    # 입력을 split()를 통해 2개의 데이터로 나누고 각각 years와 salary에 저장
    years, salary = input().split()
    
    # 단위가 10만이기 때문에 10만을 곱하여 출력에서 요구한 단위와 통일시키기
    salary = float(salary)*1000000
 
    # 연봉 '리스트'에 각 선수의 연봉을 계산하여 저장하기
    # 사용된 listname.append() 의 뜻은 listname라는 
    # 이름을 가진 리스트 뒤에 괄호안에 있는 값을 추가
    annualSalary.append(float(salary)/float(years))
    
    # 16시즌에서의 게임별 봉급을 리스트에 저장
    sixteenSalary.append((float(salary)/float(years))/16)

    # 18시즌에서의 게임별 봉급을 리스트에 저장
    eighteenSalary.append((float(salary)/float(years))/18)

    # 연봉이 10만이상일 경우 카운트 +1
    if float(salary)/float(years) > 1000000:
        moreThan10 += 1
# 반복문 종료

#평균 연봉구하기: 
# sum(listname) 리스트에 있는 모든 항목의 합 반환
# len(listname) 리스트에 있는 항목의 수 반환
avgSalary = sum(annualSalary)/len(annualSalary)

# 5번째 항목 구하기, 16시즌과 18시즌의 평균 봉금의 절대값 구하기
# 절대값: abs() 괄호안에 있는 숫자의 절대값 반환
difference = abs(sum(sixteenSalary)/len(sixteenSalary) - sum(eighteenSalary)/len(eighteenSalary))


# 문제의 요구대로 출력
print(moreThan10)
print(round(avgSalary))
print(round(min(sixteenSalary)))
print(round(max(eighteenSalary)))
print(round(difference))
```
---