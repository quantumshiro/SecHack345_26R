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