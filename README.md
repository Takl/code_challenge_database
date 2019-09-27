# SQL Code Challenge

# Setup

Included in this repo is everything you need to get started. If you have postgres already installed feel free to use your local instance or if you prefer feel free to use the included docker-compose file.

```bash
$ docker-compose up

# Once the server starts open a new terminal window and run

$ docker exec -it code_challenge_database_server_1 createdb -U postgres code_challenge

$ docker exec -it code_challenge_database_server_1 bash -c "psql -U postgres code_challenge < /root/dump.sql"
```

After running `docker-compose up` you should be able to connect using your favorite tool on:

- Host: localhost
- Port: 5432
- User: postgres
- Database: code_challenge

## Tasks

### Monthly Report

From the orders table, write a query that lists the number of orders for a given month ordered by date.

The results of a query should return:

- date in 'YYYY-MM-01' format
- number of orders for that month
- the revenue for the the given month converted from cents to dollars in $nn.nn format.

### User Satisfaction

Create a view that determines which users are the most satisfied with their orders. To determine this take into account the following:

- The number of orders for each user.
- The average rating of the orders.

Based on the user's satisfaction rank the users from most satisfied to least satisfied.
The results should return:

- user_id
- rank,
- full name (last, first)
- email_address
- mobile_number
- order_count
- score (calculation to justify rank)


# Marketing Data

Now that we have a score for each user our marketing would like to reach out to the top 10 users and congratulate them. They would also like to send marketing material to all of the users that have not yet placed an order.

The results of each must be delivered in JSON format. To make this easier in the future create a function that produces a proper JSON payload.

Write queries that:

- Produce a list of 10 users to congratulate
- Produce a list of all users that have not yet placed an order
- Create a function that returns the data in a proper JSON format.

Example:

```JSON
 {
    "data": [
        {
            "full_name": "Warren, Tim",
            "email_address": "tim.warren@takl.com",
        },
        { ... }
    ]
}
```