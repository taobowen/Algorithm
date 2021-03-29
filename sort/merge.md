### ˼��
&emsp;&emsp;����һ�ַ����㷨����ԭʼ�����зֳɽ�С�����飬ֱ��ÿ��С����ֻ��һ�Ȼ���ڽ�С����鲢Ϊ�ź���Ľϴ����飬ֱ�����õ�һ���ź����������顣
### �ϴ��룺
```
function mergeSort(arr) {
    if(arr.length === 1) {
        return arr;
    }
    const mid = Math.floor(arr.length / 2);
    const leftArr = arr.slice(0, mid);
    const rightArr = arr.slice(mid, arr.length);
    return merge(mergeSort(leftArr), mergeSort(rightArr));
}

function merge(leftArr, rightArr) {
    let answer = [];
    let leftIndex = 0;
    let rightIndex = 0;
    while(leftIndex < leftArr.length && rightIndex < rightArr.length) {
        if(leftArr[leftIndex] > rightArr[rightIndex]) {
            answer.push(rightArr[rightIndex]);
            rightIndex++;
        }else {
            answer.push(leftArr[leftIndex]);
            leftIndex++;
        }
    }
    while(leftIndex < leftArr.length) {
        answer.push(leftArr[leftIndex]);
        leftIndex++;
    }
    while(rightIndex < rightArr.length) {
        answer.push(rightArr[rightIndex]);
        rightIndex++;
    }
    return answer;
}
```