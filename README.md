
IE 360 Statistical Forecasting and Time Series
Spring 2024 – Project
Solar Power Forecasting
This project is about providing hourly solar power prediction of Edikli GES (Güneş Enerjisi Santrali) for
the next day. Edikli GES is located in Niğde at 38.29 North, 34.97 East (between 37.75-38.75° north
latitude and 34.5 -35.5° east longitude.) and further information related to the capacity and location is
available on
• https://www.birlesimyesilenerji.com/tr/yatirimlarimiz/edikli-ges/
• Google Earth link to the power plant is: https://shorturl.at/qzDN6
The project is organized as a competition (like in platforms such as www.kaggle.com) in which you are
expected to make submission everyday. For this purpose, we have built a system so that you will be
able to make submissions via Google Forms and monitor your progress through Google Sheets. We
will be informing you about the details of the submission system once we finish our tests.
.
The prediction is needed in a very similar setting to real life needs of the energy traders performing
operations in energy markets. In other words, the assumption is that on day d, the predictions are
needed for day d+1 and you know the production values until the end of day d-1. Note that you need
to provide forecasts for each hour of day d+1 (i.e. 24 predictions). In real life, you have to submit your
predictions before 12 pm of the day d for the next day (i.e. day d+1). Provided data file includes the
weather measurements for 25 grid points (coordinates) nearby the power plant. The grid points are
provided in Table 1.
Table 1. The latitude and longitude pairs for weather variables
The weather variables that can help for solar power plant production forecasting are described below:
• DSWRF_surface: This is the short version of downward shortwave radiation flux which is
known to be highly related to the production level. This is further described on the following
link:
https://www.goes-r.gov/products/baseline-DSR.html
On the other hand, I advise you not to spend too much time to understand the background
information about this variable. Instead follow a data-driven approach to understand its
relation to production levels.
• USWRF_top_of_atmosphere, USWRF_surface, DLWRF_surface: These are also solar radiation
related variables which can be related to the production level and are further described on the
following link:
https://www.noaa.gov/jetstream/atmosphere/energy
• TCDC_low.cloud.layer, TCDC_middle.cloud.layer, TCDC_high.cloud.layer,
TCDC_entire.atmosphere: These are the total cloud cover data (in terms of percentage) for
different type of clouds. Further information about cloud types are available on
https://en.wikipedia.org/wiki/List_of_cloud_types however as advised for DSWRF data, please
follow a data-driven approach to understand if the variable provides information on hourly
production.
• CSNOW_surface: This is Categorical Snow variable. It takes one if it snows, zero otherwise. This
can be related to the production levels as solar panels can get covered by snow in winters.
• TMP_surface: Temperature at the provided location. Temperature can represent the
seasonality. Moreover it is known that high temperatures affect the solar panels and decrease
their efficiency.
You are given this weather information that can be helpful in the forecasting task for 25 coordinates.
This information is provided in so called “long format”. A sample view of the data is shown in Figure 1.
One can create a data set where we have the information of the weather variables at each location
using reshaping operations. For R, you can follow the tutorial on
https://cran.r-project.org/web/packages/data.table/vignettes/datatable-reshape.html if you use
data.table package and https://www.statology.org/pandas-long-to-wide/ can help you to reshape your
data in Python (and pandas). This operation can result in a data in the following format:
“VARIABLENAME_LATITUDE_LONGITUDE” as illustrated in Figure 2. This makes a tabular data set
which is generally needed for regression approaches. This will make 25 coordinates multiplied with 10
variables = 250 weather variables in the wide format. The production and weather data is provided on
Moodle. Note that during the competition phase, you will receive the latest possible information for
both (weather forecasts for tomorrow and latest available production data from day d-1).
Figure 1. Weather information in “long format” (due to large number of variables, partial table is
shown). Latitude and longitude information is provided as separate columns
Figure 2. Weather information in “wide format” (due to large number of variables, partial table is
shown). Latitude and longitude information are combined with variables.
Performance measure
Error rate: Your model will be scored based on your weighted mean absolute percentage error over
the whole test period during the competition phase.
Note that you will be compared to a baseline method as a competitor. Baseline uses the most recent
day’s same hour’s production (i.e. 2 days ago, same hour). This is sometime called “persistence
approach”. In the time series context, this will be lag 48 value.
Project Timeline
Test Phase: This is the time period between May 6th and 12th 2024 (both included) dedicated to testing
the submission system. The aim is to make you familiar to online submissions.
Competition Phase: This is the period in which you will be evaluated based on your submissions.
The period is between May 13-May 26, 2024 (both included).
Note that the dates indicate the forecasted dates. For example, competition phase starts on May
13th, 2024. This means you need to provide your submission before 12:00 pm of May 12th, 2024 for
the next day (i.e. April 13th, 2024) in our prediction setting.
Prediction and Report
Note that 30% of your project grade will be determined by your final rank in this competition. First
place will get full points (30 points) and this will decrease to a minimum of 15 points proportional to
your deviation from the top performer (assuming that you did not miss any day during the
competition phase). Moreover, you will lose 1 points (out of 30 points if you miss to submit a
prediction during the competition phase.
You are required to submit a written report with a brief description of your final method, how you
evaluated your methods, and you choose the parameter settings. Note that you can try different
models during the competition phase of the project however you are expected to evaluate your
approaches from February 1st to May 15th of 2024 in your report.
Your report should have the following format:
• Introduction: Problem description, summary of the proposed approach, descriptive analysis of
the given data.
• Related literature: Summarize relevant literature if there is any
• Approach: Explain your approach to this problem.
• Results: Provide your results and discussion.
• Conclusions and Future Work: Summarize your findings and comments regarding your
approach. What are possible extensions to have a better approach?
• Code: Provide the Github link for your codes at the end of your report.
