# Peliculas

The initial step involved acquiring the database. To achieve this, I utilized Selenium for web scraping on the IMDb page, employing an automated approach, and successfully obtained data for 3000 films.

![Untitled](https://github.com/user-attachments/assets/bec919e4-cbe0-4248-abe9-ae76af218074)


The database has the following columns:

- Title.

- Rating.

- Director.

- MetaScore.

- Script (Screenwriters).

- Actor.

- Category.

**The second step was to clean and understand the DB, for this:**

Database Status Check::

![Untitled (1)](https://github.com/user-attachments/assets/6f600490-1790-4190-a918-177ec26e4665)


The 'Script' and 'Actor' columns follow the format (actor1, actor2, actor3), requiring the transformation into additional columns.

![Untitled (2)](https://github.com/user-attachments/assets/68f8478a-370f-4fb3-8f5e-e292118ce9ee)

Now, I had to perform "One Hot Encoding" to convert "Category" into binary columns:

![Untitled (3)](https://github.com/user-attachments/assets/8a1bd4fa-6459-420f-9996-a56a722e3153)


**Then I had to understand the database.**

Rating distribution:

![Untitled (4)](https://github.com/user-attachments/assets/f2a37b5c-c588-4f00-83a6-4753ee81aead)

![Untitled (5)](https://github.com/user-attachments/assets/7d8cd14a-b156-4336-af66-57b624e7dda5)

Top 5 Directors with more films:

![Untitled (6)](https://github.com/user-attachments/assets/c685ab9f-29ee-48c5-aa63-10cd2441ef73)

Top 10 films with more films:

![Untitled (7)](https://github.com/user-attachments/assets/27bb988b-0b02-497d-9883-332e484d4e83)

Directors with more films with higher ratings:


![Untitled (8)](https://github.com/user-attachments/assets/889fd771-afc7-47b0-befb-ea0b16977e29)

![Untitled (9)](https://github.com/user-attachments/assets/df58a877-48d1-4aa4-9756-e9b5588e8ecb)

Actors with the highest count:

![Untitled (10)](https://github.com/user-attachments/assets/b0d4eb5a-b3ef-4666-a135-94c7e68244c8)

Bivariate relationship between Director and Rating:

![Untitled (11)](https://github.com/user-attachments/assets/affa2cbd-0d9e-4a91-ae1b-e75008a1def0)

Finally, the columns chosen for the ML algorithm were Director, Actors, Scripts, and all the Categories.

After completing these tasks, I began encoding the database, transforming strings into numerical codes for the ML algorithm.

![Untitled (12)](https://github.com/user-attachments/assets/2968e473-125c-4256-88e8-01a1f5222952)

![Untitled (13)](https://github.com/user-attachments/assets/aaf606dd-3c8e-4496-8f46-30891b558aca)

I chose the Random Forest Regressor since it allows you to assess different combinations and, theoretically, avoids overfitting. 

First:

![Untitled (14)](https://github.com/user-attachments/assets/2bea7fb3-44cc-45a7-8426-6663c2b224a6)

Then, I searched for the range of max_features:

Validation using Out-of-bag error

![Untitled (15)](https://github.com/user-attachments/assets/c83f8fb5-c939-435b-937d-4cdfd94f23af)

![Untitled (16)](https://github.com/user-attachments/assets/f06d531a-3723-4d90-956a-c81bb1315b5a)

Validation using k-cross-validation and neg_root_mean_squared_error.

![Untitled (17)](https://github.com/user-attachments/assets/5ea8251c-78ff-4405-bf1c-ec78568fcd56)

![Untitled (18)](https://github.com/user-attachments/assets/ac4e3899-5798-43c2-a92b-46c2a990e2ad)

Afterwards, I evaluated the best hyperparameters:

![Untitled (19)](https://github.com/user-attachments/assets/3f72740c-058f-42bc-963a-164264a6d7a5)

Best hyperparameters through cross-validation:

![Untitled (20)](https://github.com/user-attachments/assets/472da79d-0b08-4c3e-b271-d4250c0bc068)

Test error of the final model:

![Untitled (21)](https://github.com/user-attachments/assets/65315ad4-edce-4d6f-9a55-c29b1924c7a9)

![Untitled (22)](https://github.com/user-attachments/assets/aec2e94f-426f-4b08-9835-fd054d00493d)

Importance of each column:

![Untitled (23)](https://github.com/user-attachments/assets/584ec5da-bf37-4182-bb2a-905f36587fbe)

Resuts:

![Untitled (24)](https://github.com/user-attachments/assets/f47a7458-9116-4494-9031-cb42c54a2f2b)

**Conclusion:**

The obtained results were not as expected; the small error in each prediction suggests a kind of overfitting, possibly due to the limited number of movies (constrained by computer capacity). There aren't many examples for each category, and there are few actors, causing each variable to lack sufficient weight to significantly influence the prediction. However, the project served as valuable practice for web scraping, data cleaning, and the application of random forest regression.
















