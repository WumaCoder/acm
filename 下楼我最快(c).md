# acm-
ACM例题题库
#include <stdio.h>

int abs(int num){
	if (num<0)
		num*=-1;
	return num;
}

int main(){
	int n,m;
	int t1,t2,t3,t4;
	int d,d_dt,d_bt;
	int num1,num2;
	while(scanf("%d%d%d%d%d%d", &n, &m, &t1, &t2, &t3, &t4)!=EOF){
		d = n-m; // 电梯到我家的位置
		d_dt = abs(d) * t1 + t2+ t3;//电梯到家的位置所要时间（包括开关门）
		d_bt = abs(d) * t4 + t2+ t3;//我走到电梯所需要的时间（同上）

		num2 = t4*(n-1); //步行到一楼的时间

        if (d_bt<d_dt){
            num1 = d_bt + t2 + (m-1)*t1;
        }else{
            num1 = d_dt + t2 + (n-1)*t1;
        }

		num1 = (num1 < num2) ? num1 : num2;//当坐电梯时间大于步行时间则使用步行时间

		//printf("%d\n",abs(n-m) * t1 + t2*2 + t3 + (n-1)*t4);
		printf("%d\n", num1);

	}

}


/*
思路：
n：家的位置， m：电梯当前位置
t1：空电梯每过一层楼的所用时间		t2:电梯开门时间		t3:电梯关门时间		t4:步行所下每层楼的时间

	1__ 2__ 3__ 4__ 5_-_ 6__ 7__ 8__ 9__ 10_-_
 
n = 5	m = 10
t1= 1	t2= 5	t3= 5	t4= 4
 
测试 数据：
5  10
1  5 5 4
结果 ：16
*/
