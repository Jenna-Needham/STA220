# scripts/11_practice_in_r.R


#####  I reccomend the following strategy when completing this practice

# STEP 1: Attempt to create each prompt and answer the questions first without using AI.

# STEP 2: Look first at the code from the other scripts in this project
# i.e., Find an example and adapt it to your needs

# STEP 3:  Ask AI for help identifying specific problems with script you wrote
# i.e., do not give AI the whole prompt! Instead, give it specifically what you wrote 
# with no context and ask it to identify the problem and suggest a solution.

# STEP 4: Look at the practice solutions. 


#### HOWEVER HOWEVER HOWEVER
# It's better to use the syntax from practice_solutions to answer the questions
# than to do nothing!

# ---- 0. Packages and data ------------------------------------------------------------------
library(tidyverse)

# load colleges into environment
colleges <- read_csv("data/colleges.csv") # if missing, run 02_import 

# glassboro: Glassboro borough (Rowan University) general budget, in millions of dollars, 2016 to 2025
glassboro <- read_csv("data/glassboro.csv")
glimpse(glassboro)


# ---- Task 1. Land and people ---------------------------------------------------------------

ggplot(colleges, aes(x = land_sqmi, y = pop)) +
  geom_point()


# ---- Task 2. State aid ---------------------------------------------------------------------

ggplot(colleges, aes(x = state_aid_m, y = town)) +
  geom_col()

# ---- Task 3. Glassboro's budget over time --------------------------------------------------
# Hint: + scale_x_continuous(breaks = 2016:2025)   )

ggplot(glassboro, aes(x = year, y = budget_m)) +
  geom_point() +
  scale_x_continuous(breaks = 2016:2025)

ggplot(glassboro, aes(x = year, y = budget_m)) +
  geom_col() +
  scale_x_continuous(breaks = 2016:2025)


# ---- Task 4. Budget per resident -------------------------------------------------------------
# Hint: mutate(budget_per_resident = budget_m * 1000000 / pop). 

colleges2 <- colleges |>
  mutate(
    budget_per_resident = budget_m * 1000000 / pop
  )

ggplot(colleges2, aes(x = budget_per_resident, y = town)) +
  geom_col()

# ---- Task 5. Labels, then save it -----------------------------------------------------------
# Hint: ggsave("output/budget_per_resident.png", width = 6, height = 4).

ggplot(colleges2, aes(x = budget_per_resident, y = town)) +
  geom_col() +
  labs(
    title = "Camden budgets the most per resident among these college towns",
    subtitle = "Each bar is one New Jersey town with a four-year college",
    x = "General budget per resident, 2025 ($)",
    y = "Town",
    caption = "Source: NJ DCA, User Friendly Budget Database, 2025"
  )

ggsave(
  "output/budget_per_resident.png",
  width = 6,
  height = 4
)


