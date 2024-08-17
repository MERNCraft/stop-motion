# FAILED CONCEPT #

This works only on Firefox. On Safari, if the element immediately under the mouse changes, the new `:hover` element is not detected until the mouse moves. On Chrome, the animation does not start, or it stops before the custom properties are updated.

In Firefox, an animation is created and immediately `paused`. This sets the value of `--za` to `1`, and `--value` is calculated as 0. The frontmost label is connected to input#b. When this input is checked, the animation is set to `running`. When the animation reaches the first keyframe, `--zb` is set to `1`, so `--value` is recalculated to also be `1`. Now that `--zb` is 1, the `z-index` of `input#b` is set to `1`; `input#b` is now in front of `input#a` (which is checked), and the animation is `paused` again, because it only runs when the label under the mouse (`[for]:hover`) is associated with the `:checked` input.

As a result, the animation pauses with `--value` set to `1`. The next click will be on `input#b`, and the animation will play up to the next keyframe and stop.

In Firefox only.