# Mini-Project-

#include<stdio.h>
#include<stdlib.h>

void Union(int a[30],int b[30],int c[60],int s1,int s2);
void Intersection(int a[30],int b[30],int c[60],int s1,int s2);
void Difference(int a[30],int b[30],int c[60],int s1,int s2);
void diff1(int a[30],int b[30],int c[60],int s1,int s2);
int compare(int t1,int c[60],int k);

void main()
{
	int a[30],b[30],c[60],s1,s2,m,i,ch;

	printf("\nEnter how many students in class Second year Computer Engineering:= ");
	scanf("%d",&m);
	printf("\nEnter size of set A students (play cricket):=");
	scanf("%d",&s1);
	printf("\nEnter roll numbers of set A %d students (play cricket):= ",s1);
	for(i=0;i<s1;i++)
		scanf("%d",&a[i]);

	printf("\nEnter size of set B students (play badminton):=");
	scanf("%d",&s2);
	printf("\nEnter roll numbers of set B %d students (play badminton):= ",s2);
	for(i=0;i<s2;i++)
		scanf("%d",&b[i]);

	while(1)
	{
		printf("\n\n----------Program Menu.----------\n1. Set of students who play either cricket or badminton or both (Union)\n2. Set of students who play both cricket and badminton (Intersection)\n3. Set of students who play only cricket (Difference)\n4. Set of students who play only badminton (Difference) \n5. Number of students who play neither cricket nor badminton \n6. Exit\nEnter ur choice :");
		scanf("%d",&ch);
		
		switch(ch)
		{
			case 1:
				Union(a,b,c,s1,s2);
				 break;

			case 2:
				Intersection(a,b,c,s1,s2);
				break;

			case 3:
				Difference(a,b,c,s1,s2);
				break;
			case 4:
				diff1(a,b,c,s1,s2);
				break;
        
			case 5:
                             printf("\nNumber of students who play neither cricket nor badminton= %d ",(m-(s1+s2)));
			     break;
			case 6:	
				exit(0);
		}
	}
}
int compare(int t1,int c[],int k)
{
	int i;
	for(i=0;i<k;i++)
	{
		if(t1==c[i])
			return 1;
	}
	return 0;
}
void Union(int a[],int b[],int c[],int s1,int s2)
{
	int i,j,k;
	for(i=0,k=0;i<s1;i++,k++)
		c[k]=a[i];
	for(j=0;j<s2;j++)
	{
		if((compare(b[j],c,k))==0)
		{
			c[k]=b[j];
			k++;
		}
	}
	printf("\nSet of students who play either cricket or badminton or both (Union):=\n");
	for(i=0;i<k;i++)
		printf("\t%d",c[i]);
}
void Intersection(int a[],int b[],int c[],int s1,int s2)
{
	int i,j,k=0;
	for(i=0;i<s1;i++)
	{
		for(j=0;j<s2;j++)
		{
			if(a[i]==b[j])
			{
				c[k]=a[i];
				k++;
			}
		}
	}
	printf("\nSet of students who play both cricket and badminton (Intersection):\n");
	for(i=0;i<k;i++)
		printf("\t%d",c[i]);
}
void Difference(int a[],int b[],int c[],int s1,int s2)
{
	int i,k=0;
	for(i=0;i<s1;i++)
	{
		if((compare(a[i],b,s2))==0)
		{
			c[k]=a[i];
			k++;
		}
	}
	printf("\nSet of students who play only cricket (Difference: (A-B)= \n");
	for(i=0;i<k;i++)
		printf("\t%d",c[i]);
}

void diff1(int a[],int b[],int c[],int s1,int s2)
{
	int i,k=0;
	for(i=0;i<s1;i++)
	{
		if((compare(b[i],a,s2))==0)
		{
			c[k]=b[i];
			k++;
		}
	}
	printf("\nSet of students who play only badminton (Difference: (B-A)= \n");
	for(i=0;i<k;i++)
		printf("\t%d",c[i]);
}
