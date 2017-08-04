# apexlabs_takehome

Q1

You are the CTO of a startup company that gets most of their revenue from users tapping on ads in your app. To maximize revenue, you want to predict the chance that a specific user will click on a specific ad in your app. Your server logs have kept track of which ad was served to which user and whether that user then clicked on the ad. In the interest of anonymyzing your data, you have stripped off all metadata about the kind of users and the kind of ads, and instead represented each ad and each user by a unique id. This data is saved inside `click_event_log.csv`.

a. Given a `user_id` and an `ad_id`, create a model that will predict the probability that the user will click on the ad. List any assumptions you make about the data when you create this model. What does this model output for user_id 12 and ad_id 10? What about user_id 50 and ad_id 177? Finally, what about user_id 13 and ad_id 241?

b. Even though the data is anonymized, there is a lot that can be learned about user-user and ad-ad similarity from this data. Create a user-user similariy matrix A, where A[i,j] represents how similar users i and j are. The higher this number, the more similar they are. Analyze this matrix; are there any interesting / notable user subgroups on the site?

Q2

50 different satelites took very close images of the earth from a known azimuth and altitude. These images were then examined by humans to determine whether the image contains only land (observed_image_output=0), only water (observed_image_output=2), or a combination of land and water (observed_image_output=1). For each image, we know the log of the azimuth and the log of the altitude of the satelite when it took the photo, the lens size in cm of the satelite that took the photo, and for how many months in operation the satelite was around when it took the photo.

a. Do the relevant pre-processing, training, and cross-validation to create the best classification model you can for this data, where you want to predict observed_image_output. Only use `satelite_20.csv` for this part of the problem. 

b. Based on the classification model you created in part a, predict observed_image_output given the parameters in `satelite_20_test.csv`. (Hint: all of the first four rows have class '0' as their answer. Most inferior classification models only predict that two of these four have class '0' as their prediction. Figure out in what ways your model might be naive given this hint, and try to modify your predictions until at least the first four rows all predict class '0'.)

Q3

Humanity has begin to terraform Mars. We have a network of 10 dams on the red planet that store and transport water for various cities settled across the planet. Since the polar ice caps haven't begun to melt, the system is self-contained. This means that water only comes from or goes to other dams. There are no external lakes or basins to source or put water into. Recently, foremen have noticed cracks appearing on some dams at the end of a Martian week. Over the weekend, these cracks are patched up completely, so the damage is not cumulative. No dams have cracks at the beginning of each week. Even though the dams are each rated to hold 40000 gallons maximum, the foremen believe this rating is falsely inflated. They believe the cracks are present because sometimes the dams are over their true capacity, which they think is less than 40000 gallons.

This dataset (`dams.csv`) shows the direct movement of water between dams at the end of every workweek for 95 weeks. At the end of week 0, before the dataset begins, each dam holds 10000 gallons of water. Therefore, as an example, at the end of week 1 in this dataset, every dam would be holding 10000 gallons of water except for dams 2 and 7. Dam 2 would hold 9315 gallons of water and dam 7 would hold 10685 gallons of water.

We also have the foremen's log (`foremen_log.csv`) of which dams are showing cracks at the end of each week for the first 30 weeks. Remember, dam damage is not cumulative, and if it appears in subsequent weeks it is only because of the effects of the prior week.

a) Using `dams.csv`, determine if every dam is likely connected to every other dam. If it isn't, which dams don't seem to have a connection to each other? Make a schematic showing your most likely esimate of how the dams are connected, given the data presented. (Make the assumption that if Dam A and Dam B don't send water directly to each other throughout the 95 weeks, they are likely not connected. Furthermore, make the assumption that if there is a lot of traffic between A and B, that the tunnel between them is larger.)

b) Make the assumption that there is some unknown capacity (`x`) gallons of water at which all the dams start to show cracks. Combine the information about the movement of water in `dams.csv` and the observation of cracks in `foremen_log.csv` to estimate an `x` that fits the data. Using `x`, extrapolate from the foremen log to predict which dams will show cracks at the end of each week for full 95 weeks.
