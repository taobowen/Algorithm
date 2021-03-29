&emsp;&emsp;�������ı�����һ���ȽϾ�������⣬ͨ���ݹ�ķ�ʽ���Ժ����׵�д���������ǵݹ����ֶ�ջ��������⣬���Թ�����ͨ��Ҫ����д��Ҳ�Ƿǵݹ���㷨���ǵݹ��ʵ���޷Ǿ���ͨ��ջ�����е���ʽ��
**ǰ�����**
����һ������������������ ǰ�� ������

 ʾ��:

```
����: [1,null,2,3]  
   1
    \
     2
    /
   3 

���: [1,2,3]
```
����ֻ��ע������ջʱ�ȷų�ջ�����Һ��ӽ���ٷ����ӽ�㡣
�ϴ��룺
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
 * @return {number[]}
 */
var preorderTraversal = function(root){
    let answer = [];
    let stack = [];
    while(root || stack.length !== 0) {
        while(root) {
            answer.push(root.val);
            stack.push(root);
            root = root.left;
        }
        root = stack.pop().right;
    }
    return answer;
}
```
**�������**
����һ���������������������� ������

ʾ��:

```
����: [1,null,2,3]
   1
    \
     2
    /
   3

���: [1,3,2]
```
�ϴ��룺
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
 * @return {number[]}
 */
var inorderTraversal = function(root) {
    const stack = [];
    const answer = [];
    while(root || stack.length != 0){
        while(root) {
            stack.push(root);
            root = root.left;
        }
        root = stack.pop();
        answer.push(root.val);
        root = root.right;
    }
    return answer;
};
```
**�������**
����һ������������������ ���� ������

ʾ��:

```
����: [1,null,2,3]  
   1
    \
     2
    /
   3 

���: [3,2,1]
```
������������ַ����������һ������ȡһ��pre��¼�ϴγ�ջ�Ľ�㣬�����ǰ�ڵ���������Ϊ�ջ��ߵ�ǰ�ڵ�������������֮һΪpre�����ջ������pre�������Ⱥ�ѵ�ǰ�ڵ�����������ջ���ڶ����������ҿ������˵�һ��ȡ�ɵ����������ǰ�ǰ������ĸ����Ҹ�Ϊ������Ȼ��ѱ������ȡ�����ڶ��ַ����Ƚϼ򵥣�������ֻ������һ�ַ����Ĵ��롣
�ϴ��룺
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
 * @return {number[]}
 */
var postorderTraversal = function(root){
    let stack = [];
    let answer = [];
    let pre = null;
    stack.push(root);
    while(root && stack.length !== 0){
        root = stack[stack.length - 1];
        if(!root.left && !root.right || pre && (root.right === pre || root.left === pre)){
            pre = root;
            answer.push(stack.pop().val);
        }else{
            if(root.right){
                stack.push(root.right);
            }
            if(root.left){
                stack.push(root.left);
            }
        }
    }
    return answer;
}
```