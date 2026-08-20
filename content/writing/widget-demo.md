+++
title = "Interactive widget demo"
description = "placeholder post showing the math + widget pattern"
date = 2026-08-20

[extra]
math = true
+++

This is a placeholder post demonstrating the two "rich content" patterns.
Delete it once you have real posts.

## Math

Inline math like $e^{i\pi} + 1 = 0$ works, and so does display math:

$$
\int_{-\infty}^{\infty} e^{-x^2}\,dx = \sqrt{\pi}
$$

Setting `math = true` in a post's front matter loads KaTeX for that page only.
Pages without it ship zero JavaScript.

## A widget

Widgets are just inline HTML + vanilla JS in the markdown. No framework.

<label>
  Frequency: <input type="range" id="freq" min="1" max="10" value="3" step="0.1">
</label>
<canvas id="sine" width="600" height="150" style="width:100%; border:1px solid #ddd;"></canvas>

<script>
const canvas = document.getElementById('sine');
const ctx = canvas.getContext('2d');
const slider = document.getElementById('freq');
function draw() {
  const f = parseFloat(slider.value);
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  ctx.beginPath();
  for (let x = 0; x < canvas.width; x++) {
    const y = canvas.height / 2 * (1 - 0.8 * Math.sin(2 * Math.PI * f * x / canvas.width));
    x === 0 ? ctx.moveTo(x, y) : ctx.lineTo(x, y);
  }
  ctx.strokeStyle = '#14640a';
  ctx.lineWidth = 2;
  ctx.stroke();
}
slider.addEventListener('input', draw);
draw();
</script>
