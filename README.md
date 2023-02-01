# Upgraded Octo Guacamole
## Context
Our client just sent us the generation data of two of his power plants (Hyrule and Draconis) and consumption from one of his consumer (Luminix). 

He would like us to compute the hourly and daily matching between Luminix consumption and the power plants generation.

## How do we calculate the matching score?

Let's say for a given hour, we have 100kWh of generation and 200kWh of consumption. The matching percentage is 50% (100/200) for this hour. 
If generation is 200kWh and consumption is 100kWh, then the matching percentage is 100%, meaning all consumption is covered by the provided generation.

Since one image is worth 1000 words, we can represent it like this:
![MicrosoftTeams-image](https://user-images.githubusercontent.com/100279243/216078534-8ca3eca4-1a9f-44ba-abf1-1eb75fe6b92e.png)

The dark blue area being the matched quantity. 

Now to have the complete hourly matching for a given month, we do:

$$ hourlyMatchingScore_{month} =  \frac{\sum_{hour=0}^{720} min(Generation_{hour}, Consumption_{hour})}{\sum_{hour=0}^{720} Consumption_{hour}} $$


To compute the matching score on a daily level, it is almost the same, we just need to aggregate consomption and generation at the daily level before calculating the score.

$$ dailyMatchingScore_{month} =  \frac{\sum_{day=1}^{30} min(Generation_{day}, Consumption_{day})}{\sum_{day=1}^{30} Consumption_{day}} $$

## What is the client asking for?

He just wants a way to access the matching score for a given period. He might also need to have access to the matching details (for every hour or every day of the given period).

## Okay. Let's go!

For a couple of hours, you're on your own at home. You have access to a PostgreSQL database to help you build a solution (but not mandatory). You can either choose Kotlin or Python.

Spend your time as you please, you don't need to come up with a fully built solution. We just need you to start building a proposal:
- to handle the heterogeneous data formats
- to calculate the desired metrics
- to expose the result to the client

Ideally, you would have written the tests to assert the solution's behaviour. We would then work together on how to implement it.

We will pay extra attention to:
- the tests readability
- how you separate business logic from pure technical aspects
- your communication skills

We will be obviously time-limited to solve this, so try to focus on code quality rather than technical shenanigans.



