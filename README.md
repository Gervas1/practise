# practise
算法练习
#include<iostream>
using namespace std;

const int N = 1e6 + 10;
int q[N];

/*快速排序*/
void quick_sort( int q[] ,int l ,int r ){
	if( l >= r) return ;
	int x = q[l] , i = l - 1, j = r + 1;//此处选取的是左端点为参考值，同样可以选择右端点（r），也可以选取随机值
	while( i < j ){
		do i ++ ; while( q[i] < x );//找出左边大于标准的元素
		do j -- ; while( q[j] > x );//找出右边小于标准的元素
		if( i < j ) swap( q[i] , q[j] );//交换左边大于该值和右边小于该值的数组元素
	} 
	quick_sort( q , l , j );//对左边进行递归
	quick_sort( q , j + 1 , r );//对右边进行递归
}

int main(){
	int n;
	cin >> n;
	for(int i = 0 ; i < n ;i ++ ) cin>>q[i];
	quick_sort( q , 0 , n - 1 );//0和n - 1是数组的左端点和右端点的下标
	for(int i = 0 ; i < n ;i ++ ) cout << q[i] << " ";
	return 0;
}
