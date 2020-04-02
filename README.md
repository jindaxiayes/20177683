#include<iostream>
#include<stdlib.h>
#include <string>
#include <iostream>
#include <fstream>
using namespace std;
bool sign = false;/* 构造完成标志 */
int num[3][3];/* 创建数独矩阵 */

int main(int argc,char *argv[])
{
  	int k, i, j;
	char* in;  //输入文件 
	char* out;
	
	jie_num = atoi(argv[2]); 
	pan_num = atoi(argv[4]);
	in = argv[6];
	ifstream infile(in);
	out = argv[8];
	ofstream outfile(out);
	for (k = 0; k < pan_num; k++) {
		char temp[10][10] = { 0 };
		int flag = 0;
		for (i = 0; i < jie_num; i++)
		{
			for (j = 0; j < jie_num; j++)
			{
				infile >> temp[i][j];
				num[i][j] = temp[i][j] - '0';
			}
			flag++;
		}
		cout << endl;
		sign = false;
		DFS(0);
		for (i = 0; i < jie_num; i++)
		{
			for (j = 0; j < jie_num; j++)
			{
				num2[k][i][j] = num[i][j];
			}
		}

		for (i = 0; i < jie_num; i++)
		{
			for (j = 0; j < jie_num; j++)
			{
				cout << num2[k][i][j] << " ";
			}
			cout << endl;
		}
		cout << endl;
		ofstream outfile;
		outfile.open("output.txt", ios::app);   //以后继方式打开文件以便继续写
		for (int i = 0; i < jie_num; i++) {
			for (int j = 0; j < jie_num; j++) {
				outfile << num2[k][i][j] << " ";
			}
			outfile << endl;
		}
		outfile << "\n";
		outfile.close();
	}
	return 0;
}
