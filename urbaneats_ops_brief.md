# UrbanEats — 11 AM Ops Review Brief

1. The dataset of 150 orders is ready for analysis, but 6 orders are missing delivery time records — concentrated in Cancelled and Delayed statuses — which would skew any average delivery time calculation if not handled.

2. The single restaurant-zone combination the operations team must address this week is **Spice Garden in the Central zone**, which carries the highest cancellation risk driven primarily by long delivery times and high discount usage in that corridor.

3. Starting tomorrow at 07:30, ops managers will receive an automated daily briefing via Slack and email showing total orders, cancellation rate, worst-performing zone by complaint volume, and the top cancel-risk hotspot — with a red alert triggered whenever cancellation rate crosses 20%.

4. The system cannot account for external factors such as weather, local events, or restaurant-side kitchen delays — 46 of 150 orders are flagged high-risk based on order patterns alone, but the root cause within those 46 cannot be distinguished between rider issues and restaurant prep failures without additional data.

5. After 4 weeks of intervention in the Central zone, the single metric that will confirm it is working is a reduction in the Spice Garden – Central cancellation rate below 30%.
