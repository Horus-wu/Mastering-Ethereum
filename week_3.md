# 第四章 密码学

## 简介
以太坊的基础技术之一是密码学(cryptography)，它是数学的一个分支，广泛用于计算机安全。
以太坊有两种不同类型的账户，可以拥有和控制ether：
* 外部账户（EOA）
* 合同账户（contract）

## 公钥加密技术和密码学
公钥密码技术是现代信息安全的核心概念。首先由Martin Hellman，Whitfield Diffie和Ralph Merkle在20世纪70年代公开发明。

公钥密码系统使用唯一的密钥来保护信息。这些独特的密钥基于具有独特属性的数学函数：它们很容易在一个方向上计算，但很难在相反方向上计算。基于这些数学函数，密码学能够创建数字密钥和不可伪造的数字签名，这些签名由数学定律保证。
Tips:
* 密码  https://en.wikipedia.org/wiki/Cryptography
* Trapdoor函数: https://en.wikipedia.org/wiki/Trapdoor_function
* 素因子分解： https://en.wikipedia.org/wiki/Integer_factorization 
* 离散对数： https://en.wikipedia.org/wiki/Discrete_logarithm
* 椭圆曲线密码学： https://en.wikipedia.org/wiki/Elliptic_curve_cryptography

在以太坊，我们使用公钥加密技术来创建一个密钥对，以控制对ether的访问，并允许我们对合同进行身份验证。密钥对由私钥和唯一公钥组成，并且被认为是“一对儿”，因为公钥是从私钥中派生出来的。公钥用于接收资金，私钥用于创建数字签名来签署交易以支付资金。数字签名也可用于验证合同的所有者或用户
### 私钥
私钥只是一个随机选取的数字,创建以太坊私钥基本上与“选择1到2256之间的数字”相同.

### 公钥
以太坊公钥是一个椭圆曲线上的一个点，意思是它是一组满足椭圆曲线方程的X和Y坐标。
以太坊公钥是两个坐标数字，并联在一起。这些数字是通过一次单向的计算从私钥生成的。

*椭圆曲线密码学解释*
![avatar](https://github.com/inoutcode/ethereum_book/blob/master/images/simple_elliptic_curve.png)

以太坊使用与比特币完全相同的椭圆曲线，称为secp256k1

## 加密哈希函数
哈希函数是可用于将任意大小的数据映射到固定大小的数据的函数。哈希函数的输入称为pre-image或message。输出被称为哈希hash。
哈希函数的一个特殊子类别是加密哈希函数，它具有对密码学有用的特定属性。加密哈希函数是一种单向哈希函数，它将任意大小的数据映射到固定大小的位串，如果知道输出，计算上不可能重新创建输入。确定输入的唯一方法是对所有可能的输入进行蛮力搜索，检查匹配输出。

加密哈希函数有五个主要属性:
* 确定性: 任何输入消息总是产生相同的哈希摘要。
* 可验证性: 计算消息的哈希是有效的
* 不相关:  对消息的小改动（例如，一位改变）会大幅改变哈希输出，以致它不能与原始消息的哈希相关联。
* 不可逆性: 从哈希计算消息是不可行的，相当于通过可能的消息进行蛮力搜索。
* 碰撞保护: 计算两个不同的消息产生相同的哈希输出应该是不可行的
*以太坊的加密哈希函数 - Keccak-256*

## 以太坊地址
以太坊地址是唯一标识符(unique identifiers)，它们是使用单向哈希函数（Keccak-256）从公钥或合约派生的.
*以太坊地址是十六进制数字，从公钥的Keccak-256哈希的最后20个字节导出的标识符。*

## 问题？
- How to generate address from private key?
- How to validate address?
- How to verify a signed message by private key?
- What's cryptographic hash functions and it's main properties
- What's asymmetric cryptography and it's main properties
- What is discrete logarithm problem and Elliptic curve cryptography
- Address's checksum format