Чтобы найти предел $\lim\limits_{n \to \infty} \alpha_n$ для функции

$$
\alpha_n = \frac{\pi^{n/2}}{32 \cdot \Gamma\left(\frac{n}{2} + 1\right)} \cdot (3{,}937)^{n-5},
$$

проведём **строгий асимптотический анализ** по шагам.

### Шаг 1. Перепишем формулу в удобном виде
Выделим множитель, не зависящий от *n*, и объединим степенные части:

$$
\alpha_n = \frac{(3{,}937)^{-5}}{32} \cdot \frac{(\pi^{1/2} \cdot 3{,}937)^n}{\Gamma\left(\frac{n}{2} + 1\right)} = C \cdot \frac{K^n}{\Gamma\left(\frac{n}{2} + 1\right)},
$$

где:
- $C = \dfrac{(3{,}937)^{-5}}{32}$ ≈ $5{,}96 \times 10^{-5}$ — константа;  
- $K = \sqrt{\pi} \cdot 3{,}937 \approx 1{,}772 \cdot 3{,}937 \approx 6{,}976$.


Итак:

$$
\alpha_n \sim C \cdot \frac{K^n}{\Gamma(n/2 + 1)}, \quad K \approx 6{,}976.
$$

### Шаг 2. Асимптотика гамма‑функции (формула Стирлинга)
Для $z = \dfrac{n}{2} + 1$ при $n \to \infty$:

$$
\Gamma(z) \sim \sqrt{2\pi} \, z^{z - 1/2} e^{-z}.
$$

Подставим $z = \dfrac{n}{2} + 1$:

$$
\Gamma\left(\frac{n}{2} + 1\right) \sim \sqrt{2\pi} \left(\frac{n}{2} + 1\right)^{n/2 + 1/2} e^{-(n/2 + 1)}.
$$

Для больших *n* приближаем:

$$
\frac{n}{2} + 1 \approx \frac{n}{2}, \quad \text{тогда} \quad \Gamma\left(\frac{n}{2} + 1\right) \sim \sqrt{2\pi} \left(\frac{n}{2}\right)^{n/2 + 1/2} e^{-n/2}.
$$

### Шаг 3. Подставляем в αₙ и упрощаем

$$
\alpha_n \sim C \cdot \frac{K^n}{\sqrt{2\pi} \left(\frac{n}{2}\right)^{n/2 + 1/2} e^{-n/2}} = \frac{C}{\sqrt{2\pi}} \cdot \frac{K^n \cdot e^{n/2}}{\left(\frac{n}{2}\right)^{n/2} \cdot \left(\frac{n}{2}\right)^{1/2}}.
$$

Упростим степенные части:
- $\left(\dfrac{n}{2}\right)^{n/2} = \dfrac{n^{n/2}}{2^{n/2}}$;  
- $\left(\dfrac{n}{2}\right)^{1/2} = \dfrac{n^{1/2}}{2^{1/2}}$.


Тогда:

$$
\alpha_n \sim \frac{C}{\sqrt{2\pi}} \cdot \frac{K^n \cdot e^{n/2} \cdot 2^{n/2} \cdot 2^{1/2}}{n^{n/2} \cdot n^{1/2}} = \frac{C \sqrt{2}}{\sqrt{2\pi}} \cdot \frac{(K \sqrt{2e})^n}{n^{n/2 + 1/2}}.
$$

Обозначим $A = K \sqrt{2e} \approx 6{,}976 \cdot \sqrt{5{,}436} \approx 6{,}976 \cdot 2{,}332 \approx 16{,}26$. Тогда:

$$
\alpha_n \sim D \cdot \frac{A^n}{n^{n/2 + 1/2}}, \quad D = \frac{C \sqrt{2}}{\sqrt{2\pi}} = \frac{C}{\sqrt{\pi}}.
$$

### Шаг 4. Анализируем поведение при *n* → ∞
Рассмотрим логарифм αₙ:

$$
\ln \alpha_n \sim \ln D + n \ln A - \left(\frac{n}{2} + \frac{1}{2}\right) \ln n.
$$

Вынесем *n*:

$$
\ln \alpha_n \sim n \left(\ln A - \frac{1}{2} \ln n\right) - \frac{1}{2} \ln n + \ln D.
$$

При $n \to \infty$:  
- $\ln n \to \infty$, поэтому $\ln A - \dfrac{1}{2} \ln n \to -\infty$;  
- главный член: $n \left(\ln A - \dfrac{1}{2} \ln n\right) \to -\infty$.


Следовательно:

$$
\ln \alpha_n \to -\infty \quad \Rightarrow \quad \alpha_n \to 0.
$$

### Шаг 5. Скорость стремления к нулю
Перепишем αₙ через экспоненту:

$$
\alpha_n \sim D \cdot \exp\left[n \ln A - \left(\frac{n}{2} + \frac{1}{2}\right) \ln n\right] = D \cdot \exp\left[-n \left(\frac{1}{2} \ln n - \ln A\right) - \frac{1}{2} \ln n\right].
$$

Показатель степени растёт по модулю как $n \ln n$, поэтому αₙ стремится к нулю **быстрее любой экспоненты** (но медленнее, чем $e^{-n^2}$).

### Итоговый ответ

$$
\boxed{\lim_{n \to \infty} \alpha_n = 0}
$$

**Обоснование:**  
1. Числитель $K^n$ растёт экспоненциально ($K \approx 6{,}976$).  
2. Знаменатель $\Gamma(n/2 + 1)$ растёт **суперэкспоненциально** (по формуле Стирлинга).  
3. В итоге знаменатель «перевешивает», и $\alpha_n \to 0$ при $n \to \infty$.


**Дополнительные выводы:**  
- **Положение максимума** αₙ можно найти, приравняв $\dfrac{\alpha_{n+1}}{\alpha_n} = 1$. Это даст $n_{\text{max}} \approx 49$ (как в предыдущем расчёте).  
- **Эффективный параметр** $A = K \sqrt{2e} \approx 16{,}26$ связан с вашим $K$ из ранних рассуждений.  
- **Скорость убывания** αₙ определяется членом $n^{n/2}$ в знаменателе.
