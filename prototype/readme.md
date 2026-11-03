# MVP demo

[Watch the GrabMate demonstration](GrabMate_Demo.mp4).

The uploaded notebook contains a **Python console-based interactive journey planner**. It resolves known UEH addresses or uses OSM Nominatim, generates feasible modes, estimates costs and travel times and recommends an option. It loads a fitted RandomForest cost model when `model.pkl` exists and uses rule-based cost fallback otherwise. Traffic levels in the prototype are sampled / simulated.

**Not included:** deployed web/mobile app, actual Grab payment/booking, verified real-time integration with transit operators, or independently assessed routing accuracy.

Source: [development notebook](../analysis/GrabMate_EDA_Modeling_Prototype.ipynb).
