# @Keyframes

Keyframes are written as percentages. `0%` refers to the start of the animation, `50%` to the middle, `100%` to the end, and so on.

Additionally, if an animation has two states (the first and last), we can use simplified notation by writing the `from` and `to` keywords. The `rotation` keyframe below, for example, describes a full rotation from `0deg` to `360deg`, defined using two `rotate()` values of the `transform` property:

```css
@keyframes rotation {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}
```

# Animations
Animations are applied to HTML elements using the `animation` property.

To make an animation work, we'll also need to set two sub-properties:

-   `animation-name` specifies the name of the `@keyframes` at-rule.
-   `animation-duration` sets out the total duration of the animation.

```css
div {
  animation-name: move;
  animation-duration: 2s;
}

/* or */

div {
  animation: move 2s;
}
```

-   `animation-delay`: The delay before the animation starts (in seconds).
-   `animation-iteration-count`: This value specifies how many times the animation will play. This property takes an integer value, but you can use the `infinite` keyword if you want your animation to repeat indefinitely.
-   `animation-direction`: The direction of the animation. There are four possible values for this and they can be set with keywords. You can play your animation from start to end, with the value `normal`; from end to start with `reverse`; from start to end and back to start with `alternate`; or from end to start and back to end with `alternate-reverse`.
-   `animation-timing-function`: You can use this property to specify the trajectory of the animation as a function of progression over time. We studied something similar for the `transition` property. You can set it as a [Bezier cube](https://cubic-bezier.com/) or with keywords (`linear`, `ease-in`, `ease-in-out`, `ease`, `ease-out`).
-   `animation-fill-mode`: Indicates how the element will behave after the animation finishes. For example, a value of `forwards` keeps the element in its final state, while `backwards` returns the element to its initial state.
-   `animation-play-state`: Specifies whether or not the animation has started. The `running` value launches the animation, while `paused` stops it. This property is often controlled through JavaScript, starting and stopping the animation when different events occur.

```css
div {
  animation-name: move;
  animation-duration: 2s;
  animation-timing-function: ease-in-out;
  animation-delay: 1s;
  animation-iteration-count: 3;
  animation-direction: reverse;
  animation-fill-mode: forwards;
  animation-play-state: running;
}

div {
  animation: move 2s ease-in-out 1s 3 reverse forwards running;
}
```

You can also assign multiple animations to one element by separating them with a comma:

```css
div {
  animation: move 2s, rotation 5s;
}
```

мой пример:
```css
@keyframes move_bg {
  from {
    background-position: 0 0;
  }
  to {
    background-position: 100px 0;
  }
}

@keyframes rotation {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

.demo__row_size_xs {
  background-image: url('https://pictures.s3.yandex.net/animation_topic/line_xs.svg');
  animation: move_bg 5s linear infinite alternate;
}

.demo__row_size_m {
  background-image: url('https://pictures.s3.yandex.net/animation_topic/line_m.svg');
   animation: move_bg 5s linear infinite alternate;
}

.demo__row_size_s {
  background-image: url('https://pictures.s3.yandex.net/animation_topic/line_s.svg');
   animation: move_bg 3s linear infinite alternate;
}

.demo__row_size_l {
  background-image: url('https://pictures.s3.yandex.net/animation_topic/line_l.svg');
   animation: move_bg 8s linear infinite alternate;
}

.star_size_s {
  width: 310px;
  height: 310px;
  margin-left: -155px;
  margin-top: -155px;
  animation: rotation 40s linear infinite;
}

.star_size_l {
  width: 420px;
  height: 420px;
  margin-left: -210px;
  margin-top: -210px;
  animation: rotation 30s linear infinite;
}

.star_size_m {
  width: 420px;
  height: 420px;
  margin-left: -210px;
  margin-top: -210px;
  animation: rotation 20s linear infinite;
}
```