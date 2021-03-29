����һ��������, �ҵ�����������ָ���ڵ������������ȡ�

�ٶȰٿ�������������ȵĶ���Ϊ���������и��� T ��������� p��q������������ȱ�ʾΪһ����� x������ x �� p��q �������� x ����Ⱦ����ܴ�һ���ڵ�Ҳ���������Լ������ȣ�����

���磬�������¶�����:  root = [3,5,1,6,2,0,8,null,null,7,4]
![image](https://user-images.githubusercontent.com/46807600/58612589-b35f4e00-82e5-11e9-80ba-0a8dc011d2cb.png)
**ʾ�� 1:**
```
����: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
���: 3
����: �ڵ� 5 �ͽڵ� 1 ��������������ǽڵ� 3��
```
**ʾ�� 2:**
```
����: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
���: 5
����: �ڵ� 5 �ͽڵ� 4 ��������������ǽڵ� 5����Ϊ���ݶ�������������Ƚڵ����Ϊ�ڵ㱾��
```
 

**˵��:**

���нڵ��ֵ����Ψһ�ġ�
p��q Ϊ��ͬ�ڵ��Ҿ������ڸ����Ķ������С�

**���**

&emsp;&emsp;������ı���д�ıȽ϶࣬������ͨ��ĳ�ֱ�������ĽӴ������˰���û��˼·�����ﻹ���г��ݹ顢�ǵݹ����ַ�����
- �ݹ飺�ݹ鵱Ȼ�Ǽ��������������������һ���������������ԭ���ڵ�Ϊ�ջ���Ϊp��q���ڵ�֮һ����һ������ͨ����������������о��ҵ�p��q�����ص�ǰ������Ӧ�ĸ��ڵ㣬���������н�һ���ҵ�p��q�������ҵ�Ŀ��ڵ�ĺ��ӽڵ㣬����δ�ҵ�������null��
**�ϴ��룺**
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
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {TreeNode}
 */
var lowestCommonAncestor = function(root, p, q) {
    if(root==p||root==q||!root){
        return root;
    }
    var left=lowestCommonAncestor(root.left,p,q);
    var right=lowestCommonAncestor(root.right,p,q);
    if(!left&&!right){
        return null;
    }
    else if(left&&!right){
        return left;
    }
    else if(right&&!left){
        return right;
    }else if(right&&left){
        return root;    
    }
};
```
- �ǵݹ飺�ǵݹ黹�ǽ���ջ���ֱ𱣴������Ӹ��ڵ㵽p��q��·����Ȼ��Ƚ�·���еĹ����ڵ㣬���ؼ��ɡ�
**�ϴ��룺**
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
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {TreeNode}
 */
var lowestCommonAncestor = function(root, p, q) {
    if(!root||root==p||root==q){
        return root;
    }
    var roadOfq=[];
    var roadOfp=[];
    roadOfq.push(root);
    roadOfp.push(root);
    while(roadOfp.length!=0){
        let lastnode=roadOfp[roadOfp.length-1];
        if(lastnode.flag_p==1){
            roadOfp.pop();
            continue;
        }else if((!lastnode.left||lastnode.left.flag_p==1)&&(!lastnode.right||lastnode.right.flag_p==1)){
            lastnode.flag_p=1;
        }
        if(lastnode==p){
            break;
        }else if(lastnode.right&&lastnode.right.flag_p==undefined){
            roadOfp.push(lastnode.right);
        }else if(lastnode.left&&lastnode.left.flag_p==undefined){
            roadOfp.push(lastnode.left);
        }
    }
    while(roadOfq.length!=0){
        let lastnode=roadOfq[roadOfq.length-1];
        if(lastnode.flag_q==1){
            roadOfq.pop();
            continue;
        }else if((!lastnode.left||lastnode.left.flag_q==1)&&(!lastnode.right||lastnode.right.flag_q==1)){
            lastnode.flag_q=1;
        }
        if(lastnode==q){
            break;
        }else if(lastnode.right&&lastnode.right.flag_q==undefined){
            roadOfq.push(lastnode.right);
        }else if(lastnode.left&&lastnode.left.flag_q==undefined){
            roadOfq.push(lastnode.left)
        }
    }
    for(let i=roadOfp.length-1;i>=0;i--){
        if(roadOfq.indexOf(roadOfp[i])!=-1){
            return roadOfp[i];
        }
    }
};
```