---
layout: post
title: An interesting pattern in the digits of various infinite series
---
{% include mathjax.html %}

## **An interesting pattern**

Perhaps the most well-known infinite series for $$\pi$$ is the Leibniz formula

$$\pi=\sum_{n=1}^{\infty}(-1)^{n+1}\frac{4}{2n-1}=\frac{4}{1}-\frac{4}{3}+\frac{4}{5}-\frac{4}{7}+\cdots$$

Unfortunately, while this formula is very simple and easy to remember, it converges extremely slowly. Let $$a_n=4/(2n-1)$$ and let $$\pi_N$$ be the above series truncated after $$N$$ terms. Then by the alternating series test, we have $$\left\vert\pi_N-\pi\right\vert\leq a_{N+1}\sim 2/N$$ as an upper bound for the error. This estimate for the error turns out to be of the correct order, which implies that if we want to calculate $$d$$ digits of $$\pi$$, we need to take $$N$$ to be exponential in $$d$$.

Let's make a table of $$\pi_{10^k}$$ for various values of $$k$$, so we can see just how slowly the sum converges.

$$\begin{array}{c|c}
 k & \pi_{10^k} \\
 \hline
 0 & 4.000000000000000000000000000000 \\
 1 & \color{green}{3}.041839618929402211135957265988 \\
 2 & \color{green}{3.1}31592903558552764307414238276 \\
 3 & \color{green}{3.14}0592653839792925963596502869 \\
 4 & \color{green}{3.141}492653590043238459518383374 \\
 5 & \color{green}{3.1415}82653589793488462643352029 \\
 6 & \color{green}{3.14159}1653589793238712643383279 \\
 7 & \color{green}{3.141592}553589793238462893383279 \\
 8 & \color{green}{3.1415926}43589793238462643633279 \\
 9 & \color{green}{3.14159265}2589793238462643383529 \\
 \hline
 \infty & \color{green}{3.141592653589793238462643383279}
\end{array}$$

So very slowly indeed. Even summing 10 trillion ($$10^{13}$$) terms gives a worse approximation than a *single term* of the [Chudnovsky formula][1].

However, looking at this table, there is clearly something more interesting going on. After the first incorrect digit, the next few digits are correct again! This seems like very strange behaviour. Usually when we calculate an approximation of an infinite series, product, limit, etc. the first few digits will be correct and the rest will appear totally random.

Let's rewrite the table but with greater precision, and let's highlight all of the correct and incorrect digits.

$$\begin{array}{c|c}
 k & \pi_{10^k} \\
 \hline
 0 & \color{red}{4.0000000000000000000000000000000}\color{green}{0}\color{red}{00000000000000000}\color{green}{0}\color{red}{000}\color{green}{0}\color{red}{000000} \\
 1 & \color{green}{3.}\color{red}{0}\color{green}{41}\color{red}{839}\color{green}{6}\color{red}{1892}\color{green}{9}\color{red}{402}\color{green}{2}\color{red}{1113595726598822574054}\color{green}{7}\color{red}{7219718}\color{green}{7}\color{red}{057868172}\color{green}{4}\color{red}{192} \\
 2 & \color{green}{3.1}\color{red}{3}\color{green}{1592}\color{red}{90}\color{green}{35}\color{red}{58552764307414238}\color{green}{27}\color{red}{6920516403054}\color{green}{3}\color{red}{8440657}\color{green}{5}\color{red}{651389662} \\
 3 & \color{green}{3.14}\color{red}{0}\color{green}{592653}\color{red}{83}\color{green}{979}\color{red}{29259}\color{green}{6}\color{red}{359650286}\color{green}{9}\color{red}{39597045138}\color{green}{93}\color{red}{307}\color{green}{7}\color{red}{9724489367457} \\
 4 & \color{green}{3.141}\color{red}{4}\color{green}{926535}\color{red}{9004}\color{green}{32384}\color{red}{59518}\color{green}{383}\color{red}{3}\color{green}{7}\color{red}{481537878}\color{green}{7}\color{red}{013642744}\color{green}{1}\color{red}{8046}\color{green}{0}\color{red}{513479} \\
 5 & \color{green}{3.1415}\color{red}{8}\color{green}{2653589793}\color{red}{48}\color{green}{84626433}\color{red}{5202}\color{green}{95028}\color{red}{9372841}\color{green}{939}\color{red}{3964949575}\color{green}{9}\color{red}{08635} \\
 6 & \color{green}{3.14159}\color{red}{1}\color{green}{653589793238}\color{red}{71}\color{green}{2643383279}\color{red}{1903}\color{green}{841971}\color{red}{70}\color{green}{3}\color{red}{52500}\color{green}{1058}\color{red}{1556}\color{green}{4}\color{red}{788} \\
 7 & \color{green}{3.141592}\color{red}{5}\color{green}{53589793238462}\color{red}{89}\color{green}{338327950288}\color{red}{1072}\color{green}{169399375}\color{red}{2}\color{green}{0}\color{red}{11334}\color{green}{74944} \\
 8 & \color{green}{3.1415926}\color{red}{4}\color{green}{3589793238462643}\color{red}{63}\color{green}{32795028841971}\color{red}{3814}\color{green}{93751058209}\color{red}{8}\color{green}{4}\color{red}{475} \\
 9 & \color{green}{3.14159265}\color{red}{2}\color{green}{589793238462643383}\color{red}{52}\color{green}{9502884197169399}\color{red}{0626}\color{green}{05820974944} \\
 \hline
 \infty & \color{green}{3.141592653589793238462643383279502884197169399375105820974944}
\end{array}$$

The pattern of correct and incorrect digits in $$\pi_{10^k}$$ really stands out as $$k$$ increases. We can pick out the following patterns quite clearly:
- the first incorrect digit appears after $$k$$ correct digits, and is always $$1$$ too low
- the second block of incorrect digits appears after roughly $$3k$$ digits, and is always $$25=5^2$$ too high
- the third block of incorrect digits appears after roughly $$5k$$ digits, and is always $$3125=5^5$$ too low
- the fourth block of incorrect digits appears after roughly $$7k$$ digits, and is always $$953125=5^6\cdot 61$$ too high
- ...

This suggests the existence of an asymptotic error formula (an infinite sequence of "correction" terms) that can be added to $$\pi_N$$ to yield approximations with a much smaller error. Moreover, with a bit of experimentation, the patterns we noticed above seem to suggest that this asymptotic series begins

$$\pi\stackrel{?}{=}\pi_N+\frac{1}{N}-\frac{1}{4N^3}+\frac{5}{16N^5}-\frac{61}{64N^7}+\cdots$$

so we expect some sort of alternating series in odd powers of $$1/N$$. The powers of 2 in the denominators, and the fact that the blocks of incorrect digits differed from the correct digits by multiples of powers of 5, seems to suggest that maybe we should *halve* the number of terms we are summing. By replacing $$N$$ with $$N/2$$ in the above formula, we eliminate the powers of 2 from the denominators. This isn't necessary to do of course, it just makes things a bit simpler. Looking at the case where the number of terms is now half of a power of 10, we get the asymptotic formula

$$\pi\stackrel{?}{=}\pi_{5\cdot 10^{k-1}}+\frac{2\cdot 1}{10^{k}}-\frac{2\cdot 1}{10^{3k}}+\frac{2\cdot 5}{10^{5k}}-\frac{2\cdot 61}{10^{7k}}+\cdots$$

resulting in approximations with smaller blocks of incorrect digits:

$$\begin{array}{c|c}
 k & \pi_{5\cdot 10^{k-1}} \\
 \hline
 1 & \color{green}{3.}\color{red}{33968}\color{green}{2}\color{red}{5396}\color{green}{8}\color{red}{2539682539}\color{green}{6}\color{red}{82539682}\color{green}{5}\color{red}{396}\color{green}{8}\color{red}{253968253}\color{green}{9}\color{red}{682539682539682} \\
 2 & \color{green}{3.1}\color{red}{2}\color{green}{159}\color{red}{4}\color{green}{65}\color{red}{2}\color{green}{5}\color{red}{9101047}\color{green}{8}\color{red}{51318297430}\color{green}{9}\color{red}{49}\color{green}{2}\color{red}{4329217}\color{green}{69}\color{red}{645}\color{green}{37}\color{red}{1316046487107} \\
 3 & \color{green}{3.1}\color{red}{39}\color{green}{59265}\color{red}{5}\color{green}{5897}\color{red}{8}\color{green}{3238}\color{red}{584}\color{green}{64}\color{red}{061}\color{green}{3}\color{red}{380}\color{green}{5}\color{red}{39479065852583159834568147197} \\
 4 & \color{green}{3.141}\color{red}{3}\color{green}{926535}\color{red}{91}\color{green}{793238}\color{red}{3}\color{green}{626433}\color{red}{954}\color{green}{7950}\color{red}{011}\color{green}{419}\color{red}{8}\color{green}{1}\color{red}{7}\color{green}{9}\color{red}{818834553219696518} \\
 5 & \color{green}{3.1415}\color{red}{7}\color{green}{265358979}\color{red}{5}\color{green}{23846264}\color{red}{2}\color{green}{38327950}\color{red}{410}\color{green}{419716}\color{red}{662}\color{green}{93751}\color{red}{1}\color{green}{5}\color{red}{9}\color{green}{2}\color{red}{51}\color{green}{74}\color{red}{890} \\
 6 & \color{green}{3.14159}\color{red}{0}\color{green}{6535897932}\color{red}{40}\color{green}{4626433832}\color{red}{6}\color{green}{9502884197}\color{red}{291}\color{green}{39937510}\color{red}{305}\color{green}{0974944} \\
 7 & \color{green}{3.141592}\color{red}{4}\color{green}{5358979323846}\color{red}{4}\color{green}{643383279502}\color{red}{7}\color{green}{841971693993}\color{red}{873}\color{green}{0582097494}\color{red}{1} \\
 8 & \color{green}{3.1415926}\color{red}{3}\color{green}{358979323846264}\color{red}{5}\color{green}{38327950288419}\color{red}{6}\color{green}{16939937510582}\color{red}{219}\color{green}{4944} \\
 9 & \color{green}{3.14159265}\color{red}{1}\color{green}{58979323846264338}\color{red}{5}\color{green}{2795028841971693}\color{red}{8}\color{green}{9375105820974944} \\
 \hline
 \infty & \color{green}{3.141592653589793238462643383279502884197169399375105820974944}
\end{array}$$

which is quite impressive to look at. The question, then, is what *is* the error series? What are the numbers $$1, 1, 5, 61, \dots$$ that we see appearing in the numerators?

Exercise for the reader: use the table above to predict the next two terms of the error series, and hence the next two terms of the sequence $$1, 1, 5, 61, \dots$$.

## **Generalised Harmonic Numbers**

In calculus, we often study the Taylor/power series expansion of a function $$f$$ at a point $$c$$,

$$f(x)=f(c)+f'(c)(x-c)+f''(c)\frac{(x-c)^2}{2!}+f^{(3)}(x-c)\frac{(x-c)^3}{3!}+\cdots$$

which "converts" information about the derivatives of $$f$$ at a single point $$c$$ into information about the value of $$f$$ for points $$x$$ close to $$c$$. This can be generalised to the power series at infinity, by considering the power series of $$f(1/x)$$ at zero.

For a simple example, consider $$f(x)=1/(1-x)$$. This function has perhaps the most well-known of all power series at $$0$$, namely the geometric series $$f(x)=1+x+x^2+x^3+\cdots$$, which converges for $$\left\vert x\right\vert\lt 1$$. However, we can also take the power series at infinity. We have $$f(1/x)=-x/(1-x)=-x-x^2-x^3-\cdots$$, so the power series at infinity is

$$f(x)=-\frac{1}{x}-\frac{1}{x^2}-\frac{1}{x^3}-\cdots$$

which converges for $$\left\vert 1/x\right\vert\lt 1$$, or equivalently, for $$\left\vert x\right\vert\gt 1$$.

Our desired asymptotic formula for $$\pi_N$$ looks like a power series at infinity. We can't directly use this fact though, because our function $$\pi_N$$ is only defined when $$N$$ is an integer, so it makes no sense to talk about its derivatives. Ideally, we would like to extend the definition of the series to a "nice" function defined on the reals so that we can use tools from analysis.

We will define a function $$H$$ that generalises our series $$\pi_N$$ and allows us to study any series whose terms look like the reciprocal of a first degree polynomial.

The *harmonic numbers* are the simplest series of this form, defined by

$$H_n=\sum_{k=1}^{n}\frac{1}{k}=1+\frac{1}{2}+\cdots+\frac{1}{n}$$

If we wish to generalise this to a function taking a real number as input, then the first problem that we need to fix is the fact that the parameter $$n$$ appears as the upper limit of a sum. A clever but simple solution to this problem is to rewrite the series as the infinite telescoping series

$$\begin{aligned}
H_n &= \color{green}{1+\frac{1}{2}+\cdots+\frac{1}{n}} \\
&= \left(\color{green}{1}\color{red}{-\frac{1}{n+1}}\right)+\left(\color{green}{\frac{1}{2}}\color{blue}{-\frac{1}{n+2}}\right)+\cdots+\left(\color{green}{\frac{1}{n}}-\frac{1}{2n}\right)+\left(\color{red}{\frac{1}{n+1}}-\frac{1}{2n+1}\right)+\left(\color{blue}{\frac{1}{n+2}}-\frac{1}{2n+2}\right)+\cdots \\
&= \sum_{k=1}^{\infty}\left(\frac{1}{k}-\frac{1}{k+n}\right)
\end{aligned}$$

The green terms are all of the original terms that are not cancelled out by any term in the sum. The two red terms are the first pair of terms to cancel, and the two blue terms are the second pair to cancel. The $$-1/(2n)$$ term will be cancelled later when the term $$1/(2n)-1/(3n)$$ is added, and so on.

In fact, that is all we need to do to generalise $$H_n$$. We can now define the *generalised harmonic number*

$$H(x)=\sum_{k=1}^{\infty}\left(\frac{1}{k}-\frac{1}{k+x}\right)$$

for any real number $$x$$, except the negative integers (because we would have $$k+x=0$$ in one of the terms). We can now write a general "harmonic-like" sum in terms of $$H(x)$$

$$\begin{aligned}
\sum_{k=1}^{n}\frac{1}{ak+b} &= \frac{1}{a}\sum_{k=1}^{n}\frac{1}{k+\frac{b}{a}} \\
&= \frac{1}{a}\sum_{k=1}^{\infty}\left(\frac{1}{k+\frac{b}{a}}-\frac{1}{k+\frac{b}{a}+n}\right) \\
&= \frac{1}{a}\sum_{k=1}^{\infty}\left(\left(\frac{1}{k}-\frac{1}{k+\frac{b}{a}+n}\right)-\left(\frac{1}{k}-\frac{1}{k+\frac{b}{a}}\right)\right) \\
&= \frac{1}{a}\left[\sum_{k=1}^{\infty}\left(\frac{1}{k}-\frac{1}{k+\frac{b}{a}+n}\right)-\sum_{k=1}^{\infty}\left(\frac{1}{k}-\frac{1}{k+\frac{b}{a}}\right)\right] \\
&= \frac{1}{a}\left(H\left(\frac{b}{a}+n\right)-H\left(\frac{b}{a}\right)\right)
\end{aligned}$$

Exercise for the reader: use this formula or perform a similar calculation to verify the following equations (when $$N$$ is even).

$$\pi_N=\left[H\left(\frac{N}{2}-\frac{3}{4}\right)-H\left(-\frac{3}{4}\right)\right]-\left[H\left(\frac{N}{2}-\frac{1}{4}\right)-H\left(-\frac{1}{4}\right)\right]$$

$$\pi=H\left(-\frac{1}{4}\right)-H\left(-\frac{3}{4}\right)$$

Subtracting these equations, we have $$\pi-\pi_N=H\left(\frac{N}{2}-\frac{1}{4}\right)-H\left(\frac{N}{2}-\frac{3}{4}\right)$$ which is precisely the error term we are interested in. All we need now is an asymptotic expansion of $$H(\alpha x+\beta)$$ for arbitrary constants $$\alpha,\beta$$, which will tell us everything we want to know about the asymptotics of all harmonic-like series.

## **Approximating sums by integrals**

In introductory calculus, we learn that the area under a curve can be defined by first approximating the area using rectangles, and then increasing the number of rectangles to infinity by taking a limit. This limit is then called the *integral* of the function. We also learn that integrals can be very difficult to evaluate exactly and that for practical applications, a sufficiently close approximation of the integral is often good enough. This leads to the study of integral approximation formulas, the simplest of which comes directly from the definition: approximate the area by rectangles

$$\int_a^b f(x)dx\approx h\left(f(x_0)+\cdots+f(x_n)\right)$$

where $$h=(b-a)/n$$ and $$x_i=a+ih$$. This approximation is usually pretty bad. The error turns out to be proportional to the derivative of $$f$$ (for fixed $$a,b,n$$), so this is a *zeroth order* approximation.

A better approximation is the trapezium rule, which as the name suggests, uses trapeziums instead of rectangles to approximate the area

$$\begin{aligned}
\int_a^b f(x)dx &\approx h\left(\frac{f(x_0)+f(x_1)}{2}+\cdots+\frac{f(x_{n-1})+f(x_n)}{2}\right) \\
&= h\left(f(x_0)+\cdots+f(x_n)\right)-h\left(\frac{f(x_0)+f(x_n)}{2}\right)
\end{aligned}$$

The error in this approximation is proportional to the second derivative of $$f$$, so the trapezium rule gives a *first order* approximation of the integral. Notice also that this is just the rectangle approximation formula with an extra term added on. Naturally, we can ask if there are more terms that can be added on to get higher order approximations.

The answer to this question is *yes*, there are approximation formulas like these of all degrees, and we can write even down a formula for all of them. For simplicity, let's take $$h=1$$ and $$a,b$$ to be integers. Then we have

$$\int_a^b f(x)dx=
\underbrace{\sum_{n=a}^{b}f(n)}_{\text{Rectangles}}
-\underbrace{\frac{f(a)+f(b)}{2}}_{\text{Trapezium term}}
-\underbrace{\sum_{n=2}^{m}\frac{B_n}{n!}\left(f^{(n-1)}(b)-f^{(n-1)}(a)\right)}_{\text{Higher order correction terms}}
-\underbrace{R_{m}}_{\text{Error term}}$$

where $$m$$ is the order of the approximation and $$B_n$$ are constants known as the *Bernoulli numbers*, the first few of which are listed in the table below.

$$\begin{array}{c|ccccccccccccccccc}
 n & 0 & 1 & 2 & 3 & 4 & 5 & 6 & 7 & 8 & 9 & 10 & 11 & 12 & 13 & 14 \\
 \hline
 B_n & 1 & -\frac{1}{2} & \frac{1}{6} & 0 & -\frac{1}{30} & 0 & \frac{1}{42} & 0 & -\frac{1}{30} & 0 & \frac{5}{66} & 0 & -\frac{691}{2730} & 0 & \frac{7}{6} \\
\end{array}$$

This is the Euler Maclaurin formula. Although we are currently interpreting it as a general formula for numerical integration, its main use actually comes when we use the formula *in reverse*, to approximate sums by integrals, and this is how the formula is usually presented.

$$\sum_{n=a}^{b}f(n)=\int_a^b f(x)dx+\frac{f(a)+f(b)}{2}+\sum_{n=2}^{m}\frac{B_n}{n!}\left(f^{(n-1)}(b)-f^{(n-1)}(a)\right)+R_{m}$$

There is a lot to be said about this formula and it really deserves a post of its own to explain all of the details we will use, which I plan to write in the near future. For now, we will just use the formula.

## **Asymptotic expansion of the Harmonic Numbers**

We will first derive the asymptotic expansion of $$H(x)$$ by using the Euler Maclaurin formula, and then derive the asymptotic expansion of $$H(x-c)$$ from the result, where $$c$$ is an arbitrary constant. By replacing $$x$$ with $$\alpha x$$ and $$c$$ with $$-\beta$$, this is enough to asymptotically expand $$H(\alpha x+\beta)$$, which is our goal.

Before we apply the Euler Maclaurin formula to the generalised harmonic series, there are a few things we can do to clean it up a bit. We're interested in a sum from $$n=1$$ up to $$N$$, so let's fix $$a=1$$ and $$b=N$$. For each fixed $$m$$, the error term $$R_m$$ converges to a constant depending on $$m$$ as we take $$N$$ to infinity, as long as $$f^{(m)}$$ is "well-behaved". Let's rewrite the error term $$R_m$$ as $$C_m+R'_m$$ where $$C_m$$ is the limiting constant and $$R'_m\to 0$$ as $$N\to\infty$$.

Now let's use the formula. Let $$x$$ be a real number and $$m$$ be a fixed positive integer. The obvious choice for $$f$$ is to take $$f(t)=1/t-1/(t+x)$$, but it turns out that this will give us an asymptotic series in terms of powers of $$x+1$$, rather than in powers of $$x$$. Instead, we define $$f(t)=1/t-1/(t+x-1)$$, so that $$\sum_{n=1}^{\infty}f(n)=H(x-1)$$. We can use the fact that $$H(x-1)+1/x=H(x)$$ and add back the extra $$1/x$$ term later. For clarity, denote the error terms by $$C_{m,x}$$ and $$R'_{m,x}$$ to emphasise the fact that they depend on the constant $$x$$.

Using the fact that

$$f^{(r)}(t)=(-1)^{r}r!\left(\frac{1}{t^{r+1}}-\frac{1}{(t+x-1)^{r+1}}\right),$$

the Euler Maclaurin formula now says that

$$\begin{aligned}
\sum_{n=1}^{N}\frac{1}{n}-\frac{1}{n+x-1}
&=\int_{1}^{N}\frac{1}{t}-\frac{1}{t+x-1}dt
+\frac{1-\frac{1}{x}+\frac{1}{N}-\frac{1}{N+x-1}}{2} \\
&+\sum_{n=2}^{m}\frac{B_n}{n!}(-1)^{n-1}(n-1)!\left(\frac{1}{N^n}-\frac{1}{(N+x-1)^n}-1+\frac{1}{x^n}\right) \\
&+C_{m,x}+R'_{m,x} \\
&=\color{red}{\log\left(\frac{N}{N+x-1}\right)}+\log(x)
+\frac{1-\frac{1}{x}+\color{red}{\frac{1}{N}-\frac{1}{N+x-1}}}{2} \\
&-\sum_{n=2}^{m}\frac{B_n}{n}(-1)^n\left(\color{red}{\frac{1}{N^n}-\frac{1}{(N+x-1)^n}}-1+\frac{1}{x^n}\right) \\
&+C_{m,x}+\color{red}{R'_{m,x}} \\
\end{aligned}$$

Taking $$N\to\infty$$ eliminates all of the terms in red, simplifying the formula significantly. Also, it turns out that the *odd* Bernoulli numbers $$B_3, B_5, \dots$$ are all zero, so the $$(-1)^n$$ term inside the sum has no effect and can be removed. Let's also add back the $$1/x$$ term from earlier. The resulting formula looks like this:

$$H(x)=\log(x)+\frac{1}{2}+\frac{1}{2x}+\sum_{n=2}^{m}\frac{B_n}{n}\left(1-\frac{1}{x^n}\right)+C_{m,x}$$

To obtain the final asymptotic formula for $$H(x)$$, subtract $$\log(x)$$ and consider what happens as $$x\to\infty$$. The $$1/x^n$$ term inside the sum will go to zero. It turns out that $$H(x)-\log(x)$$ converges to a constant, denoted by $$\gamma$$, and that $$C_{m,x}$$ also converges to a constant $$C_m$$ depending on $$m$$. So we have

$$\lim_{x\to\infty}H(x)-\log(x)=\gamma=\frac{1}{2}+\sum_{n=2}^{m}\frac{B_n}{n}+C_m$$

Exercise for the reader: show that $$\lim_{x\to\infty}H(x)-\log(x)$$ exists.

This shows that the right hand side is actually independent of $$m$$ (because it is always equal to $$\gamma$$), which completes the derivation of the asymptotic formula:

$$\begin{aligned}
H(x)&\sim\log(x)+\gamma+\frac{1}{2x}-\sum_{n=2}^{\infty}\frac{B_n}{nx^n} \\
&=\log(x)+\gamma-\sum_{n=1}^{\infty}\frac{B_n}{nx^n}
\end{aligned}$$

It is very important to emphasize that this is only an *asymptotic series*. The infinite sum above does *not* converge! If we truncate the series after $$m$$ terms, then the formula gets closer to $$H(x)$$ as we take $$x$$ to infinity, but diverges as we take $$m$$ to infinity.

We can now calculate the asymptotic formula for $$H(x-c)$$. This formula looks much the same as the formula above, but uses the Bernoulli *polynomials* rather than the Bernoulli numbers. The Bernoulli numbers are simply the values of the Bernoulli polynomials at zero.

$$\begin{aligned}
H(x-c)&\sim\color{red}{\log(x-c)}+\gamma-\sum_{n=1}^{\infty}\frac{B_n}{n\color{green}{(x-c)^{n}}} \\
&= \color{red}{\log(x)-\sum_{n=1}^{\infty}\frac{c^n}{nx^n}}+\gamma-\sum_{n=1}^{\infty}\frac{B_n}{n}\color{green}{\sum_{k=0}^{\infty}\binom{n+k-1}{k}c^k x^{-n-k}} \\
&= \log(x)-\sum_{n=1}^{\infty}\frac{c^n}{nx^n}+\gamma-\sum_{n=1}^{\infty}\sum_{k=0}^{\infty}\frac{B_n}{n+k}\binom{n+k}{k}c^k x^{-n-k}
\end{aligned}$$

Next, we sum over diagonals by making the substitution $$n+k=d$$.

$$\begin{aligned}
H(x-c)&\sim\log(x)-\color{red}{\sum_{n=1}^{\infty}}\frac{c^n}{\color{red}{nx^n}}+\gamma-\color{red}{\sum_{d=1}^{\infty}}\sum_{i=0}^{d-1}B_{d-i}\binom{d}{i}c^i \color{red}{\frac{1}{dx^d}} \\
&= \log(x)+\gamma-\color{red}{\sum_{d=1}^{\infty}}\underbrace{\left[c^d+\sum_{i=0}^{d-1}B_{d-i}\binom{d}{i}c^i\right]}_{\text{Bernoulli polynomial }B_d(c)}\color{red}{\frac{1}{dx^d}} \\
&= \log(x)+\gamma-\sum_{n=1}^{\infty}\frac{B_n(c)}{nx^n} \\
\end{aligned}$$

So finally, we have

$$\boxed{H(\alpha x+\beta)\sim\log(x)+\log(\alpha)+\gamma-\sum_{n=1}^{\infty}\frac{B_n(-\beta)}{n\alpha^n x^n}}$$

## **Leibniz formula error series**

All that remains now is calculation. We have

$$\begin{aligned}
\pi_N&\sim\pi+\left(\log(N/2)+\gamma-\sum_{k=1}^{\infty}\frac{B_k(1/4)}{k2^{-k}N^k}\right)-\left(\log(N/2)+\gamma-\sum_{k=1}^{\infty}\frac{B_k(3/4)}{k2^{-k}N^k}\right) \\
&=\pi-\sum_{k=1}^{\infty}\frac{B_k(1/4)-B_k(3/4)}{k2^{-k}N^k} \\
&=\pi+\frac{1}{N}-\frac{1}{4N^3}+\frac{5}{16N^5}-\frac{61}{64N^7}+\frac{1385}{256N^9}-\frac{50521}{1024N^{11}}+\frac{2702765}{4096N^{13}}-\cdots
\end{aligned}$$

or replacing $$N$$ with $$N/2$$ as before,

$$\begin{aligned}
\pi_{N/2}\sim\pi+\frac{2\cdot 1}{N}-\frac{2\cdot 1}{N^3}+\frac{2\cdot 5}{N^5}-\frac{2\cdot 61}{N^7}+\frac{2\cdot 1385}{N^9}-\frac{2\cdot 50521}{N^{11}}+\frac{2\cdot 2702765}{N^{13}}-\cdots
\end{aligned}$$


[1]: https://en.wikipedia.org/wiki/Chudnovsky_algorithm
