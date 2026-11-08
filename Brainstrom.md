# This file I all about how I got to the solution ( Ensuring you solve it on your own cause it helps 🤔 🧠)

- Credit goes to the creators of the game, link for the game : https://mystery.knightlab.com,


## Steps:
- 1) I ran this code ` SELECT * FROM sqlite_master` ( I know it is blunt and inhumane ) 
- 2) looked through the ERD and progressed into the table ` crime_scene_report `
- 3) then filter with 'WHERE' to put in murder as we have problem revolving around a murder("aka Murder Mystery")
- 4) we encounter lot of missing values on the display hmm.. but we read the descriptions of this list we find some clues 
- 5)- 1: sometime on ​Jan.15, 2018​ 
    - 2: it took place in ​SQL City
    - 3: Murder
- 6) spoiler directly gives you the answer(3 records) : ` SELECT * FROM crime_scene_report WHERE type == 'murder' AND city == 'SQL City' AND date == '20180115'`
  - we filtered the city and type we can do date aswell to get a precise record ( in case we had a large amount of data records then we cant just point out at one record so...)
  - we got our culprit details but we need the name check the ERD again and lookout
- 7) the record says two witness 
    - 1)  wit1 -> lives at the last house on "Northwestern Dr"
    - 2)  wit2 -> named Annabel, lives somewhere on "Franklin Ave"
- 8) we place order as the first witness is the last house on northwestern Dr so DESC we get a git "Morty Schapiro"
- 9) trace another witness by name and address ; first we are not getting a record for annabel so its possible that name is having annabel included in it so doing LIKE we get the record !!
- 10) we got both their ids now lets see what they spoke in their interview ->  "16371" "14887"
- 11) first witness has more detail so looking we get another set of clues 
    - 1) gym(Get Fit Now Gym bag) 
    - 2) gym status is gold(membership no-> 48Z) 
    - 3) man getting into their car and car_plate = "H42W" has this along so(LIKE)
- 12) we missed one clue that is date witness said the man worked ->  working out at the gym on 9th Jan.
- 13) so query should have table check_in from that gym with date and membership_id like the above hint
- 14) we get two records now with membership id "48Z7A" and "48Z55" , lets look at driver plate now 
- 15) ` SELECT * FROM drivers_license WHERE plate_number LIKE '%H42W%' AND gender = 'male'; ` the query to keep yall updated
- 16) now we have two records noting the ids down -> 423327 , 664760 
- 17) this ids will get us the name of the ones we need -> final suspects 
- 18) out of this two individuals getting the male with gold status and the get fit gym 
- 19) the final query would be this : ` SELECT * FROM get_fit_now_member WHERE person_id IN ("51739", "67318");`
- 20) the murderer is ~~Jeremy Bowers~~ 
=========================== THIS COMPLETES THE GAME =================================

BONUS CHALLENGES I will do it in mean time and update....

9 NOV Monday 
continuing the work of bonus challenges:
1) we get the result as there still a culprit free of charges  
2) we will have to get the interview table of the killer Jeremy he gives some clues again 
  - 1) female
  - 2) 5'5" (65") or 5'7" (67") tall
  - 3) red hair
  - 4) drives a Tesla Model S
  - 5) attended the SQL Symphony Concert 
  - 6) attended concert 3 times in December 2017 
3) with this clues we can get the mastermind with ease
4) to complete the lookup faster the two queries will be about the car she drove and other will be the times they attended concert 
5) ~~Miranda Priestly~~ is the mastermind 
