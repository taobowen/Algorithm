����һ����������������Ƿ��Ǿ���ԳƵġ�

���磬������ [1,2,2,3,4,4,3] �ǶԳƵġ�

```
     1
   /   \
  2    2
 / \   / \
3  4 4  3
```
����������� [1,2,2,null,3,null,3] ���Ǿ���ԳƵ�:

```
    1
   / \
  2   2
   \   \
   3    3
```

�����õ���һ�����뵽����ͨ���������������Ȼ�������Ĵ�������д�����ύ������һЩ������ͨ�����ַ�ʽ��鲻�˵ģ�����
   ```
  5
   /   \
  4    1
    \    \
     1    4
    /     /
  2    2
```
Ȼ��������ͨ���������������Ȼ��ÿ������һ��ͼ���Ƿ��ǻ��Ĵ��ķ�ʽ���������⣬�������£�
```
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {boolean}
 */
var isSymmetric = function(root) {
    if(!root){
        return true;
    }
    var node=[];
    var answer=[];
    var indexOfnode=0;
    node.push(root);
    while(node.length!=0){
        answer[indexOfnode]=[];
        let next=[];
        for(i in node){
            if(!node[i]){
                answer[indexOfnode].push("n");
                continue;
            }
            answer[indexOfnode].push(node[i].val);
            next.push(node[i].left);
            next.push(node[i].right);
        }
        node=next.concat();
        let arr=answer[indexOfnode].concat();
        let str1=arr.join("");
        let str2=arr.reverse().join("");
        if(str1!=str2){
            return false;
        } 
        indexOfnode++;
    }
    return true;
};
```