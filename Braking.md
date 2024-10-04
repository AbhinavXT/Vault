
Section 3.2.8.2.3 focuses on calculating a speed margin for the Emergency Brake Intervention (EBI), represented by a variable called  dV_{\text{ebi}} , which is crucial to ensuring that the emergency brake is applied in time for safe deceleration. The formula helps determine how much speed can exceed a minimum safe speed before the emergency brake is triggered.

Formula:


dV_{\text{ebi}} = \min \left\{ dV_{\text{ebi\min}} + C{\text{ebi}} \times (V_{\text{MRSP}} - V_{\text{ebi\min}}), dV{\text{ebi\_max}} \right\}


Where:

	•	 dV_{\text{ebi}} : The margin or speed difference at which emergency brake intervention happens.
	•	 dV_{\text{ebi\_min}} : Minimum speed margin for emergency brake intervention.
	•	 dV_{\text{ebi\_max}} : Maximum speed margin for emergency brake intervention.
	•	 V_{\text{MRSP}} : Most Restrictive Speed Profile, which is the current speed limit for the train based on track conditions.
	•	 V_{\text{ebi\_min}} : The minimum value for the speed at which the emergency brake should start.
	•	 C_{\text{ebi}} : A proportionality constant that helps scale the speed margin as the difference between  V_{\text{MRSP}}  and  V_{\text{ebi\_min}}  increases.

The constant  C_{\text{ebi}}  is calculated as:


C_{\text{ebi}} = \frac{dV_{\text{ebi\max}} - dV{\text{ebi\min}}}{V{\text{ebi\max}} - V{\text{ebi\_min}}}


What the Formula Does:

This formula determines how much speed margin should be allowed before the emergency brake intervenes, based on the train’s speed limit ( V_{\text{MRSP}} ) and certain predefined thresholds ( dV_{\text{ebi\min}} ,  dV{\text{ebi\_max}} ).

	1.	When the Train is Traveling Slowly:
	•	If the current speed  V_{\text{MRSP}}  is close to  V_{\text{ebi\min}} , the speed margin  dV{\text{ebi}}  will be near the minimum value  dV_{\text{ebi\_min}} . This ensures that the emergency brake doesn’t trigger prematurely at low speeds.
	2.	When the Train is Traveling Faster:
	•	As the train’s speed  V_{\text{MRSP}}  increases, the speed margin  dV_{\text{ebi}}  also increases proportionally (controlled by  C_{\text{ebi}} ) until it reaches the maximum allowed margin  dV_{\text{ebi\_max}} .
	3.	Upper Bound Check:
	•	The formula ensures that the speed margin does not exceed  dV_{\text{ebi\max}} . If the calculation gives a value higher than  dV{\text{ebi\_max}} , it is capped at that maximum value.

Purpose of the Formula:

The formula’s purpose is to dynamically adjust the speed margin for emergency brake intervention based on how fast the train is moving. It provides a larger margin (allowing for more speed) when the train is moving faster and a smaller margin when the train is slower. This way, the emergency brake is only applied when necessary, with appropriate sensitivity based on speed.


The constant  C_{\text{ebi}}  is necessary to provide a proportional adjustment to the emergency brake intervention margin  dV_{\text{ebi}}  based on the train’s current speed, ensuring smooth and safe operation under varying speeds. Here’s why  C_{\text{ebi}}  is important:

1. Gradual Scaling of the Speed Margin:

Without  C_{\text{ebi}} , the emergency brake intervention margin  dV_{\text{ebi}}  would be fixed and static. However, the speed at which a train travels can vary significantly (from low speeds near stations to high speeds on open tracks). A fixed margin may either be too strict at high speeds or too loose at low speeds, which can result in:

	•	Unnecessary Emergency Brake Applications at Low Speeds: If the margin is too tight at low speeds, even small deviations could trigger the emergency brake, disrupting smooth train operation and causing inconvenience.
	•	Insufficient Braking at High Speeds: If the margin is too large at high speeds, it may delay the brake intervention, creating safety risks if the train exceeds the permitted speed for too long.

2. Proportional Response to Speed:

The constant  C_{\text{ebi}}  ensures that the margin grows proportionally as the train’s speed increases. The formula:


C_{\text{ebi}} = \frac{dV_{\text{ebi\max}} - dV{\text{ebi\min}}}{V{\text{ebi\max}} - V{\text{ebi\_min}}}


creates a proportional factor that adjusts the speed margin  dV_{\text{ebi}}  based on how close the current speed  V_{\text{MRSP}}  is to the upper or lower limits. As the train goes faster, the margin increases, and as the train slows down, the margin decreases. This flexibility is important to:

	•	Allow more tolerance at high speeds: At higher speeds, a small deviation from the speed limit is less critical for safety, so a larger margin can be allowed before triggering emergency brakes.
	•	Ensure tight control at low speeds: At lower speeds, safety is more sensitive to even small deviations, so the margin should be smaller to ensure quick intervention if needed.