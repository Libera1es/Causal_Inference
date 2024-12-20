# 二重にロバストな推定（DR）  

IPWと回帰分析の推定を組み合わせた手法。どっちかが適切に推定できていれば、ATEが推定できる。  
つまり、結果変数を推定するモデルか傾向スコアを推定するモデルのどちらかが適切に推定できれば良い。  

そのDRによるATEの推定量は、
$$ \frac{1}{N}\sum_{i=1}^N\bigg(\hat{\mu}_t(X_i)+\frac{T_i(Y_i-\hat{\mu}_t(X_i))}{\hat{\pi}(X_i)}\bigg) - \frac{1}{N}\sum_{i=1}^N\bigg(\hat{\mu}_c(X_i)+\frac{(1- T_i)(Y_i-\hat{\mu}_c(X_i))}{1-\hat{\pi}(X_i)}\bigg) $$  

結果変数モデルが正しいなら、例えばトリートメントグループについて、$Y_i \fallingdotseq \hat{\mu}_t(X_i)$なので、$$E[Y_t] = \frac{1}{N}\sum_{i=1}^N\bigg(\hat{\mu}_t(X_i)+\frac{T_i(Y_i-\hat{\mu}_t(X_i))}{\hat{\pi}(X_i)}\bigg) \tag{1}$$  
上の括弧内の第二項の分子は０になるので、傾向スコアとは関係なしに上式が成り立つ  

傾向スコアのモデルが正しいなら、$T_i \fallingdotseq \hat{\pi}(X_i)$なので、（１）式の括弧内の第二項は$Y_i-\hat{\mu}_t(X_i)$となるので、結果変数の推定値に関わらず上式が成り立つ。  

これらは、コントロールグループについてもいえるので、ATEの推定ができる。  
