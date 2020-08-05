A common motion encountered in robotics is the rotation of a rigid body
about a fixed axis. In particular, consider a robot link rotating about
an axis  <img src="https://www.zhihu.com/equation?tex=u" alt="u" class="ee_img tr_noresize" eeimg="1">  (represented by a unit vector in  <img src="https://www.zhihu.com/equation?tex=R^3" alt="R^3" class="ee_img tr_noresize" eeimg="1"> ) at a rate of
 <img src="https://www.zhihu.com/equation?tex=\theta" alt="\theta" class="ee_img tr_noresize" eeimg="1">  radians per second (rad/s, in  <img src="https://www.zhihu.com/equation?tex=R" alt="R" class="ee_img tr_noresize" eeimg="1"> ) for  <img src="https://www.zhihu.com/equation?tex=t" alt="t" class="ee_img tr_noresize" eeimg="1">  seconds. Consider a
point  <img src="https://www.zhihu.com/equation?tex=p" alt="p" class="ee_img tr_noresize" eeimg="1">  attached to the robot link and  <img src="https://www.zhihu.com/equation?tex=\dot{p}" alt="\dot{p}" class="ee_img tr_noresize" eeimg="1">  the tangent velocity
at point  <img src="https://www.zhihu.com/equation?tex=p" alt="p" class="ee_img tr_noresize" eeimg="1"> .

We define a (arbitrary) Cartesian coordinate system  <img src="https://www.zhihu.com/equation?tex=A" alt="A" class="ee_img tr_noresize" eeimg="1"> , and represent
 <img src="https://www.zhihu.com/equation?tex=u" alt="u" class="ee_img tr_noresize" eeimg="1"> ,  <img src="https://www.zhihu.com/equation?tex=p" alt="p" class="ee_img tr_noresize" eeimg="1">  and  <img src="https://www.zhihu.com/equation?tex=\dot{p}" alt="\dot{p}" class="ee_img tr_noresize" eeimg="1">  in frame  <img src="https://www.zhihu.com/equation?tex=A" alt="A" class="ee_img tr_noresize" eeimg="1"> , using the 3D coordinate vectors
 <img src="https://www.zhihu.com/equation?tex=^Au" alt="^Au" class="ee_img tr_noresize" eeimg="1"> ,  <img src="https://www.zhihu.com/equation?tex=^Ap" alt="^Ap" class="ee_img tr_noresize" eeimg="1"> , and  <img src="https://www.zhihu.com/equation?tex=^A\dot{p}" alt="^A\dot{p}" class="ee_img tr_noresize" eeimg="1"> , respectively. From the fact that
 <img src="https://www.zhihu.com/equation?tex=v=2\pi r/t = \omega r" alt="v=2\pi r/t = \omega r" class="ee_img tr_noresize" eeimg="1">  in 1D we can verify the following relation


<img src="https://www.zhihu.com/equation?tex=^A\dot{p}(t) = \theta ^Au\times ^Ap(t)," alt="^A\dot{p}(t) = \theta ^Au\times ^Ap(t)," class="ee_img tr_noresize" eeimg="1">

where  <img src="https://www.zhihu.com/equation?tex=\times" alt="\times" class="ee_img tr_noresize" eeimg="1">  denotes *cross product*. The above equation is a
time-invariant linear differential equation which may be integrated to
give


<img src="https://www.zhihu.com/equation?tex=^Ap(t) = \exp\left(t\theta ^Au\times\right) {^Ap}(0)," alt="^Ap(t) = \exp\left(t\theta ^Au\times\right) {^Ap}(0)," class="ee_img tr_noresize" eeimg="1">

where  <img src="https://www.zhihu.com/equation?tex=e^{t\theta ^Au\times}" alt="e^{t\theta ^Au\times}" class="ee_img tr_noresize" eeimg="1">  is the exponential map of
 <img src="https://www.zhihu.com/equation?tex=t\theta ^Au\times" alt="t\theta ^Au\times" class="ee_img tr_noresize" eeimg="1"> . The above equation means that if the robot link
rotates about the axis  <img src="https://www.zhihu.com/equation?tex=^Au" alt="^Au" class="ee_img tr_noresize" eeimg="1">  at rate  <img src="https://www.zhihu.com/equation?tex=\theta" alt="\theta" class="ee_img tr_noresize" eeimg="1">  (rad/s) for  <img src="https://www.zhihu.com/equation?tex=t" alt="t" class="ee_img tr_noresize" eeimg="1">  seconds,
the rotation is given by


<img src="https://www.zhihu.com/equation?tex=R(^Au, \theta, t) = e^{t\theta ^Au\times} \label{eq:exp-map}" alt="R(^Au, \theta, t) = e^{t\theta ^Au\times} \label{eq:exp-map}" class="ee_img tr_noresize" eeimg="1">

#### Definition (3D angular velocity)

. The 3D angular velocity is represented by a coordinate vector
expressed in frame  <img src="https://www.zhihu.com/equation?tex=A" alt="A" class="ee_img tr_noresize" eeimg="1"> , as the product of the angle
 <img src="https://www.zhihu.com/equation?tex=\theta\in\mathbb{R}" alt="\theta\in\mathbb{R}" class="ee_img tr_noresize" eeimg="1">  and the rotation axis  <img src="https://www.zhihu.com/equation?tex=^Au\in\mathbb{R}^3" alt="^Au\in\mathbb{R}^3" class="ee_img tr_noresize" eeimg="1"> :


<img src="https://www.zhihu.com/equation?tex=^A\omega = \theta ^Au." alt="^A\omega = \theta ^Au." class="ee_img tr_noresize" eeimg="1">

In constrast, we have  <img src="https://www.zhihu.com/equation?tex=^Au=^A\omega/\|^A\omega\|" alt="^Au=^A\omega/\|^A\omega\|" class="ee_img tr_noresize" eeimg="1">  and
 <img src="https://www.zhihu.com/equation?tex=\theta = \|^A\omega\|" alt="\theta = \|^A\omega\|" class="ee_img tr_noresize" eeimg="1"> .

With the definition of angular velocity we can rewrite the exponential
map by its power series:


<img src="https://www.zhihu.com/equation?tex=R(^A\omega, t) = I + t^A\omega\times + \frac{\left(t^A\omega\times\right)^2}{2} + \frac{\left(t^A\omega\times\right)^3}{3} + ... = \sum_{n=0}^{\infty}{\frac{1}{n!}\left(t^A\omega\times\right)^n} \label{eq:exp-map-power-series}" alt="R(^A\omega, t) = I + t^A\omega\times + \frac{\left(t^A\omega\times\right)^2}{2} + \frac{\left(t^A\omega\times\right)^3}{3} + ... = \sum_{n=0}^{\infty}{\frac{1}{n!}\left(t^A\omega\times\right)^n} \label{eq:exp-map-power-series}" class="ee_img tr_noresize" eeimg="1">

In the following parts, we show that accepts a closed form solution
which is known as the *Rodrigues’ formula*.

From the definition of cross product it is easy to see that the matrix
 <img src="https://www.zhihu.com/equation?tex=^A\omega\times" alt="^A\omega\times" class="ee_img tr_noresize" eeimg="1">  is a skew-symmetric matrix, i.e.
 <img src="https://www.zhihu.com/equation?tex=^A\omega\times \in so(3)" alt="^A\omega\times \in so(3)" class="ee_img tr_noresize" eeimg="1"> , where  <img src="https://www.zhihu.com/equation?tex=so(3)" alt="so(3)" class="ee_img tr_noresize" eeimg="1">  is the vector space of
 <img src="https://www.zhihu.com/equation?tex=3\times 3" alt="3\times 3" class="ee_img tr_noresize" eeimg="1">  skew-symmetric matrices defined by


<img src="https://www.zhihu.com/equation?tex=so(3) = \left\{ S\in \mathbb{R}^{3\times 3} \mid S^T = -S \right\}" alt="so(3) = \left\{ S\in \mathbb{R}^{3\times 3} \mid S^T = -S \right\}" class="ee_img tr_noresize" eeimg="1">

or equivalently


<img src="https://www.zhihu.com/equation?tex=so(3) = \left\{ \begin{pmatrix}
0 & -\omega_3 & \omega_2\\
\omega_3 & 0 & -\omega_1\\
-\omega_2 & \omega_1 & 0
\end{pmatrix} \mid \left(\omega_1,\omega_2,\omega_3\right) \in R^3 \right\}." alt="so(3) = \left\{ \begin{pmatrix}
0 & -\omega_3 & \omega_2\\
\omega_3 & 0 & -\omega_1\\
-\omega_2 & \omega_1 & 0
\end{pmatrix} \mid \left(\omega_1,\omega_2,\omega_3\right) \in R^3 \right\}." class="ee_img tr_noresize" eeimg="1">

#### Lemma.

Given  <img src="https://www.zhihu.com/equation?tex=\omega\in so(3)" alt="\omega\in so(3)" class="ee_img tr_noresize" eeimg="1"> , the following relations hold:


<img src="https://www.zhihu.com/equation?tex=\begin{aligned}
  \left(\omega\times\right)^2 &= \omega\omega^T - \|\omega\|^2I, \\
  \left(\omega\times\right)^3 &= -\|\omega\|^2 \omega\times,\end{aligned}" alt="\begin{aligned}
  \left(\omega\times\right)^2 &= \omega\omega^T - \|\omega\|^2I, \\
  \left(\omega\times\right)^3 &= -\|\omega\|^2 \omega\times,\end{aligned}" class="ee_img tr_noresize" eeimg="1">

and higher powers of  <img src="https://www.zhihu.com/equation?tex=\omega\times" alt="\omega\times" class="ee_img tr_noresize" eeimg="1">  can be calculated recursively.

Applying this lemma with  <img src="https://www.zhihu.com/equation?tex=a=t^A\omega" alt="a=t^A\omega" class="ee_img tr_noresize" eeimg="1"> , equation becomes


<img src="https://www.zhihu.com/equation?tex=\begin{aligned}
R(^A\omega, t) = I + \frac{^A\omega\times}{\|^A\omega\|}\sin\left(\|^A\omega\|t\right) + \frac{\left(^A\omega\times\right)^2}{\|^A\omega\|^2}\left(1-\cos\left(\|^A\omega\|t\right)\right), \label{eq:rodrigues-fomula}\end{aligned}" alt="\begin{aligned}
R(^A\omega, t) = I + \frac{^A\omega\times}{\|^A\omega\|}\sin\left(\|^A\omega\|t\right) + \frac{\left(^A\omega\times\right)^2}{\|^A\omega\|^2}\left(1-\cos\left(\|^A\omega\|t\right)\right), \label{eq:rodrigues-fomula}\end{aligned}" class="ee_img tr_noresize" eeimg="1">

This formula, commonly referred to as *Rodrigues’ formula*, gives an
efficient method for computing exponential map of
 <img src="https://www.zhihu.com/equation?tex=e^{t ^A\omega \times}" alt="e^{t ^A\omega \times}" class="ee_img tr_noresize" eeimg="1"> .

Finally, we show that exponential map transforms skew-symmetric matrices
into rotation matrices. In other words, exponentials of  <img src="https://www.zhihu.com/equation?tex=so(3)" alt="so(3)" class="ee_img tr_noresize" eeimg="1">  elements
are elements in the *special orthogonal group* defined by


<img src="https://www.zhihu.com/equation?tex=SO(3) = \left\{ R \in \mathbb{R}^{3\times 3} \mid RR^T = R^TR = I,\  det(R)=+1 \right\}," alt="SO(3) = \left\{ R \in \mathbb{R}^{3\times 3} \mid RR^T = R^TR = I,\  det(R)=+1 \right\}," class="ee_img tr_noresize" eeimg="1">

or equivalently


<img src="https://www.zhihu.com/equation?tex=SO(3) = \left\{ r: \mathbb{E}^3 \rightarrow \mathbb{E}^3 \mid \forall x,y\in\mathbb{E}^3,\  \|r(x)-r(y)\|=\|x-y\|,\  g(0)=0\right\}," alt="SO(3) = \left\{ r: \mathbb{E}^3 \rightarrow \mathbb{E}^3 \mid \forall x,y\in\mathbb{E}^3,\  \|r(x)-r(y)\|=\|x-y\|,\  g(0)=0\right\}," class="ee_img tr_noresize" eeimg="1">

#### Proposition.

Given a skew-symmetric matrix  <img src="https://www.zhihu.com/equation?tex=\omega\times \in so(3)" alt="\omega\times \in so(3)" class="ee_img tr_noresize" eeimg="1"> , we have


<img src="https://www.zhihu.com/equation?tex=\begin{aligned}
  e^{\omega\times}\in SO(3).\end{aligned}" alt="\begin{aligned}
  e^{\omega\times}\in SO(3).\end{aligned}" class="ee_img tr_noresize" eeimg="1">

*Proof.* The following chain of equalities can be checked using
Rodrigues’ formula:


<img src="https://www.zhihu.com/equation?tex=\begin{aligned}
  \left(e^{\omega\times}\right)^{-1} = e^{-\omega\times} = e^{{\omega\times}^T} = \left(e^{\omega\times}\right)^T,\end{aligned}" alt="\begin{aligned}
  \left(e^{\omega\times}\right)^{-1} = e^{-\omega\times} = e^{{\omega\times}^T} = \left(e^{\omega\times}\right)^T,\end{aligned}" class="ee_img tr_noresize" eeimg="1">

Thus  <img src="https://www.zhihu.com/equation?tex=\left(e^{\omega\times}\right)^Te^{\omega\times}=I" alt="\left(e^{\omega\times}\right)^Te^{\omega\times}=I" class="ee_img tr_noresize" eeimg="1"> , from which it
follows that  <img src="https://www.zhihu.com/equation?tex=\det\left(e^{\omega\times}\right)= \pm1" alt="\det\left(e^{\omega\times}\right)= \pm1" class="ee_img tr_noresize" eeimg="1">  for all
 <img src="https://www.zhihu.com/equation?tex=\omega\times\in so(3)" alt="\omega\times\in so(3)" class="ee_img tr_noresize" eeimg="1"> . Using the continuity of the determinant as a
function of the entries of a matrix, combined with continuity of the
exponential map and the fact that  <img src="https://www.zhihu.com/equation?tex=\det\exp(0) = 1" alt="\det\exp(0) = 1" class="ee_img tr_noresize" eeimg="1"> , we conclude that
 <img src="https://www.zhihu.com/equation?tex=\det\left(e^{\omega\times}\right)= +1" alt="\det\left(e^{\omega\times}\right)= +1" class="ee_img tr_noresize" eeimg="1"> .

#### Further discussion.

In fact, the exponential map of  <img src="https://www.zhihu.com/equation?tex=so(3)" alt="so(3)" class="ee_img tr_noresize" eeimg="1">  is surjective onto  <img src="https://www.zhihu.com/equation?tex=SO(3)" alt="SO(3)" class="ee_img tr_noresize" eeimg="1"> ,
which means  <img src="https://www.zhihu.com/equation?tex=\forall R\in SO(3)" alt="\forall R\in SO(3)" class="ee_img tr_noresize" eeimg="1"> , there exists  <img src="https://www.zhihu.com/equation?tex=\omega\in\mathbb{R}^3" alt="\omega\in\mathbb{R}^3" class="ee_img tr_noresize" eeimg="1"> 
such that  <img src="https://www.zhihu.com/equation?tex=R=e^{\omega\times}" alt="R=e^{\omega\times}" class="ee_img tr_noresize" eeimg="1"> . Proof can be found in the book of
[Murray’1994], page 29.

In summary, the 3D vector  <img src="https://www.zhihu.com/equation?tex=\omega=u\theta" alt="\omega=u\theta" class="ee_img tr_noresize" eeimg="1">  with  <img src="https://www.zhihu.com/equation?tex=\|u\|=1" alt="\|u\|=1" class="ee_img tr_noresize" eeimg="1">  can be
understood in two different aspects:

-   On the one hands,  <img src="https://www.zhihu.com/equation?tex=\omega" alt="\omega" class="ee_img tr_noresize" eeimg="1">  represents the anglar velocity of a rigid
    body rotating around the axis  <img src="https://www.zhihu.com/equation?tex=u" alt="u" class="ee_img tr_noresize" eeimg="1">  at rate  <img src="https://www.zhihu.com/equation?tex=\theta" alt="\theta" class="ee_img tr_noresize" eeimg="1"> . For a rotation
    at *constant* rate  <img src="https://www.zhihu.com/equation?tex=\theta" alt="\theta" class="ee_img tr_noresize" eeimg="1"> , the rotation matrix at time  <img src="https://www.zhihu.com/equation?tex=t" alt="t" class="ee_img tr_noresize" eeimg="1">  w.r.t.
    the initial position at time  <img src="https://www.zhihu.com/equation?tex=0" alt="0" class="ee_img tr_noresize" eeimg="1"> , i.e.  <img src="https://www.zhihu.com/equation?tex=R(u\theta, t)" alt="R(u\theta, t)" class="ee_img tr_noresize" eeimg="1"> , is given by
    the Rodrigues’ formula .

-   On the other hand,  <img src="https://www.zhihu.com/equation?tex=\omega" alt="\omega" class="ee_img tr_noresize" eeimg="1">  represents the net rotation
     <img src="https://www.zhihu.com/equation?tex=R(u,\theta)" alt="R(u,\theta)" class="ee_img tr_noresize" eeimg="1">  about a fixed axis  <img src="https://www.zhihu.com/equation?tex=u=\frac{\omega}{\|\omega\|}" alt="u=\frac{\omega}{\|\omega\|}" class="ee_img tr_noresize" eeimg="1"> 
    through an angle  <img src="https://www.zhihu.com/equation?tex=\theta=\|\omega\|" alt="\theta=\|\omega\|" class="ee_img tr_noresize" eeimg="1"> .


