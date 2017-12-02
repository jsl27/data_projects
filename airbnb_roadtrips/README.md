### Overview

Airbnb Roadtrips was the company's first-ever big-data consumer PR story. 

![](roadtrips_landing_design.png)

Roadtrips were defined as a chain of bookings at least three-bookings long, with consecutive check-in days. Bookings were restricted to U.S. locations. Thinking of each roadtrip as a transaction of destination cities, the most frequent sets of cities (\"trending roadtrips\") were identified using a market basket analysis. Finally, driving routes of these trending roadtrips were mapped.


### Learning Roadtrips

Internal Airbnb data on roadtrips, as defined above, was queried using HiveQL. The R package __arules__ was used for this market basket analysis. Top item sets were identified by the highest __support__, which is the proportion of all roadtrips that contain a particular item set.

The following code can used to run the market basket analysis. Dummy data and dummy parameters are used for data privacy reasons.

```R
library(arules)
library(ggmap)

# Example dataset
RT <- data.frame(
  roadtrip_id = c(1, 1, 1, 2, 2, 2, 2, 3, 3, 3),
  city_state = c("Seward, Alaska", "Homer, Alaska", "Anchorage, Alaska",
                 "Fairbanks, Alaska", "Talkeetna, Alaska", "Cantwell, Alaska", "Seward, Alaska",
                 "Nashville, Tennessee", "Dallas, Texas", "Houston, Texas")
) 

# Prepare dataset for market basket analysis (apriori)
RT <- RT[!duplicated(RT),] # Get rid of duplicated rows
RT <- split(RT$city_state, RT$roadtrip_id) # Spread data so each line is a roadtrip (ie "transaction")
RT <- as(RT, "transactions") # Convert to 'transactions' object

# Run apriori
rules <- apriori(RT, parameter = list(sup = 0.2, conf = .7, target = "rules", minlen = 2))

# Inspect top rules by support
# Support is a measure of how frequently the rule appears in the transactions
inspect(head(sort(rules, by = "support"), 10))

# Create lists of rules so that we can identify roadtrips containing those rules, then map them
# Each list is the merge of a rule's lhs and rhs
rt.toprules <- head(sort(rt.rules, by = "support"), 40)
rt.toprules <- mapply(c, as(rt.toprules@lhs, "list"), as(rt.toprules@rhs, "list"))
```

