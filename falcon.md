---
marp: true
math: mathjax
---
# Falcon

---
## Falconを採用

- NTRU格子の上で構成されるFDH署名
- 環$R$を決める多項式($X^n + 1$)の次数は$n = 512, 1024$, $\pmod{12289}$
---

- 署名生成時に、格子トラップドア$B$を使って離散ガウス分布に従った出力計算を行う

---
## 格子とは
- 多次元空間における基底ベクトルの線形結合によって形成される格子上の構造である。

## 格子トラップドアとは
- SVPやCVPなどの難しい格子問題を効率的に解決するための特別な情報である。
- これは、コンパクトで安全な署名を作成するために使用される短い格子ベクトルの生成を可能にする

---
## Falconの基本形
---
### 鍵生成
1. $q\mathbb{Z}^m \subset \Lambda \subset \mathbb{Z}^m$となる格子$\Lambda$を生成する
2. 公開鍵$A \subset \mathbb{Z}^{n \times m}_q \quad (m > n)$ と $\Lambda \pmod q$に直交する格子$\Lambda^\perp_q$を生成する
3. $\begin{Vmatrix}B\end{Vmatrix}$が十分小さい秘密鍵$B \in \mathbb{Z}^{m \times m}_q$を生成する

- $A$は$\mathbb{Z}_q$の元を成分とする行列であるので$q\mathbb{Z}^m \subset \Lambda$が満たされる
- $\Lambda \pmod q$と$\Lambda^\perp_q$が直交しているので$B \cdot A^T$が成り立つ

---
### 署名生成
- メッセージ$M$に対して$As = H(M) \quad (H: \{0, 1\}^* \rightarrow \mathbb{Z}^n_q)$となるベクトル$s \in \mathbb{Z}^m_q$が署名となる

---
#### 計算方法

1. $Ac_0 = H(M)$となる$c_0 \in \mathbb{Z}^m_q$を計算する
2. $\begin{Vmatrix}B\end{Vmatrix}$が十分小さい$B$を使った離散ガウス分布サンプリングにより$c_0$に近い$v \in \Lambda^\perp_q$を計算する
3. $M$に対する署名を $s := c_0 - v$とする


---
### 署名検証

1. $A$を使って$s$が正しい署名であることを検証するのに、$s$が短いことと、$As = H(M)$が成り立つことを確認できたらOK

$s := c_0 - v$が正しい署名となることは$Av = 0$より、$As = A(c_0 - v) = Ac_0 = H(M)$となりわかる。