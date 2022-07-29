姓名：刘金星

学号：202000460060

git账户：frozen0234

Merkle Tree的特点

Merkle Tree是一种树，大多数是二叉树，也可以多叉树，无论是几叉树，它都具有树结构的所有特点；

Merkle Tree的叶子节点的value是数据集合的单元数据或者单元数据HASH。

非叶子节点的value是根据它下面所有的叶子节点值，然后按照Hash算法计算而得出的。

Merkle tree的树根并不表示树的深度，这可能会导致second-preimage attack，即攻击者创建一个具有相同Merkle树根的虚假文档。

一个简单的解决方法在Certificate Transparency中定义：
当计算叶节点的hash时，在hash数据前加0x00。当计算内部节点是，在前面加0x01。
另外一些实现限制hash tree的根，通过在hash值前面加深度前缀。
因此，前缀每一步会减少，只有当到达叶子时前缀依然为正，提取的hash链才被定义为有效。

merkletree* initial(merkletree* tree, char** s, int n)生成merkletree，倘若该层节点不足以两两分完，则将最后一个节点记录下来，并以它为头节点对应的树上的所有节点高度均加一作为下一层节点进行，以符合RFC6962要求。

void delete_tree(merkletree* tree)删除merkletree；

char** divide_string(char* str, int* number)merkletree支持字符串的存储，且以标点符号为分割；

void delete_string(char** s, int n)删除字符串；

运行结果如下：

![image](https://user-images.githubusercontent.com/106589212/181280220-71749187-655b-4597-9862-cdbbe53b1a5f.png)
