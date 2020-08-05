A common motion encountered in robotics is the rotation of a rigid body
about a fixed axis. In particular, consider a robot link rotating about
an axis $u$ (represented by a unit vector in $R^3$) at a rate of
$\theta$ radians per second (rad/s, in $R$) for $t$ seconds. Consider a
point $p$ attached to the robot link and $\dot{p}$ the tangent velocity
at point $p$.

We define a (arbitrary) Cartesian coordinate system $A$, and represent
$u$, $p$ and $\dot{p}$ in frame $A$, using the 3D coordinate vectors
$^Au$, $^Ap$, and $^A\dot{p}$, respectively. From the fact that
$v=2\pi r/t = \omega r$ in 1D we can verify the following relation

$$^A\dot{p}(t) = \theta ^Au\times ^Ap(t),$$

where $\times$ denotes *cross product*. The above equation is a
time-invariant linear differential equation which may be integrated to
give

$$^Ap(t) = \exp\left(t\theta ^Au\times\right) {^Ap}(0),$$

where $e^{t\theta ^Au\times}$ is the exponential map of
$t\theta ^Au\times$. The above equation means that if the robot link
rotates about the axis $^Au$ at rate $\theta$ (rad/s) for $t$ seconds,
the rotation is given by

$$R(^Au, \theta, t) = e^{t\theta ^Au\times} \label{eq:exp-map}$$

#### Definition (3D angular velocity)

. The 3D angular velocity is represented by a coordinate vector
expressed in frame $A$, as the product of the angle
$\theta\in\mathbb{R}$ and the rotation axis $^Au\in\mathbb{R}^3$:

$$^A\omega = \theta ^Au.$$

In constrast, we have $^Au=^A\omega/\|^A\omega\|$ and
$\theta = \|^A\omega\|$.

With the definition of angular velocity we can rewrite the exponential
map by its power series:

$$R(^A\omega, t) = I + t^A\omega\times + \frac{\left(t^A\omega\times\right)^2}{2} + \frac{\left(t^A\omega\times\right)^3}{3} + ... = \sum_{n=0}^{\infty}{\frac{1}{n!}\left(t^A\omega\times\right)^n} \label{eq:exp-map-power-series}$$

In the following parts, we show that accepts a closed form solution
which is known as the *Rodrigues’ formula*.

From the definition of cross product it is easy to see that the matrix
$^A\omega\times$ is a skew-symmetric matrix, i.e.
$^A\omega\times \in so(3)$, where $so(3)$ is the vector space of
$3\times 3$ skew-symmetric matrices defined by

$$so(3) = \left\{ S\in \mathbb{R}^{3\times 3} \mid S^T = -S \right\}$$

or equivalently

$$so(3) = \left\{ \begin{pmatrix}
0 & -\omega_3 & \omega_2\\
\omega_3 & 0 & -\omega_1\\
-\omega_2 & \omega_1 & 0
\end{pmatrix} \mid \left(\omega_1,\omega_2,\omega_3\right) \in R^3 \right\}.$$

#### Lemma.

Given $\omega\in so(3)$, the following relations hold:

$$\begin{aligned}
  \left(\omega\times\right)^2 &= \omega\omega^T - \|\omega\|^2I, \\
  \left(\omega\times\right)^3 &= -\|\omega\|^2 \omega\times,\end{aligned}$$

and higher powers of $\omega\times$ can be calculated recursively.

Applying this lemma with $a=t^A\omega$, equation becomes

$$\begin{aligned}
R(^A\omega, t) = I + \frac{^A\omega\times}{\|^A\omega\|}\sin\left(\|^A\omega\|t\right) + \frac{\left(^A\omega\times\right)^2}{\|^A\omega\|^2}\left(1-\cos\left(\|^A\omega\|t\right)\right), \label{eq:rodrigues-fomula}\end{aligned}$$

This formula, commonly referred to as *Rodrigues’ formula*, gives an
efficient method for computing exponential map of
$e^{t ^A\omega \times}$.

Finally, we show that exponential map transforms skew-symmetric matrices
into rotation matrices. In other words, exponentials of $so(3)$ elements
are elements in the *special orthogonal group* defined by

$$SO(3) = \left\{ R \in \mathbb{R}^{3\times 3} \mid RR^T = R^TR = I,\  det(R)=+1 \right\},$$

or equivalently

$$SO(3) = \left\{ r: \mathbb{E}^3 \rightarrow \mathbb{E}^3 \mid \forall x,y\in\mathbb{E}^3,\  \|r(x)-r(y)\|=\|x-y\|,\  g(0)=0\right\},$$

#### Proposition.

Given a skew-symmetric matrix $\omega\times \in so(3)$, we have

$$\begin{aligned}
  e^{\omega\times}\in SO(3).\end{aligned}$$

*Proof.* The following chain of equalities can be checked using
Rodrigues’ formula:

$$\begin{aligned}
  \left(e^{\omega\times}\right)^{-1} = e^{-\omega\times} = e^{{\omega\times}^T} = \left(e^{\omega\times}\right)^T,\end{aligned}$$

Thus $\left(e^{\omega\times}\right)^Te^{\omega\times}=I$, from which it
follows that $\det\left(e^{\omega\times}\right)= \pm1$ for all
$\omega\times\in so(3)$. Using the continuity of the determinant as a
function of the entries of a matrix, combined with continuity of the
exponential map and the fact that $\det\exp(0) = 1$, we conclude that
$\det\left(e^{\omega\times}\right)= +1$.

#### Further discussion.

In fact, the exponential map of $so(3)$ is surjective onto $SO(3)$,
which means $\forall R\in SO(3)$, there exists $\omega\in\mathbb{R}^3$
such that $R=e^{\omega\times}$. Proof can be found in the book of
[Murray’1994], page 29.

In summary, the 3D vector $\omega=u\theta$ with $\|u\|=1$ can be
understood in two different aspects:

-   On the one hands, $\omega$ represents the anglar velocity of a rigid
    body rotating around the axis $u$ at rate $\theta$. For a rotation
    at *constant* rate $\theta$, the rotation matrix at time $t$ w.r.t.
    the initial position at time $0$, i.e. $R(u\theta, t)$, is given by
    the Rodrigues’ formula .

-   On the other hand, $\omega$ represents the net rotation
    $R(u,\theta)$ about a fixed axis $u=\frac{\omega}{\|\omega\|}$
    through an angle $\theta=\|\omega\|$.


