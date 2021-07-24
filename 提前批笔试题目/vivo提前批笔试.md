# Vivo   

1. vivo团队在年底计划组织一次抽奖活动，助理小v要从团队中选出工号为数字7或者是7的幸运倍数的员工。

   ```C++
   #include <iostream>
   #include <string>
   #include <vector>
   using namespace std;
   
   int main()
   {
   	string str;
   	//cin >> str;
   	int count = 0;
   	while (cin >> str)
   	{
   		// 判断是否含有'7'
   		int n = str.length();
   		int intS = atoi(str.c_str());
   		if (intS % 7 == 0)
   			count++;
   		else
   			for (int i = 0; i < n; i++)
   			{
   				if (str[i] == '7')
   				{
   					count++;
   					break;
   				}
   			}
   	}
   	cout << count;
   	return 0;
   }
   ```

2. 有一艘货轮的最大载重量为C，现在有N个集装箱，编号为0,1,2,...,n-1，每个集装箱的重量为W，对应的货品价值为V，求这艘货轮选择装载哪些集装箱，才能在不超过最大载重的前提下保证装载的货品总价值最大。**（0-1背包问题）**
   输入描述：
   5  // C
   1,2,3,4,5  // W
   10,11,12,10,14  // V
   输出描述：
   23  // 货运总价值

   ```C++
   int main()
   {
   	int C;		// 最大载重量
   	cin >> C;
   	vector<int> dp(C + 1);
   	string W;
   	string V;
   	cin >> W;
   	cin >> V;
   	vector<int> w;
   	vector<int> v;
   	
   	auto getInt = [](vector<int>& num, string& s)
   	{
   		int temp = 0;
   		for (int i = 0; i < s.size(); ++i)
   		{
   			if (s[i] >= '0' && s[i] <= '9')
   			{
   				temp = temp * 10 + (s[i] - '0');
   			}
   			else
   			{
   				num.push_back(temp);
   				temp = 0;
   			}
   		}
   		num.push_back(temp);
   	};
   
   	getInt(w, W);
   	getInt(v, V);
   	for (int i = 0; i < w.size(); ++i)
   	{
   		for (int j = C; j >= w[i]; j--)
   		{
   			dp[j] = max(dp[j], dp[j-w[i]]+v[i]);
   		}
   	}
   	cout << dp[C];
   	return 0;
   }
   ```

3. ![image-20210618004430238](image/image-20210618004430238.png)

   * 和华为7.7号笔试第二题一模一样，DFS能做