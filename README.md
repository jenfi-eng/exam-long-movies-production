# Movie Production!

This is an extension of the shorter exam, [Movies API](https://github.com/jenfi-eng/exam-short-movie-api).

Here we want an API endpoint for movie producers to be able to create a movie & book actors.

## Info

1. Use any language or framework you are most comfortable with.
1. Don't spend more than >4 hours on this.
1. When you're finished - **zip** up the directory, email it.

## Requirements

1. Create a `POST` endpoint (e.g. `/create-movie`)
    - Movie Title
    - `X` Number of actors to book
    - Production length in `Y` months
1. During the endpoint
    - Randomly `X` actors to book for the movie.
    - Booked actors may only be booked for one movie
1. If all actors are currently booked
    - Still increment the current month
    - Respond with a failure
1. Your previous [Movies API](https://github.com/jenfi-eng/exam-short-movie-api) output should now be updated with the new Movies.
1. Add `RSpec` coverage of API and anything else you believe is necessary.

## For simplicity

1. Each time the POST endpoint is called, it should increment the current month by 1.
    - If the Production Length is `1`. Actors are always available.

## Example endpoint flow

1. Existing DB:

    | Actor Name | Number of Movies |
    | ----- | ---- |
    | Awesome Actress | 2 |
    | Actor Dude | 1 |

1. Call endpoint (e.g. `POST /create-movie`)

    - Movie title: `'My Amazing Movie'`
    - Num actors: `2`
    - Production length: `3`
    - Endpoint response
      - Success
      - Movie Title: `'My Amazing Movie'`
      - Booked Actors: `['Awesome Actress', 'Actor Dude']`

1. Call endpoint (try x1)
    - Movie title: `'Some Other Movie'`
    - Num actors: `1`
    - Production length: `2`
    - Endpoint response
      - Failure
      - Reason: `'No actors/actresses are available.'`

1. Call endpoint (try x2)
    - Movie title: `'Some Other Movie'`
    - Num actors: `1`
    - Production length: `2`
    - Endpoint response
      - Failure
      - Reason: `'No actors/actresses are available.'`

1. Call endpoint (try x3)
    - Movie title: `'Some Other Movie'`
    - Num actors: `1`
    - Production length: `2`
    - Endpoint response
      - Success!
      - Movie Title: `'Some Other Movie'`
      - Booked Actors: `['Actor Dude']`

## Extra

This section is **NOT** required. If you have lots of left over time and want to have fun. Jenfi will pay for it.

### Data Modifications

- Each `Actor`, now has a Salary as a Percentage of Budget (e.g. 20%)
- Each `Movie`, now has a Budget (e.g. $100,000,000)

### Logic Modifications

- For each `Movie` the `Actor` has appeared in, add 10% to the Actor's Salary
- If there are other actors available who are in budget, pick them instead.
- If no actors in budget, fail to create/book.

### Endpoint Modifications

- Endpoint now requires a 'Budget' to be given
- Endpoint responds with each Actor's cost
- Add a new failure - `'There are no actors available within budget'`