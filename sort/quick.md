## ˼��
&emsp;&emsp;���������㷨��˼�������ڶ��ַ���ÿ�ζ�����������ѡ��һ������������������һ��λ�õ���������һ��ѡ���м�����ֻ�������ߵ����֣���ÿһ�ֽ����󣬱ȸû���С������λ�ڸû�������ߣ��ȸû����������λ�ڸû������ұߡ�Ȼ���ٷֱ�Ի�����ߺ��ұߵ����������ͬ�Ĳ�����ֱ��������ֻ��һ��Ԫ��ʱ�����ظ����顣
## �ϴ��룺
### ȡ����Ԫ����Ϊ������
```
function quickSort(arr, i, j) {
    if(i > j)
        return;
    let pivotIndex = i;
    let leftIndex = i;
    let rightIndex = j;
    while(leftIndex < rightIndex) {
        while(arr[rightIndex] >= arr[pivotIndex] && leftIndex < rightIndex) {
            rightIndex--;
        }
        while(arr[leftIndex] <= arr[pivotIndex] && leftIndex < rightIndex) {
            leftIndex++;
        }
        [arr[leftIndex], arr[rightIndex]] = [arr[rightIndex], arr[leftIndex]];
    }
    [arr[leftIndex], arr[pivotIndex]] = [arr[pivotIndex], arr[leftIndex]];
    quickSort(arr, i, leftIndex - 1);
    quickSort(arr, leftIndex + 1, j);
    return arr;
}
```
