## 6. Business Recommendations

**1. Prioritize customers whose previous campaign succeeded.**
Customers with a prior campaign success subscribe at **65.4%** this time, versus
**8.9%** for those never contacted before and **13.9%** for those whose last
campaign failed -- nearly 6x the overall average of 11.3%. This is the single
strongest signal in the dataset. Recommendation: before running a new campaign,
pull the list of prior-success customers and contact them first -- they represent
the highest-return, lowest-effort segment available.

**2. Target retired (60+) and student customers as core demographic segments.**
The 60+ age band converts at **45.5%** and students (concentrated in the 18-30
band) convert at **32.9%**, both with reliable group sizes (600-700+ each) --
not statistical flukes. Combined analysis confirmed the 60+ effect holds
regardless of marital status, so it's a genuine age-driven pattern, not a proxy
for something else. Recommendation: weight campaign targeting toward these two
groups over working-age segments (31-50), which convert at roughly a third of
this rate (8-10%).

**3. Cap contact attempts at 3-4 per customer.**
Subscribe rate declines steadily with each additional contact -- from **13.0%**
on the first attempt down to **4-6%** by the 7th-10th attempt. Continuing to
call past 3-4 attempts shows diminishing, and likely negative, returns (repeated
unwanted calls may actively discourage a "yes"). Recommendation: set a hard cap
of 3-4 attempts per customer per campaign cycle, and redirect that effort toward
higher-probability segments instead.

**4. Data limitation, stated for transparency.**
`duration` (call length) is strongly associated with a successful outcome (553s
average for "yes" vs 221s for "no"), but this value is only known *after* a call
ends -- it cannot inform who to call in advance, so it was deliberately excluded
from all targeting conclusions above. Flagging this avoids a common mistake in
this specific dataset: using a feature that looks predictive but is actually
just a byproduct of the outcome itself.

**5. Scope note.**
This analysis focused on actionable segmentation rather than a predictive
model, since the goal was a clear, explainable targeting recommendation a
campaign team could act on directly -- not a black-box probability score. A
classification model (e.g. logistic regression) could be added as a next step
to rank individual customers, but the four recommendations above are usable
immediately without one.
