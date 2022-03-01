# HackerRank-
SQL -> Basic Join -> Top Competitors

Julia just finished conducting a coding contest, and she needs your help assembling the leaderboard!
Write a query to print the respective hacker_id and name of hackers who achieved full scores for more
than one challenge. Order your output in descending order by the total number of challenges in which 
the hacker earned a full score. If more than one hacker received full scores in same number of challenges, 
then sort them by ascending hacker_id.

Input Format

The following tables contain contest data:

Hackers: The hacker_id is the id of the hacker, and name is the name of the hacker


![image](https://user-images.githubusercontent.com/90959192/156126887-79205c55-1bd1-4b29-926f-e1ccc1428b69.png)


Difficulty: The difficult_level is the level of difficulty of the challenge, and score is the score of the challenge for the difficulty level. 

![image](https://user-images.githubusercontent.com/90959192/156127199-9d77d3a6-5c97-4c48-927e-6799557bc210.png)


Challenges: The challenge_id is the id of the challenge, the hacker_id is the id of the hacker who created the challenge, and difficulty_level is the level of difficulty of the challenge

![image](https://user-images.githubusercontent.com/90959192/156127017-1505a6f0-94ba-4321-ae52-40b68c8a0aa8.png)


Submissions: The submission_id is the id of the submission, hacker_id is the id of the hacker who made the submission, challenge_id is the id of the challenge that the submission belongs to, and score is the score of the submission.

![image](https://user-images.githubusercontent.com/90959192/156127078-57c08c57-00a9-47e8-bd5a-0bbc8bdb8f6f.png)


**Explanation**

Hacker 86870 got a score of 30 for challenge 71055 with a difficulty level of 2, so 86870 earned a full score for this challenge.
Hacker 90411 got a score of 30 for challenge 71055 with a difficulty level of 2, so 90411 earned a full score for this challenge.
Hacker 90411 got a score of 100 for challenge 66730 with a difficulty level of 6, so 90411 earned a full score for this challenge.
Only hacker 90411 managed to earn a full score for more than one challenge, so we print the their hacker_id and name as 2 space-separated values.


=============================================================================================================================

**ANS**


        select  Hackers.hacker_id, Hackers.name from 
        Hackers full outer join Submissions 
        on
        Hackers.hacker_id = Submissions.hacker_id
        full outer join Challenges
        on 
        Challenges.challenge_id= Submissions.challenge_id
        full outer join Difficulty
        on
        Difficulty.difficulty_level = Challenges.difficulty_level
        where Difficulty.score = Submissions.score
        group by Hackers.hacker_id, Hackers.name
        having count(*)>1
        order by count(*) desc , Hackers.hacker_id;      



===============================================================================

You can aslo put Hackers as h
                 Difficulty as d
                 Challenges as c
                 Submissions as s
it will reduce repetation of lengthy table name.

===============================================================================









