created on: 05/26/2020

updated on: 06/04/2021

# LeetCode Notes

## Description

Problem solving and practicing on [LeetCode](https://leetcode.com/) and [力扣](https://leetcode-cn.com/) using Python and SQL.

## Algorithm

[Problems and solutions](https://github.com/tong-jin-nyu/leetcode-notes/tree/master/algorithm)

[Wiki page](https://github.com/tong-jin-nyu/leetcode-notes/wiki/Algorithm)

## Database

[Problems and solutions](https://github.com/tong-jin-nyu/LeetCode-notes/tree/master/database)

[Wiki page](https://github.com/tong-jin-nyu/leetcode-notes/wiki/Database)

### Join

- [175 Combine Two Tables](database/175%20Combine%20Two%20Tables.md) - Left join
- [180 Consecutive Numbers](database/180%20Consecutive%20Numbers.md) - Self join
- [181 Employees Earning More Than Their Managers](database/181%20Employees%20Earning%20More%20Than%20Their%20Managers.md) - Left join
- [196 Delete Duplicate Emails](database/196%20Delete%20Duplicate%20Emails.md) - Self join
- [262 Trips and Users](database/262%20Trips%20and%20Users.md) - Left join
- [580 Count Student Number in Departments](database/580%20Count%20Student%20Number%20in%20Departments.md) - Right join
- [601 Human Traffic of Stadium](database/601%20Human%20Traffic%20of%20Stadium)
- [602 Friend Requests II: Who Has the Most Friends](database/602%20Friend%20Requests%20II%20Who%20Has%20the%20Most%20Friends.md)
- [1068 Product Sales Analysis I](database/1068%20Product%20Sales%20Analysis%20I.md) - `JOIN`
- [1075 Project Employees I](database/1075%20Project%20Employees%20I.md) - `JOIN`

### CTE

- [176 Second Highest Salary](database/176%20Second%20Highest%20Salary.md) - CTE as part of `WHERE`
- [177 Nth Highest Salary](database/177%20Nth%20Highest%20Salary.md) - CTE as part of `SELECT`
- [183 Customers Who Never Order](database/183%20Customers%20Who%20Never%20Order.md) - CTE as part of `WHERE`
- [512 Game Play Analysis II](database/512%20Game%20Play%20Analysis%20II.md) - CTE as part of `WHERE`
- [550 Game Play Analysis IV](database/550%20Game%20Play%20Analysis%20IV.md) - CTE as part of `WHERE` and `SELECT`
- [574 Winning Candidate](database/574%20Winning%20Candidate.md) - CTE as part of `WHERE`
- [614 Second Degree Follower](database/614%20Second%20Degree%20Follower.md) - CTE as part of `WHERE`
- [615 Average Salary Departments vs Company](database/615%20Average%20Salary%20Departments%20vs%20Company.md) - CTE as part of the main table
- [619 Biggest Single Number](database/619%20Biggest%20Single%20Number.md) - CTE as part of the main table
- [1070 Product Sales Analysis III](database/1070%20Product%20Sales%20Analysis%20III.md) - CTE as part of the main table
  
### Window function

- [178 Rank Scores](database/178%20Rank%20Scores.md) - `DENSE_RANK()`
- [180 Consecutive Numbers](database/180%20Consecutive%20Numbers.md) - `LEAD()`, `LAG()`
- [184 Department Highest Salary](database/184%20Department%20Highest%20Salary.md) - `RANK()`, `PARTITION()`
- [185 Department Top Three Salaries](database/185%20Department%20Top%20Three%20Salaries.md) - `DENSE_RANK()`
- [197 Rising Temperature](database/197%20Rising%20Temperature.md) - `ROW_NUMBER()`, `LAG()`
- [534 Game Play Analysis III](database/534%20Game%20Play%20Analysis%20III.md) - `OVER()`, `PARTITION BY`
- [569 Median Employee Salary](database/569%20Median%20Employee%20Salary.md) - `ROW_NUMBER()`
- [571 Find Median Given Frequency of Numbers](database/571%20Find%20Median%20Given%20Frequency%20of%20Numbers.md) - `SUM()`, `OVER()`
- [579 Find Cumulative Salary of an Employee](database/579%20Find%20Cumulative%20Salary%20of%20an%20Employee.md) - `SUM()`, `OVER()`, `RANK()`
- [585 Investments in 2016](database/585%20Investments%20in%202016.md) - `PARTITION BY`
- [618 Students Report by Geography](database/618%20Students%20Report%20by%20Geography.md) - `ROW_NUMBER()`
- [1076 Project Employees II](database/1076%20Project%20Employees%20II.md) - `RANK()`
- [1077 Project Employees III](database/1077%20Project%20Employees%20III.md) - `RANK()`

### Sort and filter

- [182 Duplicated Emails](database/182%20Duplicated%20Emails.md) - `HAVING()`
- [511 Game Play Analysis I](database/511%20Game%20Play%20Analysis%20I.md) - `GROUP BY`
- [570 Managers with at Least 5 Direct Reports](database/570%20Managers%20with%20at%20Least%205%20DIrect%20Reports.md) - `HAVING`, `GROUP BY`
- [577 Employeee Bonus](database/577%20Employee%20Bonus.md) - `IS NULL`
- [578 Get Highest Answer Rate Question](database/578%20Get%20Highest%20Answer%20Rate%20Question.md) - logic
- [595 Big Countries](database/595%20Big%20Countries.md)
- [584 Find Customer Referee](database/584%20Find%20Customer%20Referee.md) - `IS NULL`
- [586 Customer Placing the Largest Number of Orders](database/586%20Customer%20Placing%20the%20Largest%20Number%20of%20Orders.md)
- [596 Classes More Than 5 Students](database/596%20Classes%20More%20Than%205%20Students.md)
- [597 Friend Requests I: Overall Acceptance Rate](database/597%20Friend%20Requests%20I%20-%20Overall%20Acceptance%20Rate.md) - `UNION ALL`
- [608 Tree Node](database/608%20Tree%20Node.md) - `CASE`
- [620 Not Boring Movies](database/620%20Not%20Boring%20Movies.md) - `WHERE`
- [626 Exchange Seats](database/626%20Exchange%20Seats.md) - `CASE`
- [1179 Reformat Department Table](database/1179%20Reformat%20Department%20Table.md) - `CASE`
- [1045 Customers Who Bought All Products](database/1045%20Customers%20Who%20Bought%20All%20Products.md) - `HAVING`, `GROUP BY`
- [1050 Actors and Directors Who Cooperated At Least Three Times](database/1050%20Actors%20and%20Directors%20Who%20Cooperated%20At%20Least%20Three%20Times.md) - `HAVING`, `GROUP BY`
- [1069 Product Sales Analysis II](database/1069%20Product%20Sales%20Analysis%20II.md) - `GROUP BY`

### Other

- [612 Shortest Distance in a Plane](database/612%20Shortest%20Distance%20in%20a%20Plane.md)
- [613 Shortest Distance in a Line](database/613%20Shortest%20Distance%20in%20a%20Line.md) - `POWER`
- [627 Swap Salary](database/627%20Swap%20Salary.md) - `UPDATE`

## Analytics

[Problems and solutions](https://github.com/tong-jin-nyu/LeetCode-notes/tree/master/analytics)

[Wiki page](https://github.com/tong-jin-nyu/leetcode-notes/wiki/Analytics)
