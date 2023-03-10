# Autosens, Dynamic ISF/ICR and Adjust Basal
!!! abstract "Highlights"
    - Enable Dynamic ISF, Dynamic CR and/or Adjust Basal for more rapid adjustments in response to physiological changes in insulin sensitivity
    - Bias the calculated ISF/CR/Basal rates towards more or less aggressive values by increasing or decreasing the adjustment factor accordingly.
    - Adjustments are limited by autosens max/min.

!!! tip
    Examples in this section employ the default logarithmic formula for calculations. [See the sigmoid section for more information.](sigmoid.md)

## Auto-sensitivity Mode
Auto-sensitivity (autosens) reviews your last 8 hrs and 24 hrs of data every loop cycle (5 min) and determines whether you have been reacting more or less sensitively to insulin. It then makes conservative temporary adjustments to your basal rates, blood sugar target, and ISF.

Example:
Autosens finds Bill has been running more sensitive to insulin lately. In the last 24 hours, he has been 2X more sensitive to insulin, whereas in the last 8 hours, he has been 3X more sensitive to insulin.

Autosens then takes the more conservative calculated sensitivity. In this example, the more conservative value is obtained from the 8 hour window because by assuming Bill is 3X more as opposed to 2X more sensitive to insulin, the system will be posed to give less insulin.

If you are using autotune, autosens will use your calculated autotune ICR, ISF and basal rates as its baseline as opposed to your set values.

Note that autosens does not look at meals and make adjustments to your ICR. It only looks at your sensitivity to insulin and adjust ISF/basal rates/blood sugar targets accordingly.

## Dynamic ISF
Autosens was thought by some to be too conservative and slow at making changes. Dynamic ISF is a drop-in replacement for autosens's ISF calculation formula, with the goal of making it more aggressive. If you find that you have high ISF variability throughout the day and autosens is not providing you with sufficent control, you can turn this feature on.

Dynamic ISF takes into consideration a new variable called "Adjustment Factor" which affects its aggressiveness. If dynamic ISF is too aggressive, you can decrease this number by 0.05-0.1 points to make it more meek. Likewise, increase this number if you still feel dynamic ISF is not aggressive enough.

Notes: 

- Dynamic ISF is temporarily disabled and the system reverts to autosens if either "High Temptarget Raises Sensitivity" or "Exercise Mode" is enabled and a high temporary target has been set by the user.
- While Dynamic ISF is inherently more aggressive, it also provides the user greater control as opposed to autosens via the adjustment factor. You can alter the adjustment factor to make Dynamic ISF less aggressive than the calculated autosens values. 

### Advanced information
Autosens determines an ratio (autosens.ratio) and alters your ISF in the following manner:

- New ISF = (profile set ISF)/(autosens.ratio)

Example: Bill has an ISF of 3 in his settings. The system finds Bill has been more resistant to insulin lately and needs to increase his insulin. It calculates Bill to have an autosens.ratio of 1.1 (note that a larger autosens.ratio results in you having a lower, more aggressive ISF):

When autosens goes to adjust the ISF, it does the following calculation:

- 3 UL/mmol / 1.1 = 2.73 UL/mmol

Bill is now temporarily set to have an ISF of 2.73.

Dynamic ISF (using the default logarithmic algorithm in iAPS) uses an alternative formula to calculate the autosens.ratio for ISF adjustments:

- autosens.ratio = profile.sens * AF * TDD * log((BG/peak)+1) / 1800
- New ISF = (profile set ISF)/(autosens.ratio)

This formula takes into consideration your profile set ISF (profile.sens in mg/dl) current blood glucose (BG in mg/dl), total daily dose (TDD over the last 24 hours), insulin peak effect (peak activity normally is 120 min) and a new variable called adjustment factor (AF) that allows for user tuning of Dynamic ISF/CR.

[Click here to view a graph despicting the logarithmic formula](https://www.desmos.com/calculator/yat7mguwqb)

## Dynamic CR
This is an experimental feature that alters the carb ratio (CR) based on current blood sugar and total daily dose (TDD). Unlike ISF, ICR was not originally altered by autosens with respect to your detected sensitivty. Using Dynamic CR will lead to a dramatic change in how ICR is calculated by iAPS. Dynamic CR uses a similar formula as Dynamic ISF as described above:

- autosens.ratio = profile.sens * AF * TDD * log((BG/peak)+1) / 1800
- New CR = (profile set CR)/(autosens.ratio)

If you find your CR changes dramatically day to day and iAPS is not providing adequate bolus recommendations, you can test this feature. Note that iAPS is already makes modifications to your recommended boluses without this feature enabled based on your blood glucose target, COB, and IOB.

!!! note
    If the calculated autosens.ratio by Dynamic CR is greater than 1, the following formula is used to make the resulting CR less aggressive: 

    - new.autosens.ratio = (autosens.ratio - 1)/2 + 1 
    

## Adjust Basal
Adjust basal replaces autosens's formula for adjusting basal rates, with one dependent on total daily dose (TDD) of insulin. Turn on this setting to give basal adjustments more agility. Keep this setting off if you basal needs are not highly variable.

### Advanced Information
Normally a new basal rate is set by autosens:

- New basal profile = current basal profile * autosens.ratio

Adjust basal replaces the autosens.ratio with its own autosens.ratio calculated as such:

- autosens.ratio = (weighted average of TDD)/(2 week average of TDD)
- New basal profile = current basal profile * autosens.ratio

See "Weighted Average of TDD" setting to understand how this variable is calculated.

As an example:

Bill has a TDD of 55 U over the last 24 hours. He has a 14 day TDD average of 48 U. He has set his "Weighted average of TDD" in preferences to 0.7. His current profile basal rate is 1 U/h.

- Weighted average of TDD = 0.7 * 55 U + 0.3 * 48 U = 52.9 U
- basal.autosens.ratio = 52.9 U / 48 U = 1.10
- New basal profile = 1 U/h * 1.10 = 1.10 U/h


## Final Thoughts
- Remember that all autosens ratios calculated in this section are being limited by autosens max and autosens min safety limiters. Additionally, Dynamic CR has an inbuilt safety limiter against highly aggressive ratios.