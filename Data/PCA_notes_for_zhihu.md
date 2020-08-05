Introduction
============

[b]<span>0.45</span> ![A set of 3D data (shown as green
points)](set_of_3d_points.jpg "fig:")

[b]<span>0.45</span> ![The same points “unfolded” in a 2D
space.](set_of_2d_points.jpg "fig:")

[fig:pca~h~euristics]

All data points lie in a sub-manifold of the 3 dimentional space. If
somehow we find this sub-manifold which can be “unfolded” to a lower
dimensional space (2D space in this case), then we can reduce the
dimensiontality of the data without losing much information.

Principle
=========

Let  <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1">  be a  <img src="https://www.zhihu.com/equation?tex=d" alt="d" class="ee_img tr_noresize" eeimg="1"> -dimensional random vector and  <img src="https://www.zhihu.com/equation?tex=x_1" alt="x_1" class="ee_img tr_noresize" eeimg="1"> ,..., <img src="https://www.zhihu.com/equation?tex=x_N" alt="x_N" class="ee_img tr_noresize" eeimg="1">  be an
i.i.d. sample of  <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> . We denote by  <img src="https://www.zhihu.com/equation?tex=X" alt="X" class="ee_img tr_noresize" eeimg="1">  the  <img src="https://www.zhihu.com/equation?tex=N\times d" alt="N\times d" class="ee_img tr_noresize" eeimg="1">  matrix (a.k.a.
the *design matrix* of the sample) defined by:


<img src="https://www.zhihu.com/equation?tex=X = \left( \begin{array}{ccc}
   \ldots & x_1^T & \ldots \\
    & \vdots & \\
   \ldots & x_N^T & \ldots\\
  \end{array} \right)." alt="X = \left( \begin{array}{ccc}
   \ldots & x_1^T & \ldots \\
    & \vdots & \\
   \ldots & x_N^T & \ldots\\
  \end{array} \right)." class="ee_img tr_noresize" eeimg="1">

In order to perserve the information as much as possible, our idea is to
find directions along which the variance of the projected data is
maximal. Let  <img src="https://www.zhihu.com/equation?tex=u\in R^d" alt="u\in R^d" class="ee_img tr_noresize" eeimg="1"> , the affine transformation of the ran. vec.  <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 
along  <img src="https://www.zhihu.com/equation?tex=u" alt="u" class="ee_img tr_noresize" eeimg="1"> , i.e.  <img src="https://www.zhihu.com/equation?tex=u^Tx" alt="u^Tx" class="ee_img tr_noresize" eeimg="1"> , is a ran. var. with variance:


<img src="https://www.zhihu.com/equation?tex=\begin{aligned}
  &\text{Var}(u^Tx) \\
  =& E\left((u^Tx)^2\right) - E\left(u^Tx\right)^2 \\
  =& E\left(u^Txx^Tu\right) - E\left(u^Tx\right)E\left(x^Tu\right) \\
  =& u^TE\left(xx^T\right)u - u^TE\left(x\right)E\left(x\right)^Tu \\
  =& u^T\Sigma u,\end{aligned}" alt="\begin{aligned}
  &\text{Var}(u^Tx) \\
  =& E\left((u^Tx)^2\right) - E\left(u^Tx\right)^2 \\
  =& E\left(u^Txx^Tu\right) - E\left(u^Tx\right)E\left(x^Tu\right) \\
  =& u^TE\left(xx^T\right)u - u^TE\left(x\right)E\left(x\right)^Tu \\
  =& u^T\Sigma u,\end{aligned}" class="ee_img tr_noresize" eeimg="1">

where  <img src="https://www.zhihu.com/equation?tex=\Sigma=E\left(xx^T\right)-E\left(x\right)E\left(x\right)^T" alt="\Sigma=E\left(xx^T\right)-E\left(x\right)E\left(x\right)^T" class="ee_img tr_noresize" eeimg="1">  is
the covariance matrix of  <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1">  by definition.

We would like to solve the problem


<img src="https://www.zhihu.com/equation?tex=\label{eq:pb1}
\begin{aligned}
& \underset{u\in R^d}{\text{maximize}}
& & u^T\Sigma u \\
& \text{subject to}
& & \|u\| \leq 1.
\end{aligned}" alt="\label{eq:pb1}
\begin{aligned}
& \underset{u\in R^d}{\text{maximize}}
& & u^T\Sigma u \\
& \text{subject to}
& & \|u\| \leq 1.
\end{aligned}" class="ee_img tr_noresize" eeimg="1">

Note that the constraint  <img src="https://www.zhihu.com/equation?tex=\|u\| \leq 1" alt="\|u\| \leq 1" class="ee_img tr_noresize" eeimg="1">  is necessary because otherwise
the problem is ill-posed: the objective function is unlimited due to
unlimited scale of  <img src="https://www.zhihu.com/equation?tex=u" alt="u" class="ee_img tr_noresize" eeimg="1"> , which is meaningless in the sense of finding the
optimal direction of  <img src="https://www.zhihu.com/equation?tex=u" alt="u" class="ee_img tr_noresize" eeimg="1">  which optimizes  <img src="https://www.zhihu.com/equation?tex=\text{Var}(u^Tx)" alt="\text{Var}(u^Tx)" class="ee_img tr_noresize" eeimg="1"> .

Note also that in practice, we only have an i.i.d. sample instead of the
real distribution of  <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> , namely, the covariance matrix  <img src="https://www.zhihu.com/equation?tex=\Sigma" alt="\Sigma" class="ee_img tr_noresize" eeimg="1">  in
Problem is unknown. Therefore, instead of solving , we introduce the
empirical mean and the empirical covariance of the sample
 <img src="https://www.zhihu.com/equation?tex=x_1" alt="x_1" class="ee_img tr_noresize" eeimg="1"> ,..., <img src="https://www.zhihu.com/equation?tex=x_N" alt="x_N" class="ee_img tr_noresize" eeimg="1"> :


<img src="https://www.zhihu.com/equation?tex=\begin{aligned}
  \bar{x} &= \frac{1}{N}\sum_{i=1}^Nx_i, \\
  S &= \frac{1}{N}\sum_{i=1}^Nx_ix_i^T - \bar{x}\bar{x}^T,\end{aligned}" alt="\begin{aligned}
  \bar{x} &= \frac{1}{N}\sum_{i=1}^Nx_i, \\
  S &= \frac{1}{N}\sum_{i=1}^Nx_ix_i^T - \bar{x}\bar{x}^T,\end{aligned}" class="ee_img tr_noresize" eeimg="1">

and solve the problem


<img src="https://www.zhihu.com/equation?tex=\label{eq:pb2}
\begin{aligned}
& \underset{u\in R^d}{\text{maximize}}
& & u^TS u \\
& \text{subject to}
& & \|u\| \leq 1.
\end{aligned}" alt="\label{eq:pb2}
\begin{aligned}
& \underset{u\in R^d}{\text{maximize}}
& & u^TS u \\
& \text{subject to}
& & \|u\| \leq 1.
\end{aligned}" class="ee_img tr_noresize" eeimg="1">

Firstly, we show that objective function of is actually equal to the
empirical variance of  <img src="https://www.zhihu.com/equation?tex=u^Tx_i" alt="u^Tx_i" class="ee_img tr_noresize" eeimg="1"> , ...,  <img src="https://www.zhihu.com/equation?tex=u^Tx_N" alt="u^Tx_N" class="ee_img tr_noresize" eeimg="1"> .


<img src="https://www.zhihu.com/equation?tex=\begin{aligned}
  &u^TSu \\
  =& u^T\left(\frac{1}{N}\sum_{i=1}^Nx_ix_i^T\right)u - u^T\left(\frac{1}{N}\sum_{i=1}^Nx_i\frac{1}{N}\sum_{i=j}^Nx_j^T\right)u \\
  =& \frac{1}{N}\sum_{i=1}^Nu^Tx_ix_i^Tu - \frac{1}{N}\sum_{i=1}^Nu^Tx_i\frac{1}{N}\sum_{i=j}^Nx_j^Tu \\
  =& \frac{1}{N}\sum_{i=1}^N(u^Tx_i)^2 - \left(\frac{1}{N}\sum_{i=1}^Nu^Tx_i\right)^2\end{aligned}" alt="\begin{aligned}
  &u^TSu \\
  =& u^T\left(\frac{1}{N}\sum_{i=1}^Nx_ix_i^T\right)u - u^T\left(\frac{1}{N}\sum_{i=1}^Nx_i\frac{1}{N}\sum_{i=j}^Nx_j^T\right)u \\
  =& \frac{1}{N}\sum_{i=1}^Nu^Tx_ix_i^Tu - \frac{1}{N}\sum_{i=1}^Nu^Tx_i\frac{1}{N}\sum_{i=j}^Nx_j^Tu \\
  =& \frac{1}{N}\sum_{i=1}^N(u^Tx_i)^2 - \left(\frac{1}{N}\sum_{i=1}^Nu^Tx_i\right)^2\end{aligned}" class="ee_img tr_noresize" eeimg="1">

which is by definition the empirical variance of  <img src="https://www.zhihu.com/equation?tex=u^Tx_i" alt="u^Tx_i" class="ee_img tr_noresize" eeimg="1"> , ...,
 <img src="https://www.zhihu.com/equation?tex=u^Tx_N" alt="u^Tx_N" class="ee_img tr_noresize" eeimg="1"> . See @rigollet2017mitcourse for more information about the
empirical covariance matrix  <img src="https://www.zhihu.com/equation?tex=S" alt="S" class="ee_img tr_noresize" eeimg="1"> .

Then we show how to solve Problem . The Lagrangian of the problem is


<img src="https://www.zhihu.com/equation?tex=\begin{aligned}
  L(u,\lambda) = u^TSu - \lambda(u^Tu-1).\end{aligned}" alt="\begin{aligned}
  L(u,\lambda) = u^TSu - \lambda(u^Tu-1).\end{aligned}" class="ee_img tr_noresize" eeimg="1">

The partial derivitavie w.r.t.  <img src="https://www.zhihu.com/equation?tex=u" alt="u" class="ee_img tr_noresize" eeimg="1">  is


<img src="https://www.zhihu.com/equation?tex=\begin{aligned}
  \frac{\partial L}{\partial u} = 2(Su-\lambda u)\end{aligned}" alt="\begin{aligned}
  \frac{\partial L}{\partial u} = 2(Su-\lambda u)\end{aligned}" class="ee_img tr_noresize" eeimg="1">

From  <img src="https://www.zhihu.com/equation?tex=\frac{\partial L}{\partial u}=0" alt="\frac{\partial L}{\partial u}=0" class="ee_img tr_noresize" eeimg="1">  we obtain


<img src="https://www.zhihu.com/equation?tex=\begin{aligned}
  Su=\lambda u\end{aligned}" alt="\begin{aligned}
  Su=\lambda u\end{aligned}" class="ee_img tr_noresize" eeimg="1">

which means the optimal  <img src="https://www.zhihu.com/equation?tex=\lambda" alt="\lambda" class="ee_img tr_noresize" eeimg="1">  and  <img src="https://www.zhihu.com/equation?tex=u" alt="u" class="ee_img tr_noresize" eeimg="1">  must be an eigenvalue and the
corresponding eigenvector of  <img src="https://www.zhihu.com/equation?tex=S" alt="S" class="ee_img tr_noresize" eeimg="1"> . Since  <img src="https://www.zhihu.com/equation?tex=u^TSu" alt="u^TSu" class="ee_img tr_noresize" eeimg="1">  is equal to empirical
variance, it means that  <img src="https://www.zhihu.com/equation?tex=u^TSu\geq0" alt="u^TSu\geq0" class="ee_img tr_noresize" eeimg="1">  for any  <img src="https://www.zhihu.com/equation?tex=u\in R^d" alt="u\in R^d" class="ee_img tr_noresize" eeimg="1"> . Therefore, the
symmetric matrix  <img src="https://www.zhihu.com/equation?tex=S" alt="S" class="ee_img tr_noresize" eeimg="1">  is positive semi-definite, and hence is
diagonalizable. Therefore, Problem is a convex optimization problem
(with concave objective function). The optimal solution  <img src="https://www.zhihu.com/equation?tex=u^*" alt="u^*" class="ee_img tr_noresize" eeimg="1">  is the
eigenvector of the first (i.e. largest) eigenvalue of  <img src="https://www.zhihu.com/equation?tex=S" alt="S" class="ee_img tr_noresize" eeimg="1"> .

PCA algorithm
=============

[H]
