# SM4-AESNI
基本思想是利用SM4与AES中S盒结构的相似性，借助intel的AESNI指令完成S盒操作      
AES的S盒结构形如*S<sub>a</sub> (x)=A<sub>a</sub> ·I<sub>a</sub> (x) + C<sub>a</sub>*    
SM4的S盒结构形如*S<sub>s</sub> (x)=A<sub>s</sub> ·I<sub>s</sub> (A<sub>s</sub>x+C<sub>s</sub>) + C<sub>s</sub>*   
AES使用的不可约多项式为x<sup>8</sup> +x<sup>4</sup> +x<sup>3</sup> +x<sup>1</sup> +1    
SM4使用的不可约多项式为x<sup>8</sup> +x<sup>7</sup> +x<sup>6</sup> +x<sup>5</sup> x<sup>4</sup> +x<sup>2</sup> +1    
借助于有限域同构，将SM4对应的有限域元素映射到AES对应的有限域元素中，再借助指令求逆，最后再逆映射      
实现时要特别注意8bit数与矩阵的对应关系，这在SM4与AES中的结果有所不同  
