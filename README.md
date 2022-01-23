# Kaggle-Airbnb-New-User-Booking-Prediction

https://www.kaggle.com/c/airbnb-recruiting-new-user-bookings

This is a solution to the above kaggle competition. The goal is to predict which countries will the new users book based on customers' personal information, session histories, etc. The 12 destinations are 'AU', 'GB', 'CA', 'US', 'DE', 'IT', 'FR', 'ES', 'NL', 'PT', 'NDF', and 'other', where 'NDF' means did not book and 'other' means other countries.

## EDA

- Country destinations distribution:

![image](https://user-images.githubusercontent.com/76148884/150660553-a82e3067-08ec-4c5c-87d8-79ff5a01c94f.png)

- Age and destinations:

![image](https://user-images.githubusercontent.com/76148884/150661006-64235972-aeda-4160-9551-ea60a943dd73.png)

- Device type, browser are related to destinations. 
- Session history counts is related to book or not. The more histories users have, the more likely the users will book.
- System language is also related to the destination languages.

## Feature Engineering

- Count sessions and sum total time spent for each user.
- Count different actions and time spent on different action for each user.
- Clean age. Fill null ages with median.
- Destinations probabilities based on system languages.
- Feature selection, one-hot encoding.

## Modeling
I first tried lightgbm and the performance is good. Then I tried a voting classifier with lgb, xgboost and random forest. The performace increased a little bit.

For the submission, I select 5 most likely countries based on probabilities for each user.

## Conclusion

The most difficult problem in this project is that there are too many features from session data. In session, the column "action" has more than 300 categories. A more complex model may be needed. Another issue is that age got a lot of missing values. Also, the difference between booking and not booking is obvious. However, the difference among difference countries is small. It is hard to predict which country the user will go.
