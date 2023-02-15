# leak-repair
# c
첫번째 줄에 물이 새는 곳 N과 테이프의 길이 L이 주어지고 두번째 줄에는 물이 새는 곳의 위치가 있다. 물을 막을때 1만큼 간격이 필요하다면 필요한 테이프의 개수를 출력하는 프로그램을 작성해보자!

#include <stdio.h>
#include <stdlib.h>

int i,j,cnt=0;
int leakage[100];


int compare(int n,int l){
	int start=leakage[0];
	for(i=0;i<n;i++){
		if(leakage[i]-start>=l){ //해당지점까지 테이프를 부족하면? 
			cnt++; //테이프갯수 증가  
			start=leakage[i]; /*테이프부족지점부터를 시작위치로*/  }}
	//for문에서 마지막 테이프는 세지 않아서 +1한다
	return cnt+1;}


void main(){
	int n,l; //n: 물세는 곳  l: 테이프의 길이  
	scanf("%d %d",&n,&l);
	for(i=0;i<n;i++){
		scanf("%d",&leakage[i]);}
	int tmp=0;
	for(i=0;i<n;i++){
		for(j=0;j<(n-1)-i;j++){ //오름차순으로 정렬시킨다  
			if(leakage[j]>leakage[j+1]){
				tmp=leakage[j];
				leakage[j]=leakage[j+1];
				leakage[j+1]=tmp;}}}
	int answer=compare(n,l);
	printf("필요한 테이프의 개수는: %d\n",answer);}
